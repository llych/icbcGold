获取工商银行黄金价格, 升降(幅度0.5)发送通知

## 使用
```bash
git clone https://github.com/llych/icbcGold.git
cd icbcGold
go get -v .
go run icbc.go
```

```bash
$ go run icbc.go
2019-02-07T13:44:24+08:00 INF icbc.go:69 > 当前价格: 282.56
2019-02-07T13:44:24+08:00 INF icbc.go:85 > 当前价格: 282.56 [上升]
2019-02-07T13:44:26+08:00 INF icbc.go:104 > 发送成功
2019-02-07T13:45:24+08:00 INF icbc.go:69 > 当前价格: 282.57
2019-02-07T13:46:23+08:00 INF icbc.go:69 > 当前价格: 282.56
2019-02-07T13:47:23+08:00 INF icbc.go:69 > 当前价格: 282.56
```

### 通知地址
> http://api.xx.com/weixin , 自行斟酌修改
```
func wechat(msg string) {
	var (
		res *http.Response
		err error
	)
	if res, err = http.PostForm("http://api.xx.com/weixin", url.Values{"msg": {msg}}); err != nil {
		log.Error().Msg("发送失败")
	} else {
		log.Info().Msgf("发送成功")
	}
	res.Body.Close()
}
```
