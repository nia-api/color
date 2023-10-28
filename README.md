# color

`nia-api` 的插件

用于获取常用的颜色 以及 css 渐变语句

### 安装插件

从 Release 下载文件，然后解压到插件目录

### 配置文件

```bash
 # 定义颜色列表 参考下方的格式定义
 colors:
   pink: fa7298
```

### 接口

GET

`/color`

需传参

```javascript
{
	color: 颜色的简称，与配置文件中的相同 | null
	type: gradient | null
}
```

若未传 `color` 值系统返回目前可获取的颜色列表

```javascript
{
    "status": 200,
    "msg": "获取预设颜色数据成功!",
    "colorList": {
        "pink": "fa7298"
    }
}
```

若传入的 `color` 值没有被配置文件定义

```javascript
{
	"status": 404,
	"msg": "请求的颜色不存在"
}
```

若传入了 `type` 但是是错误的值

```javascript
{
	"status": 400,
	"msg": "非法的参数！"
}
```

正确传值，未传 `type` （ `color` 以 `pink` 为例 ）

```javascript
{
	"status": 200,
	"color": "#fa7298",
	"hexadecimal": "fa7298",
	"msg": "获取颜色成功！"
}
```

正确传值，已传 `type` （ `color` 以 `pink` 为例 ）

```javascript
{
	"status": 200,
	"css": "linear-gradient(150deg, hsl(343, 0.93%, 10.71%) 15%, hsl(343, 0.93%, 0.71%) 70%, hsl(343, 0.93%, -9.29%) 94%)",
	"msg": "获取渐变色语句成功！"
}
```
