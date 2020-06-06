# About web security and state management

## Why do we need to get token by code?

## What is SSO?
### SAML 2.0
诞生于2005年，不适用于跨平台场景，比如从手机应用跳到浏览器进行认证
### OAuth 2.0
OAuth 的本意是一个应用允许另一个应用在用户授权的情况下访问自己的数据,OAuth 的设计本意更倾向于授权而非认证（当然授权用户信息就间接实现了认证）
### 区分认证和授权

## JWT
使用 client ID 和私钥创一个签名的 JWT，利用JWT 换区token，然后访问服务器信息，甚至不需要token，直接用JWT 访问
JWT 是哈希的结果，服务端如何验证
```
// signature algorithm
data = base64urlEncode( header ) + “.” + base64urlEncode( payload )
signature = Hash( data, secret );
```

## JWT 与Session

## Ref
不要用JWT替代session管理（上）：全面了解Token,JWT,OAuth,SAML,SSO：https://juejin.im/post/5b3b870a5188251ac85826b8