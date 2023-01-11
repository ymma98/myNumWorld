# 解决 windows 中无法 git fetch 的问题

如果无法 ping 通 github.com，

1. 打开网站 https://www.ipaddress.com/ , 搜索 `github.com` 和 `github.global.ssl.fastly.net ` 的 ip。

2. 把上一步搜索到的两个 ip 添加到 C:\Windows\System32\drivers\etc hosts 文件，比如：

   ```bash
   140.82.113.4 github.com
   151.101.1.194 github.global.ssl.fastly.net 
   ```



如果可以 ping 通 github，但是报错:

```bash
Failed to connect to github.com port 443 after 21040 ms: Timed out
```

那么执行命令:

```bash
git config --global http.proxy 127.0.0.1:10809
```

解决问题!

