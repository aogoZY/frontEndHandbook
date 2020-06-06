# 前后端鉴权二三事

## 为啥需要认证和鉴权
### 认证用于确认你是一个合法的用户，比如说掘金必须要登录才能点赞、收藏。
### 鉴权用于确认你有哪些操作权限，比如说你在掘金上不能删除别人创建的文章，但是超级管理员就可以。

## 有哪些认证和鉴权方式？
### Session-Cookie
- 用户先使用用户名和密码登录，登录完成后后端保存一份登录信息，放在session 中，把sessionId 返回给前端，前端保存在cookie 中，后面每次操作带着cookie 去后端，只要后端判断sessionId 没问题且没过期就不需要再次登录
- cookie安全性问题、跨域问题，session耗费服务器资源、分布式session共享问题
### Token 验证（包括 JWT，SSO）
#### JWT
前端拿到的内容：算出签名以后，把 Header、Payload、Signature 三个部分拼成一个字符串，每个部分之间用"点"（.）分隔，就可以返回给用户。
优势：可以放在header 的Authorization 中，不需要cookie，所以可以作为跨域认证授权的解决方案
缺点：一旦 JWT 签发了，到期之前就会始终有效，除非服务器部署额外的逻辑。JWT 一旦泄露，任何人都可以获得该令牌的所有权限。
### OAuth2.0（开放授权）

## Why do we need to get token by code?
token一定是有时间限制的

## Sth About SSO
### Why we need SSO?
### SAML 2.0
诞生于2005年，不适用于跨平台场景，比如从手机应用跳到浏览器进行认证
### OAuth 2.0
OAuth 的本意是一个应用允许另一个应用在用户授权的情况下访问自己的数据,OAuth 的设计本意更倾向于授权而非认证（当然授权用户信息就间接实现了认证）

## Ref
- 不要用JWT替代session管理（上）：全面了解Token,JWT,OAuth,SAML,SSO：https://juejin.im/post/5b3b870a5188251ac85826b8
- 傻傻分不清之 Cookie、Session、Token、JWT：https://juejin.im/post/5e055d9ef265da33997a42cc#heading-22
