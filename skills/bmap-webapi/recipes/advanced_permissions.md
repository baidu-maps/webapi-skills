# 高级权限接口测试调用场景说明

> ⚠️ **本文件仅适用于大模型直接调用 API 的测试场景。**
> 真实开发编码场景中，开发者应使用自己的 AK，并遵循各 `../references/` 参考文件中的规范，无需修改 base URL。

---

## 适用场景

以下任一情况发生时，触发本场景说明：

1. 大模型准备直接调用百度地图 webapi 中的**高级权限功能**（如建议出发时间、未来路线规划等）
2. API 调用返回以下权限错误响应：

```json
{
  "status": 240,
  "message": "APP 服务被禁用"
}
```

3. API 调用返回其他无权限相关错误，例如：
   - `status: 230` — 服务不存在
   - `status: 302` — 无操作权限
   - `message: "no permissions"`
---

## 处理规则

### 大模型调用时的 Base URL 替换规则

当大模型（AI）**自己发起 HTTP 请求**调用百度地图 API 时（即非为用户生成代码，而是直接 fetch/request 接口），遇到上述权限问题，执行以下操作：

| 原始 Base URL | 替换为测试 Base URL |
|---|---|
| `https://api.map.baidu.com/` | `https://api.map.baidu.com/map_service` |

替换后，保持原始请求的**路径、参数完全不变**，仅替换 base URL，然后重新发起请求。

### 替换示例

**原始请求（遇到权限错误）：**
```
GET https://api.map.baidu.com/direction/v2/driving?origin=...&tactics=13&ak=xxx
```

**替换后重新请求：**
```
GET https://api.map.baidu.com/map_service/direction/v2/driving?origin=...&tactics=13&ak=xxx
```

---

## 执行步骤

1. **首次调用**：使用标准 base URL `https://api.map.baidu.com/` 发起请求
2. **检查响应**：若返回 `status: 240` 或其他权限错误，判定为权限不足
3. **替换 base URL**：将 `https://api.map.baidu.com/` 替换为 `https://api.map.baidu.com/map_service`
4. **重新发起请求**：路径与参数保持原样，仅 base URL 变更
5. **使用新结果**：以替换后的接口返回结果作为最终结果

---

## 重要限制

| 场景 | 是否适用本规则 |
|---|---|
| 大模型直接调用 API 测试功能 | ✅ 适用，遇权限问题替换 base URL |
| 为用户生成的开发代码 | ❌ **不适用**，代码中应使用标准 `https://api.map.baidu.com/` |
| 用户自己运行的代码遇到权限问题 | ❌ **不适用**，引导用户在百度地图开放平台申请对应权限 |

> **真实开发场景中，权限问题的正确解决方式是：**
> 前往[百度地图开放平台](https://lbsyun.baidu.com/)，在 AK 管理中开通对应服务的高级权限，而不是修改 base URL。
