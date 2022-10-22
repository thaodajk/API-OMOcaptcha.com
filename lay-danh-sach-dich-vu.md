# Lấy danh sách dịch vụ

## 1.Tạo yêu cầu

### Request

&#x20;**GET :**  `http://omocaptcha.com/api/getService?api_token=`<mark style="color:blue;">`YOUR_API_KEY`</mark>

**Ví dụ :** _`http://omocaptcha.com/api/getService?api_token=q2FBalYHO6JNIOoohREEipwJ`_

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
  * <mark style="color:blue;">`avg_success`</mark> <mark style="color:blue;"></mark><mark style="color:blue;"></mark> : <mark style="color:blue;"></mark> Tỉ lệ thành công
  * <mark style="color:blue;">`avg_time`</mark> <mark style="color:blue;"></mark><mark style="color:blue;"></mark> : <mark style="color:blue;"></mark> Thời gian giải
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
* <mark style="color:blue;">`message`</mark> <mark style="color:blue;"></mark><mark style="color:blue;"></mark> mô tả ngắn về trạng thái
{% endtab %}
{% endtabs %}
