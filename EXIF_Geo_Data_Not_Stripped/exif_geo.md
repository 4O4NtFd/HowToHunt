<h4>Summary总览:</h4>

When a user uploads an image in example.com, the uploaded image’s EXIF Geolocation Data does not gets stripped. As a result, anyone can get sensitive information of example.com users like their Geolocation, their Device information like Device Name, Version, Software & Software version used etc.
当用户在 example.com 上传图像时，上传图像的 EXIF 地理位置数据不会被剥离。 因此，任何人都可以获得 example.com 用户的敏感信息，例如他们的地理位置，他们的设备信息，例如设备名称、版本、使用的软件和软件版本等。

<h4>Steps to reproduce重现步骤:</h4>

1. Got to GitHub`去GitHub` ( https://github.com/ianare/exif-samples/tree/master/jpg) <br>
2. There are lot of images having resolutions (i.e. 1280 * 720 ) , and also with different MB’s .`有很多图像具有分辨率（即 1280 * 720 ），也有不同 MB 的图像`<br>
3. Go to Upload option on the website `转到网站上的上传选项` <br>
4. Upload the image `上传图片`<br>
5. see the path of uploaded image ( Either by right click on image then copy image address OR right click, inspect the image, the URL will come in the inspect ,   edit it as html )`查看上传图片的路径（右键点击图片然后复制图片地址或右键点击查看图片，URL会出现在inspect中，将其编辑为html）`</br>
6. open it (http://exif.regex.info/exif.cgi)`打开(http://exif.regex.info/exif.cgi)`</br>
7. See weather is that still showing exif data , if it is then Report it.`看是否还显示exif数据，如果是就报告`

# Reports (Hackerone)

- [IDOR with Geolocation data not stripped from images`带有未从图像中剥离的地理定位数据的 IDOR(不安全的直接对象引用)`](https://hackerone.com/reports/906907)

# Author
* [@0xd3vil](https://twitter.com/0xd3vil)
* [@klaus](https://twitter.com/klaus_dev)
