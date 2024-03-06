# reCAPTCHA-v3

reCAPTCHA-v3 là một loại hình ảnh xác thực rất phổ biến trông giống thế nay:

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

Đầu tiên, bạn cần tìm giá trị của tham số <mark style="color:red;">`data-sitekey`</mark> trong mã nguồn của trang web. Mở bảng điều khiển dành cho nhà phát triển trong trình duyệt của bạn và tìm phần tử có thuộc tính <mark style="color:red;">`data-sitekey`</mark>

```html
<div id="recaptcha-demo" class="g-recaptcha" data-sitekey="6Le-wvkSAAAAAPBMRTvw0Q4Muexq9bi0DJwx_mJ-" data-callback="onSuccess" data-action="action">
```

## 1.Tạo yêu cầu

### Request

**POST :** `https://omocaptcha.com/api/createJob`

<table><thead><tr><th width="184">Name</th><th width="76">Type</th><th width="104">Required</th><th>Description</th></tr></thead><tbody><tr><td>api_token</td><td>text</td><td>yes</td><td>Khóa tài khoản khách hàng</td></tr><tr><td>data.type_job_id</td><td>text</td><td>yes</td><td>ID loại captcha cần nhận diện</td></tr><tr><td>data.website_url</td><td>text</td><td>yes</td><td>Địa chỉ của một trang web đích. Có thể được đặt ở bất kỳ đâu trên trang web, ngay cả trong khu vực thành viên. Nhân viên của chúng tôi không điều hướng đến đó mà thay vào đó mô phỏng chuyến thăm</td></tr><tr><td>data.website_key</td><td>text</td><td>yes</td><td>Khoá trang web Recaptcha. Tìm hiểu cách tìm nó trong bài viết này.</td></tr><tr><td>data.score</td><td>text</td><td>yes</td><td><p>Giá trị điểm yêu cầu:</p><p><strong>0,3</strong> </p><p><strong>0,7</strong><br><strong>0,9</strong></p></td></tr><tr><td>data.action</td><td>text</td><td>yes</td><td>Giá trị tham số hành động. Giá trị được chủ sở hữu trang web đặt bên trong <code>data-action</code>thuộc tính của phần tử reCAPTCHA <code>div</code>hoặc được truyền bên trong đối tượng tùy chọn của <code>execute</code>lệnh gọi phương thức, như<code>grecaptcha.execute('websiteKey'{ action: 'myAction' })</code></td></tr></tbody></table>

```json
Host: omocaptcha.com
Content-Type: application/json

{
	"api_token": "YOUR_API_KEY",
	"data": {
		"type_job_id": "3",
		"website_url": "https://recaptcha-demo.appspot.com/recaptcha-v3-request-scores.php",
		"website_key": "6LdyC2cUAAAAACGuDKpXeDorzUDWXmdqeg-xy696",
		"score": "0,9",
		"action": "examples/v3scores"
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

* Máy chủ sẽ trả về <mark style="color:blue;">`error= false`</mark> và <mark style="color:blue;">`job_id`</mark> thành công
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

<table><thead><tr><th width="122">Name</th><th width="99">Type</th><th width="111"> Required</th><th width="412">Description</th></tr></thead><tbody><tr><td>api_token</td><td>text</td><td>yes</td><td>Khóa tài khoản khách hàng</td></tr><tr><td>job_id</td><td>number</td><td>yes</td><td>Id của job vừa tạo</td></tr></tbody></table>

```json
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
		"03AHJ_VuvYIBNBW5yyv0zRYJ75VkOKvhKj9_xGBJKnQim...."
	}
}
```

* Máy chủ sẽ trả về <mark style="color:blue;">`error = false`</mark> và <mark style="color:blue;">`status = success`</mark>
* Đọc kết quả trong <mark style="color:blue;">`result`</mark>
{% endtab %}

{% tab title="Đang xử lý" %}
```json
{
	"error": false,
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

* Máy chủ sẽ trả về <mark style="color:blue;">`error= false`</mark> và <mark style="color:blue;">`status = fail`</mark>
{% endtab %}
{% endtabs %}

