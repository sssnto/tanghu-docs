# API 文档

## 基础信息

- **Base URL**: `https://api.tanghu.com/v1` (待配置)
- **认证方式**: Bearer Token
- **数据格式**: JSON

## 接口列表

### 用户相关

#### 获取用户资料

```
GET /users/{userId}
```

**响应:**
```json
{
  "code": 0,
  "message": "success",
  "data": {
    "id": 1,
    "name": "张三",
    "birthday": "1990-01-01",
    "diabetesType": "TYPE_2",
    "diagnosisDate": "2020-06-15",
    "targetGlucoseMin": 3.9,
    "targetGlucoseMax": 7.8
  }
}
```

#### 更新用户资料

```
PUT /users/{userId}
```

**请求体:** `UserProfile` 对象

### 血糖记录

#### 获取血糖记录列表

```
GET /users/{userId}/blood-glucose?startDate=2026-03-01&endDate=2026-03-25
```

**响应:**
```json
{
  "code": 0,
  "message": "success",
  "data": [
    {
      "id": 1,
      "userId": 1,
      "value": 6.5,
      "measureTime": "2026-03-25T08:30:00",
      "measureType": "FASTING",
      "note": "空腹"
    }
  ]
}
```

#### 添加血糖记录

```
POST /users/{userId}/blood-glucose
```

**请求体:**
```json
{
  "value": 6.5,
  "measureTime": "2026-03-25T08:30:00",
  "measureType": "FASTING",
  "note": "空腹"
}
```

#### 删除血糖记录

```
DELETE /blood-glucose/{recordId}
```

## 错误码

| 错误码 | 说明 |
|--------|------|
| 0 | 成功 |
| 1001 | 参数错误 |
| 1002 | 未授权 |
| 1003 | 资源不存在 |
| 2001 | 血糖值超出合理范围 |
| 5000 | 服务器内部错误 |
