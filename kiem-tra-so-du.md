# Kiểm tra số dư

Kiểm tra số dư bằng của tài khoản bằng khóa tài khoản khách hàng

## 1.Tạo yêu cầu

### Request

&#x20;**POST:** `https://omocaptcha.com/api/getBalance`

<table><thead><tr><th width="177">Name</th><th width="76">Type</th><th width="104">Required</th><th>Description</th></tr></thead><tbody><tr><td>api_token</td><td>text</td><td>yes</td><td>Khóa tài khoản khách hàng</td></tr></tbody></table>

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
    "balance": "0.00000",
    "message": "Get balance success."
}
```

* Máy chủ sẽ trả về :<mark style="color:blue;">`error = false`</mark>
* Xem số dư còn lại ở trong : <mark style="color:blue;">`balance`</mark>
* <mark style="color:blue;">`message`</mark> : Mô tả ngắn về trạng thái
{% endtab %}

{% tab title="Thất bại" %}
```json
{
    "error": true,
    "message": "Invalid api token."
}
```

* Máy chủ sẽ trả về <mark style="color:blue;">`error = true`</mark>
* <mark style="color:blue;">`message`</mark> : Mô tả ngắn về trạng thái
{% endtab %}
{% endtabs %}
