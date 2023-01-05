# Nimo.tv

Captcha Nimo.tv là một loại captcha trông giống như sau:

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption><p>Captcha Nimo.tv</p></figcaption></figure>

Đầu tiên mở bảng điều khiển dành cho nhà phát triển trong trình duyệt của bạn và tìm phần tử có tên <mark style="color:blue;">`bg-placeholder`</mark> và lấy giá trị ở thuộc tính <mark style="color:red;">`src`</mark>

```html
<img src="data:image/jpg;base64,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" class="bg-placeholder">
```

Sau khi lấy giá trị ở thuộc tính <mark style="color:red;">`src`</mark> xong nó có thể trông giống như sau : <mark style="color:blue;">`data:image/jpg;base64,/9j/4AAQSkZJRgABAgAAAQABAAD/2wBDAAgGBgcGBQgHBwcJCQgKDBQNDAsLDBkSEw8UHRofHh0aHBwgJC4nICIsIxwcKDcpLDAxNDQ0Hyc5PTgyPC4zNDL/2wBDAQkJCQwLDBgNDRgyIRwhMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjI`</mark>

## 1.Tạo yêu cầu

### Request

**POST :** `https://omocaptcha.com/api/createJob`

| Name               | Type  | Required | Description                                                                |
| ------------------ | ----- | -------- | -------------------------------------------------------------------------- |
| api\_token         | text  | yes      | Khóa tài khoản khách hàng                                                  |
| data.type\_job\_id | text  | yes      | Id dịch vụ captcha cần giải                                                |
| data.image\_base64 | text  | yes      | Giá trị ở thuộc tính <mark style="color:red;">`src`</mark>                 |
| data.width\_view   | numbe | yes      | Kích thước chiều rộng hiện thị của ảnh![](<.gitbook/assets/image (2).png>) |

```json
POST /createTask HTTP/1.1
Host: omocaptcha.com
Content-Type: application/json

{
	"api_token": "YOUR_API_KEY",
	"data": {
	"type_job_id": "44",
        "image_base64": "data:image/jpg;base64,/9j/4AAQSkZJRgABAgAAAQABAAD......",
	"width_view": 320
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
	"result": {
		"123"
	}
}
```

* Máy chủ sẽ trả về <mark style="color:blue;">`error = false`</mark> và <mark style="color:blue;">`status = success`</mark>
* Đọc kết quả trong <mark style="color:blue;">`result`</mark>
* Trong bảng điều khiển dành cho nhà phát triển, tìm đến nút có tên <mark style="color:blue;">`drag-button`</mark> và kéo nút từ trái qua phải bằng giá trị đã nhận được từ <mark style="color:blue;">`result`</mark>
{% endtab %}

{% tab title="Đang xử lý" %}
```json
	"status": "running",
	"result": null
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