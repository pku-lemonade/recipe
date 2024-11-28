# 服务器

## 管理人员

[吴飞扬](mailto:1308642003@qq.com)

## seele

位于昌平机房。配置与 Amazon EC2 `m6i.32xlarge`实例相同。

- Server: Inspur 5280 M6
- CPU: 2 x Intel 8375c
- Memory: 16 x 32 GB
- SSD: 2 x 2 TB
- HDD: 18 TB + 8 TB
- GPU: NVIDIA L4
- OS: Debian 12

## apples

位于昌平办公室。主要用作存储池和深度学习机器。

- CPU: AMD EPYC 7c13
- Memory: 8 x 32 GB
- SSD: 4 TB + 2 TB
- HDD: 8 x 8 TB (RAID 10, 32 TB available)
- GPU: 3 x NVIDIA RTX 4090
- OS: Debian 12

## 登录方式

### 校园网

使用如下 ssh 配置登录。

```ssh-config
Host seele
	Hostname *在分配账号时会告知IP地址*
	Port 23333
```

### VPN

首先使用[这个](https://gist.github.com/youweizhuo/aea674cac7d79dcdb02b42f3a0985536)脚本在本地 11080 端口启动 socks5 代理。

然后使用如下 ssh 配置登录。

```ssh-config
Host seele-vpn
  Hostname *在分配账号时会告知IP地址*
  Port 23333
  ProxyCommand nc -X 5 -x 127.0.0.1:11080 %h %p
```

## 在服务器上使用代理

### 在 `bash` 中使用代理

- 请执行以下命令加载环境变量：`source /etc/profile.d/clash.sh`
- 请执行以下命令开启系统代理：`proxy_on`
- 若要临时关闭系统代理，请执行：`proxy_off`

这样，除`git`外的所有命令都会使用代理。

### 在 `fish` 中使用代理

如果你将 `fish` 作为默认 shell，可以在 `~/.config/fish/config.fish` 中添加如下内容：

```fish
function proxy_on
  set -xg ALL_PROXY http://127.0.0.1:7890
  set -xg HTTP_PROXY http://127.0.0.1:7890
  set -xg HTTPS_PROXY http://127.0.0.1:7890
end

function proxy_off
  set -e ALL_PROXY
  set -e HTTP_PROXY
  set -e HTTPS_PROXY
end
```

- 请执行以下命令开启系统代理：`proxy_on`
- 若要临时关闭系统代理，请执行：`proxy_off`

这样，除`git`外的所有命令都会使用代理。

### 在 `git` 中使用代理

只需要执行一次：

```bash
git config --global https.proxy http://127.0.0.1:7890
```
