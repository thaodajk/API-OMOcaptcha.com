# Lấy danh sách dịch vụ bằng API

## 1.Tạo yêu cầu

### Request

&#x20;**POST :**  `https://omocaptcha.com/api/getService`

<table><thead><tr><th width="177">Name</th><th width="76">Type</th><th width="104">Required</th><th>Description</th></tr></thead><tbody><tr><td><code>api_token</code></td><td>text</td><td>yes</td><td>Khóa tài khoản khách hàng</td></tr></tbody></table>

```json
GET/createTask HTTP/1.1
Host: omocaptcha.com
Content-Type: application/json

{
    "api_token": "YOUR_API_KEY"
}
```

### Phản hồi

{% tabs %}
{% tab title="Thành công" %}
```json
{
    "error": false,
    "service": [
        {
            "id": 1,
            "name": "reCaptcha v2",
            "description": "Google Inc",
            "price": "0.00055",
            "require_field": null,
            "order": 1,
            "image": "recaptcha.svg",
            "avg_success": "98%",
            "avg_time": "15s",
            "is_active": 1,
            "created_at": null,
            "updated_at": null
        }
    ],
    "message": "Get service success."
}
```

* Máy chủ sẽ trả về : <mark style="color:blue;">`error = false`</mark>
* <mark style="color:blue;">`service`</mark>
  * <mark style="color:blue;">`id`</mark> : Id dịch vụ
  * <mark style="color:blue;">`name`</mark> : Tên dịch vụ
  * <mark style="color:blue;">`description`</mark>&#x20;
  * <mark style="color:blue;">`price`</mark> : Giá dịch vụ
  * <mark style="color:blue;">`require_field`</mark>
  * <mark style="color:blue;">`order`</mark>
  * <mark style="color:blue;">`image`</mark>
  * <mark style="color:blue;">`avg_success`</mark> : Tỉ lệ thành công
  * <mark style="color:blue;">`avg_time`</mark> : Thời gian giải
  * <mark style="color:blue;">`is_active`</mark>
  * <mark style="color:blue;">`created_at`</mark>
  * <mark style="color:blue;">`updated_at`</mark>
* <mark style="color:blue;">`message`</mark> mô tả ngắn về trạng thái
{% endtab %}

{% tab title="Thất bại" %}
```json
{
    "error": true,
    "message": "Invalid api token."
}
```

* Máy chủ sẽ trả về <mark style="color:blue;">`error = true`</mark>
* <mark style="color:blue;">`message`</mark> mô tả ngắn về trạng thái
{% endtab %}
{% endtabs %}
