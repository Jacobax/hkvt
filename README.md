# heroku-vless
## Deploy VLESS and Trojan server to heroku
## 请使用者保持低调，免费的资源已所剩无几
## ![捕获1](https://user-images.githubusercontent.com/72486732/132114143-0e5d6c0a-9867-458c-b2fd-e3c7191c062b.png) Fork本项目后将readme.md中的Dimitri2020007替换为自己的用户名后再进行部署，非常重要，切记！！！！
## 选择不向任何网站转传是为了更长久的相聚，愿你能发现墙外美好而又有趣的地方。
## 带有删除线的部分表示不适用或已经废弃
## 自2021.11.18起不再部署caddy，改为单一部署以减少项目大小，提高项目稳定性，不保证本项目有被封的可能。

## Fork this project, replace Dimitri2020007 in readme.md with your own user name before deploying, it is very important, remember!!!!
## The part with a strikethrough indicates that it is not applicable or has been obsoleted
## The reason for choosing not to repost to any website is to get together for a longer time. I hope you can find beautiful and interesting places outside the wall.
## Since 2021.11.18, caddy will no longer be deployed, but a single deployment will be used to reduce the size of the project and improve the stability of the project. There is no guarantee that this project may be blocked.
## This wall will fall. Beliefs become reality. (Ronald Reagan)

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://dashboard.heroku.com/new?template=https://github.com/Jacobax/hkvt.git)

# VLESS Client Setup

| Connection Variables | Values |
| -------------------- | ------ |
| `Address` | yourAppName.herokuapp.com </br> Cloudflare Reverse Proxy IP |
| `SNI` | Cloudflare Reverse Proxy Domain Name |
| `AllowInsecure` | false |
| `Port` | 443 |
| `Host` | yourAppName.herokuapp.com </br> Cloudflare Reverse Proxy Domain Name |
| `Path` | /$ID-vless |
| `id` | Generate using UUID generator or V2RayN/V2RayNG client generate </br> [uuidgenerator](https://www.uuidgenerator.net/) |
| `Flow` | none |
| `encryption` | none |
| `Transport` | ws |
| `Tls` | Tls must open, otherwise your network was insecure! |

# Trojan Client Setup
| Connection Variables | Values |
| -------------------- | ------ |
| `Address` | yourAppName.herokuapp.com </br> Cloudflare Reverse Proxy IP |
| `SNI` | Cloudflare Reverse Proxy Domain Name |
| `Port` | 443 |
| `Host` | yourAppName.herokuapp.com </br> Cloudflare Reverse Proxy Domain Name |
| `Path` | /$ID-trojan |
| `password` | Generate using UUID generator or V2RayN/V2RayNG client generate </br> [uuidgenerator](https://www.uuidgenerator.net/) |
| `Transport` | ws |
| `Tls` | Tls must open, otherwise your network was insecure! |

# Client Ws+Tls+Xtls-rprx-direct(Flow) Support Status
| Client | Status |
| ------ | ------ |
| `2dust V2RayN` </br> `2dust V2RayNG` | Ws+Tls+Flow |
| `OpenWrt SSRPlus` | Ws+Tls |
| `OpenWrt Passwall` | Ws+Tls |
| ~~`QV2Ray`~~ | ~~Ws+Tls~~ |

# Trojan Ws+Tls Support Status
| Client | Support Trojan ws+tls? |
| ------ | ------ |
| `2dust V2RayN` </br> `2dust V2RayNG` | No, Please use VLESS ws+tls |
| `OpenWrt SSRPlus` | Yes |
| `OpenWrt Passwall` | Yes |

# Cloudflare Reverse Proxy Code (Choose one from both examples)

example 1
```
addEventListener(
  "fetch", event => {
    let url = new URL(event.request.url);
    url.host = "appname.herokuapp.com";
    let request = new Request(url, event.request);
    event.respondWith(
      fetch(request)
    )
  }
)
```

example 2 (recommend)
```
const SingleDay = 'appname.herokuapp.com'
const DoubleDay = 'appname.herokuapp.com'
addEventListener(
    "fetch",event => {
    
        let nd = new Date();
        if (nd.getDate()%2) {
            host = SingleDay
        } else {
            host = DoubleDay
        }
        
        let url=new URL(event.request.url);
        url.hostname="appname.herokuapp.com";
        let request=new Request(url,event.request);
        event. respondWith(
            fetch(request)
        )
    }
)
```

# Acknowledgments

- [Project V](https://github.com/v2fly/v2ray-core.git)
- [Project X](https://github.com/XTLS/Xray-core.git)
- [HeroKu](https://heroku.com)
- [heroku-vless](https://github.com/DanyTPG/heroku-vless.git)
- [Better Cloudflare IP](https://github.com/XIU2/CloudflareSpeedTest.git)

# 重要信息

新用户只需要修改id即可

严禁滥用，因滥用出现的所有问题本人概不负责，且用且珍惜！

本项目不宜做为长期翻墙使用。

出于安全考量，请使用cdn，不要使用自定义域名，以实现VLESS+WS+TLS或Trojan+WS+TLS。

禁止在任何网站宣传本项目！！！！

# Important information

New users only need to modify the id

Abuse is strictly prohibited, I am not responsible for all problems arising from abuse, and use and cherish!

This project is not suitable for long-term use over the wall.

For security reasons, please use cdn instead of custom domain names to implement VLESS+WS+TLS or Trojan+WS+TLS.

It is forbidden to promote this project on any website!!!!
