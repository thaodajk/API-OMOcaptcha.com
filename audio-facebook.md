# Audio Facebook

Captcha Audio Facebook là một loại captcha trông giống như sau:

<figure><img src=".gitbook/assets/image (3).png" alt=""><figcaption><p>Captcha Audio Facebook</p></figcaption></figure>

Đầu tiên mở bảng điều khiển dành cho nhà phát triển trong trình duyệt của bạn và tìm phần tử có tên <mark style="color:red;">`captcha_persist_data`</mark> và lấy giá trị ở thuộc tính <mark style="color:red;">`value`</mark>

```html
<input type="hidden" id="captcha_persist_data" name="captcha_persist_data" value="AZmuYDEKSJsTMPeub2_KqB6PtM76JRnWBqKJe1dgFFDpQOFEjvsWScCUVypMgkaHnkC8uHcA43Qt3hMTJ15GsU9GKu6KJ6tg97BiY7pbYKg2PMZoNffxR7Tdr_2CwFBjctShF5haeoorruBefMpiLRovzH8T0GY_gXPsvN0d2BVkbu5i-EWdzuo5OifIa_gTp0ZcTCZpBlClhgHUJt-kPLz00TvnbOJopsTrkgYeUeaLoFV-17FrPeZErKj0I4JVnsH68ph33KfK7MFbyOy5YorvyskyI3H14GludKuZlRkff2JCF8RxtxHgbuG7idD1QRWCEucIKeRHYBXbMWw6ueA3u_anGXSI9jVuWQPFD98J7t-yLlGMCWdd4A0ynkNyZrZzCz3aeUpf-ecsL8lpHhKNt4Oi4vcMHea3hQn9T8YC7BbJ4uiQPcZ5mEFacjy39gRb13Stay4qLS87QuVIkq0e">
```

Sau khi lấy giá trị ở thuộc tính <mark style="color:red;">`value`</mark> xong nó có thể trông giống như sau : <mark style="color:blue;">`AZmuYDEKSJsTMPeub2_KqB6PtM76JRnWBqKJe1dgFFDpQOFEjvsWScCUVypMgkaHnkC8uHcA43Qt3hMTJ15GsU9GKu6KJ6tg97BiY7pbYKg2PMZoNffxR7Tdr_2CwFBjctShF5haeoorruBefMpiLRovzH8T0GY_gXPsvN0d2BVkbu5i-EWdzuo5OifIa_gTp0ZcTCZpBlClhgHUJt-kPLz00TvnbOJopsTrkgYeUeaLoFV-17FrPeZErKj0I4JVnsH68ph33KfK7MFbyOy5YorvyskyI3H14GludKuZlRkff2JCF8RxtxHgbuG7idD1QRWCEucIKeRHYBXbMWw6ueA3u_anGXSI9jVuWQPFD98J7t-yLlGMCWdd4A0ynkNyZrZzCz3aeUpf-ecsL8lpHhKNt4Oi4vcMHea3hQn9T8YC7BbJ4uiQPcZ5mEFacjy39gRb13Stay4qLS87QuVIkq0e`</mark>

Tiếp tục đến phần tải file mp3 ta sẽ lấy giá trị thuộc tính  <mark style="color:red;">`value`</mark> thêm vào URL [`https://www.facebook.com/captcha/tfbaudio/?captcha_persist_data=`](https://www.facebook.com/captcha/tfbaudio/?captcha\_persist\_data=)

Sau khi thêm giá trị ở thuộc tính <mark style="color:red;">`value`</mark> vào URL nó có thể trông giống như sau : <mark style="color:blue;">`https://www.facebook.com/captcha/tfbaudio/?captcha_persist_data=AZmuYDEKSJsTMPeub2_KqB6PtM76JRnWBqKJe1dgFFDpQOFEjvsWScCUVypMgkaHnkC8uHcA43Qt3hMTJ15GsU9GKu6KJ6tg97BiY7pbYKg2PMZoNffxR7Tdr_2CwFBjctShF5haeoorruBefMpiLRovzH8T0GY_gXPsvN0d2BVkbu5i-EWdzuo5OifIa_gTp0ZcTCZpBlClhgHUJt-kPLz00TvnbOJopsTrkgYeUeaLoFV-17FrPeZErKj0I4JVnsH68ph33KfK7MFbyOy5YorvyskyI3H14GludKuZlRkff2JCF8RxtxHgbuG7idD1QRWCEucIKeRHYBXbMWw6ueA3u_anGXSI9jVuWQPFD98J7t-yLlGMCWdd4A0ynkNyZrZzCz3aeUpf-ecsL8lpHhKNt4Oi4vcMHea3hQn9T8YC7BbJ4uiQPcZ5mEFacjy39gRb13Stay4qLS87QuVIkq0e`</mark>

Sau khi tải file mp3 về thì bạn cần phải chuyển file mp3 đó thành chuỗi base64

## 1.Tạo yêu cầu

### Request

**POST :** `https://omocaptcha.com/api/createJob`

| Name               | Type | Required | Description                         |
| ------------------ | ---- | -------- | ----------------------------------- |
| api\_token         | text | yes      | Khóa tài khoản khách hàng           |
| data.type\_job\_id | text | yes      | Id dịch vụ captcha cần giải         |
| data.input         | text | yes      | Chuỗi base64 chuyển đổi từ file mp3 |

```json
POST /createTask HTTP/1.1
Host: omocaptcha.com
Content-Type: application/json

{
	"api_token": "YOUR_API_KEY",
	"data": {
		"type_job_id": "41",
		"input": "SUQzBAAAAAAAHFRTU0UAAAAIAAADR2983QHCQwPEBMW......."
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
		"ABCDEF"
	}
}
```

* Máy chủ sẽ trả về <mark style="color:blue;">`error = false`</mark> và <mark style="color:blue;">`status = success`</mark>
* Đọc kết quả trong <mark style="color:blue;">`result`</mark>
* Trong bảng điều khiển dành cho nhà phát triển, tìm <mark style="color:red;">`name="`</mark><mark style="color:blue;">`captcha_response`</mark><mark style="color:red;">`"`</mark> và đặt mã nhận được vào đó. Sau đó, nhấp vào nút <mark style="color:blue;">`Continue`</mark>
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
