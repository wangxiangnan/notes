## url组成部分详解

#### 示例： https://www.aspxfans.com:8080/news/index.asp?boardID=5&ID=24618&page=1#name

#### 1. 协议部分
```
	该URL的协议部分为'http',这代表网页使用的是HTTP协议，在Internet中可以使用多种协议，如：HTTP、FTP，以//为
	分割符
```
#### 2. 域名部分
```
	该URL的域名为：www.aspxfans.com，一个URL中，也可以使用IP地址作为域名部分
```
#### 3. 端口部分
```
	跟在域名后面的是端口，域名和端口之间用:作为分隔符，如果省略端口，将使用默认端口（80）
```
#### 4. 服务器路径部分
```
	从域名后的第一/开始，到最后一个/结束，是服务器路径部分。服务器路径也不是必须的，本例中的路径是'/news/'
```
#### 5. 文件名部分
```
	从域名后的最后/开始，到第一？ || #为止，是文件部分，本例中的文件名是'index.asp',文件名也不是一个URL必须的部分
	如果省略该部分则使用默认的文件名
```
#### 6. 参数部分
```
	从url第一个问号开始，到最后或者#号为止，称为参数部分、查询部分、搜索部分，参数允许多个参数，以&隔开
```
#### 7. 锚部分
```
	从#开始到最后，都是锚部分，本例中的锚部分是'name',锚部分也不是一个URL中必须的部分
```