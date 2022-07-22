### 理论介绍

什么是SpringSecurity？

> Spring Security 是强大的且容易定制的，基于 Spring 开发的实现认证登录与资源授权的应用安全框架

SpringSecurity的核心功能：

- **Authentication**：身份认证，用户登陆的验证（解决你是谁的问题）
- **Authorization**：访问授权，授权系统资源的访问权限（解决你能干什么的问题）

- 安全防护，防止跨站请求，session 攻击等

### SpringSecurity 配置类

- configure(HttpSecurity httpSecurity)
  - 于配置需要拦截的 url 路径、jwt 过滤器及出异常后的处理器
- configure(AuthenticationManagerBuilder auth)
  - 用于配置 UserDetailsService 及 PasswordEncoder
- RestfulAccessDeniedHandler
  - 当用户没有[访问权限](https://so.csdn.net/so/search?q=访问权限&spm=1001.2101.3001.7020)时的处理器，用于返回 JSON 格式的处理结果
- RestAuthenticationEntryPoint
  - 当未登录或 token 失效时，返回 JSON 格式的结果
- UserDetailsService
  - SpringSecurity 定义的核心接口，用于根据用户名获取用户信息，需要自行实现
- UserDetails
  - SpringSecurity 定义用于封装用户信息的类（主要是用户信息和权限），需要自行实现
- PasswordEncoder
  - SpringSecurity 定义的用于对密码进行编码及比对的接口，目前使用的是 BCryptPasswordEncoder
- JwtAuthenticationTokenFilter
  - 在用户名和密码校验前添加的过滤器，如果有 jwt 的 token，会自行根据 token 信息进行登录



### 认证流程

![img](https://img-blog.csdnimg.cn/img_convert/173b0cdc5791da46f738acd54cc1f24c.png)

### 应用结构

> 相关服务划分：
>
> security-oauth2-gateway：网关服务，负责请求转发和鉴权功能，整合 Spring Security+Oauth2
> security-oauth2-auth：Oauth2认证服务，负责对登录用户进行认证，整合 Spring Security+Oauth2
> security-oauth2-api：受保护的 API 服务，用户鉴权通过后可以访问该服务，不整合 Spring Security+Oauth2

![图片](https://img-blog.csdnimg.cn/img_convert/b8c823e462aae759e77cd05d5bb05b8f.webp?x-oss-process=image/format,png)