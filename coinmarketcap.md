# Coinmarketcap



Coinmarketcap là một loại hình ảnh xác thực phổ biến trông giống như thế này

<figure><img src=".gitbook/assets/313081093_1997448693779508_5391987535300753600_n (1).png" alt=""><figcaption></figcaption></figure>

## 1.Tạo yêu cầu

### Request

**POST :** `https://omocaptcha.com/api/createJob`

| Name               | Type | Required | Description                                                                                                 |
| ------------------ | ---- | -------- | ----------------------------------------------------------------------------------------------------------- |
| api\_token         | text | yes      | Khóa tài khoản khách hàng                                                                                   |
| data.type\_job\_id | text | yes      | Id dịch vụ captcha cần giải                                                                                 |
| data.input         | text | yes      | Văn bản để nhận diện đối tượng![](.gitbook/assets/313081093\_1997448693779508\_5391987535300753600\_n.png)  |
| data.image\_base64 | text | yes      | Hình ảnh được mã hóa base64![](.gitbook/assets/19c9c2b0c266469fbba054aa5ea4bbe7.jpg)                        |

```json
POST /createTask HTTP/1.1
Host: omocaptcha.com
Content-Type: application/json

{
	"api_token": "YOUR_API_KEY",
	"data": {
		"type_job_id": "14",
		"input": "panda",
		"image_base64": "iVBORw0KGgoAAAANSUhEUgAAAcwAAAHMC......"
	}
}
```

<mark style="color:red;">Lưu ý :</mark> Văn bản để nhận diện đối tượng chỉ hỗ trợ ngôn ngữ tiếng anh và tiếng việt

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
		    "index|index|index"
	 }
}
```

* Máy chủ sẽ trả về <mark style="color:blue;">`error = false`</mark> và <mark style="color:blue;">`status = success`</mark>
* Đọc kết quả trong <mark style="color:blue;">`result`</mark>
* <mark style="color:blue;">`index`</mark> là số thứ tự để click ví du số 1 là ảnh số 1
{% endtab %}
{% endtabs %}
