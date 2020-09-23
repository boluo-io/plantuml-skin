# PlantUML Skin

## Default Skin

### Code

```plantuml
@startuml
!include skin-default.puml

== 登录过程 ==

用户 -> 认证中心: 登录操作
认证中心 -> 缓存: 存放token
note right: key=token+ip,value=token
用户 <- 认证中心 : 认证成功返回token

== 认证过程 ==

用户 -> 认证中心: 下次访问头部携带token认证
认证中心 -> 缓存: key=token+ip获取token

alt 验证通过
其他服务 <- 认证中心: 存在且校验成功则跳转到用户请求的其他服务
其他服务 -> 用户: 信息
end

alt 验证未通过
认证中心 -> 用户: 验证通过，跳转到登录页面
end

@enduml
```

### Image
![](https://raw.githubusercontent.com/ken-io/plantuml-skin/master/preview/preview-skin-default.png)
