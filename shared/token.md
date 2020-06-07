# 前后端鉴权二三事

## 为啥需要认证和鉴权
- 认证用于确认你是一个合法的用户，比如说掘金必须要登录才能点赞、收藏。
- 鉴权用于确认你有哪些操作权限，比如说你在掘金上不能删除别人创建的文章，但是超级管理员就可以。

## 有哪些认证和鉴权方式？
### Session-Cookie
- 用户先使用用户名和密码登录，登录完成后后端保存一份登录信息，放在session 中，把sessionId 返回给前端，前端保存在cookie 中，后面每次操作带着cookie 去后端，只要后端判断sessionId 没问题且没过期就不需要再次登录
- cookie安全性问题、跨域问题，session耗费服务器资源、分布式session共享问题
### Token 验证（包括 JWT，SSO）
#### JWT
前端拿到的内容：算出签名以后，把 Header、Payload、Signature 三个部分拼成一个字符串，每个部分之间用"点"（.）分隔，就可以返回给用户。
优势：可以放在header 的Authorization 中，不需要cookie，所以可以作为跨域认证授权的解决方案
缺点：一旦 JWT 签发了，到期之前就会始终有效，除非服务器部署额外的逻辑。JWT 一旦泄露，任何人都可以获得该令牌的所有权限。
### SSO
#### Why we need SSO?
DevCloud 下有那么多微服务，比如项目管理、代码托管、代码检查、流水线、编译构建等，大家需要认证的时候都去一个地方，然后认证完了之后状态可以共享。
#### SAML 2.0
诞生于2005年，不适用于跨平台场景，比如从手机应用跳到浏览器进行认证
#### OAuth 2.0
OAuth 的本意是一个应用允许另一个应用在用户授权的情况下访问自己的数据,OAuth 的设计本意更倾向于授权而非认证（当然授权用户信息就间接实现了认证）
> OAuth 引入了一个授权层，用来分离两种不同的角色：客户端和资源所有者。......资源所有者同意以后，资源服务器可以向客户端颁发令牌。客户端通过令牌，去请求数据。
为什么要用code 换token，因为code 会直接显示在浏览器的url 上，不安全，别人看到code 没用，因为code 有时效性。

## 那么多概念，用什么故事可以把他们串联在一起？
在日常开发过程中，我们为什么会同时接触到session 和token？按理来说，session 和token 是用于认证授权的两种方式？

#### CAS

CAS （Central Authentication Service）中央认证服务，是一款不错的Web 应用的单点登录框架，包含CAS Server、CAS Client 和Web Browser 三个概念。CAS的核心就是Ticket，中文称之为票据。

#### TGC

1、是什么

Ticket-granting cookie(TGC) ：存放用户身份认证凭证的 cookie ，在浏览器和 CAS Server 间通讯时使用，并且只能基于安全通道传输（ Https ），是 CAS Server 用来明确用户身份的凭证；

2、为什么需要？

同一公司中的AB两个子服务都依赖C做单点登录，用户在A登录以后，如果跳转到B进行访问，不需要再次登录，这个过程就是由TGC保障的，用户浏览器带着TGC到C（C根据这个TGC找到一个TGT，存放的是用户的信息），C判断这是一个已登录用户，告诉B可以直接访问资源。

3、TGC过期规则是如何设置的？

可以在cas.properties中进行配置，默认八小时，无操作，默认两小时。

#### ST

ST票据过期配置，默认时间是10秒钟。所以需要用ST换取token？然后用session 管理token，可以维持一个小时不过期

Ref：

https://blog.csdn.net/yushenzaishi/article/details/80435343

## Ref
- 不要用JWT替代session管理（上）：全面了解Token,JWT,OAuth,SAML,SSO：https://juejin.im/post/5b3b870a5188251ac85826b8
- 傻傻分不清之 Cookie、Session、Token、JWT：https://juejin.im/post/5e055d9ef265da33997a42cc#heading-22
