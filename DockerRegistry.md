# 常用Docker镜像仓库

## 方案对比

| 方案特性         | Docker Registry | VMware Harbor     | Sonatype Nexus   | SUSE Portus |
|--------------|-----------------|-------------------|------------------|-------------|
| 系统复杂度        | 简单              | 复杂                | 简单               | 一般          |
| 配置难易度        | 简单              | 复杂                | 一般               | 一般          |
| Web UI管理界面   | 无               | 有                 | 有                | 有           |
| 与外部LDAP/AD集成 | 无               | 有                 | 有                | 有           |
| 访问权限控制       | 弱               | 强                 | 弱                | 强           |
| 镜像复制         | 无               | 支持复制到另一个Harbor镜像库 | 支持Proxy代理到另一个镜像库 | 弱           |
| 镜像扫描         | 无               | 可集成Clair          | 无                | 可集成Clair    | 

## Docker Registry

- 部署简单，只需要运行一个镜像
- 支持TLS和基于签名的身份验证。
- 提供RESTful API以提供外部客户端调用

## VMware Harbor

- Web UI管理界面
- 基于角色的访问控制
- 可以集成LDAP或AD用户认证系统
- 审计日志
- 镜像复制
- 提供RESTful API以提供外部客户端调用
- 镜像安全漏洞扫描（从v1.2版本开始集成了Clair景象扫描工具）

> Harbor相对于Docker Registry，提供了更好的用户管理、角色权限管理、审计日志，以及多个Harbor镜像仓库之间的镜像复制功能，可以用作企业私有镜像库的服务器。不过由于Harbor的组件较多，所以与外界的集成较为复杂。

## Sonatype Nexus

- 提供Web UI管理界面
- 部署简单，通过启动一个容器即可完成
- 支持TLS安全认证
- 支持代理仓库（Docker Proxy），可以将到Nexus镜像仓库的操作代理到另一个远程镜像库
- 支持仓库组（Docker Group），可以把多个仓库组合成一个地址提供服务
- 除了支持Docker镜像，还支持对其他软件仓库的管理，例如：Yum、Npm等。

> 主要有2.X和3.X两个大版本。2.X版本主要支持Maven、P2、OBR、Yum等仓库软件；3.X版本主要支持Docker、NuGet、npm、Bower、PyPI、Ruby Gems、Apt、Conam、R、CPAN、Raw、Helm等仓库软件，也支持构建工具Maven。


## SUSE Portus

- Web UI管理界面
- 基于组（Team）和命名空间（Namespace）的细粒度访问权限控制
- 可以集成LDAP用户认证系统，也支持OAuth
- 审计日志
- 提供RESTful API，以供外部客户端调用
- 镜像安全漏洞扫描（集成Clair镜像扫描工具）
 
