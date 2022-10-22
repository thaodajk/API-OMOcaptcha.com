# reCAPTCHA V2

reCAPTCHA V2 còn được gọi là Tôi không phải là  reCAPTCHA là một loại hình ảnh xác thực rất phổ biến trông giống như thế này

<figure><img src=".gitbook/assets/recaptchav2.gif" alt=""><figcaption><p>2.Ảnh captcha reCAPTCHA v2</p></figcaption></figure>

## 1.Tạo yêu cầu

### Request

**POST :** `https://omocaptcha.com/api/createJob`

| Name               | Type | Required | Description                                                                                                                                                                                        |
| ------------------ | ---- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| api\_token         | text | yes      | Khóa tài khoản khách hàng                                                                                                                                                                          |
| data.type\_job\_id | text | yes      | ID loại captcha cần nhận diện                                                                                                                                                                      |
| data.websiteURL    | text | yes      | Địa chỉ của một trang web đích. Có thể được đặt ở bất kỳ đâu trên trang web, ngay cả trong khu vực thành viên. Nhân viên của chúng tôi không điều hướng đến đó mà thay vào đó mô phỏng chuyến thăm |
| data.websiteKey    | text | yes      | Khoá trang web Recaptcha. Tìm hiểu cách tìm nó trong bài viết này.                                                                                                                                 |
| task.isInvisible   | bool | no       | Chỉ định xem Recaptcha có ẩn hay không. Điều này sẽ hiển thị một widget thích hợp cho công nhân của chúng tôi.                                                                                     |

```json
POST /createTask HTTP/1.1
Host: api.anycaptcha.com
Content-Type: application/json

{
	"api_token": "YOUR_API_KEY",
	"data": {
		"type_job_id": "ID",
		"websiteURL": "http://mywebsite.com/recaptcha/test.php",
		"websiteKey": "6Lc_aCMTAAAAABx7u2N0D1XnVbI_v6ZdbM6rYf16",
		"isInvisible": false
	}
}
```

### Phản hồi

{% tabs %}
{% tab title="Thành công" %}
```json
{
	"error": false,
	"job_id": 123456,
	"message": "Create job success."
}
```

* Máy chủ sẽ trả về <mark style="color:blue;">`error= false`</mark> và <mark style="color:blue;">`job_id`</mark> <mark style="color:blue;"></mark><mark style="color:blue;"></mark> thành công
{% endtab %}

{% tab title="Thất bại" %}
```json
{
	"error": true,
	"message": "MESSAGE_ERROR",
}
```

* Máy chủ sẽ trả về <mark style="color:blue;">`error = true`</mark> và <mark style="color:blue;">`message`</mark> mô tả ngắn về trạng thái
{% endtab %}
{% endtabs %}

## 2.Nhận kết quả yêu cầu

### Request

**POST :** `https://omocaptcha.com/api/getJobResult`

| Name       | Type   |  Required | Description               |
| ---------- | ------ | --------- | ------------------------- |
| api\_token | text   | yes       | Khóa tài khoản khách hàng |
| job\_id    | number | yes       | Id của job vừa tạo        |

```json
POST /getTaskResult HTTP/1.1
Host: omocaptcha.com
Content-Type: application/json

{
	"api_token": "YOUR_API_KEY",
	"job_id": 123456
}
```

### Phản hồi

{% tabs %}
{% tab title="Thành công" %}
```json
{
	"error": false,
	"status": "success",
	"result":{
		"gRecaptchaResponse": "3AHJ_VuvYIBNBW5yyv0zRYJ75VkOKvhKj9_xGBJKnQim...."
	}
}
```

* Máy chủ sẽ trả về <mark style="color:blue;">`error = false`</mark> và <mark style="color:blue;">`status = success`</mark>
* Đọc kết quả trong <mark style="color:blue;">`result`</mark>
{% endtab %}

{% tab title="Đang xử lý" %}
```json
{
	"errorId": 0,
	"status": "processing"
}
```

* <mark style="color:blue;">`error= false`</mark> và <mark style="color:blue;">`status = running`</mark> yêu cầu đang được xử lý, xin vui lòng chờ 2 giây rồi yêu cầu lại
{% endtab %}

{% tab title="Thất bại" %}
```json
{
	"error": false,
	"status": "fail",
	"result": null
}
```

* Máy chủ sẽ trả về <mark style="color:blue;"></mark> <mark style="color:blue;"></mark><mark style="color:blue;">`error= false`</mark> và <mark style="color:blue;">`status = fail`</mark>
{% endtab %}
{% endtabs %}

