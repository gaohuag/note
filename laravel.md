# laravel标准目录结构

标签（空格分隔）： 

---

## app下的目录结构
├── Console **用户写的命令行**
│   ├── Commands
│   │   ├── CalculateActiveUser.php 生成活跃用户
│   │   ├── GenerateToken.php 快速为用户生成 token
│   │   └── SyncUserActivedAt.php 将用户最后登录时间从 Redis 同步到数据库中
│   └── Kernel.php 配置定时任务等
├── Exceptions **异常处理**
│   └── Handler.php 异常的情况下，记录日志，返回json或者是响应请求。
├── Handlers
│   ├── ImageUploadHandler.php 处理图片上传与裁剪
│   └── SlugTranslateHandler.php 调用百度api，将话题标题翻译为 Slug
├── Http
│   ├── Controllers
│   │   ├── Api
│   │   │   ├── AuthorizationsController.php 第三方登录等
│   │   │   ├── CaptchasController.php 图片验证码
│   │   │   ├── CategoriesController.php  分类
│   │   │   ├── Controller.php 
│   │   │   ├── ImagesController.php 用户头像与话题的图片保存
│   │   │   ├── LinksController.php 资源管理，就是一些外链
│   │   │   ├── NotificationsController.php 通知 列表，未读数，标记已读
│   │   │   ├── PermissionsController.php 当前登录用户权限
│   │   │   ├── RepliesController.php 回复
│   │   │   ├── TopicsController.php 话题
│   │   │   ├── UsersController.php 用户
│   │   │   └── VerificationCodesController.php 短信验证码
│   │   ├── Auth
│   │   │   ├── ForgotPasswordController.php 忘记密码
│   │   │   ├── LoginController.php 登录
│   │   │   ├── RegisterController.php 注册
│   │   │   └── ResetPasswordController.php 重置密码
│   │   ├── CategoriesController.php 分类
│   │   ├── Controller.php
│   │   ├── NotificationsController.php 通知
│   │   ├── PagesController.php 没有管理后台权限的情况，返回没有权限页面，否则到管理界面
│   │   ├── RepliesController.php 回复
│   │   ├── TopicsController.php 话题
│   │   └── UsersController.php 用户
│   ├── Kernel.php 全局中间件 中间件组 中间件别名
│   ├── Middleware
│   │   ├── ChangeLocale.php 设置语言
│   │   ├── EncryptCookies.php Cookie 加密解密
│   │   ├── RecordLastActivedTime.php 记录最后登录时间
│   │   ├── RedirectIfAuthenticated.php 只有游客才能访问，在 register 和 login 请求中使用，只有未登录用户才能访问这些页面
│   │   ├── TrimStrings.php 对提交的请求参数进行 PHP 函数 `trim()` 处理
│   │   ├── TrustProxies.php 修正代理服务器后的服务器参数
│   │   └── VerifyCsrfToken.php 检验 CSRF ，防止跨站请求伪造的安全威胁
│   └── Requests **表单验证的规则写在这里**
│       ├── Api
│       │   ├── AuthorizationRequest.php
│       │   ├── CaptchaRequest.php
│       │   ├── FormRequest.php
│       │   ├── ImageRequest.php
│       │   ├── ReplyRequest.php
│       │   ├── SocialAuthorizationRequest.php
│       │   ├── TopicRequest.php
│       │   ├── UserRequest.php
│       │   ├── VerificationCodeRequest.php
│       │   └── WeappAuthorizationRequest.php
│       ├── ReplyRequest.php
│       ├── Request.php
│       ├── TopicRequest.php
│       └── UserRequest.php
├── Jobs
│   └── TranslateSlug.php 将话题标题翻译为 Slug
├── Listeners
│   └── PushNotification.php 推送ios消息
├── Models **模型**
│   ├── Category.php
│   ├── Image.php
│   ├── Link.php
│   ├── Model.php
│   ├── Reply.php
│   ├── Topic.php
│   ├── Traits
│   │   ├── ActiveUserHelper.php
│   │   └── LastActivedAtHelper.php
│   └── User.php
├── Notifications
│   └── TopicReplied.php 通知作者话题有新回复
├── Observers **定义观察者**
│   ├── LinkObserver.php
│   ├── ReplyObserver.php
│   ├── TopicObserver.php
│   └── UserObserver.php
├── Policies **授权策略**
│   ├── Policy.php
│   ├── ReplyPolicy.php
│   ├── TopicPolicy.php
│   └── UserPolicy.php
├── Providers **服务提供者**
│   ├── AppServiceProvider.php 里面定义了模型对应的观察者
│   ├── AuthServiceProvider.php 里面定义了模型对应的授权策略
│   ├── BroadcastServiceProvider.php 
│   ├── EasySmsServiceProvicer.php
│   ├── EventServiceProvider.php 事件与监听者 事件订阅者
│   ├── JpushServiceProvicer.php JPush服务注册
│   └── RouteServiceProvider.php  路由服务
└── Transformers 定义返回api的实体字段信息，以及实体之间的关系
    ├── CategoryTransformer.php
    ├── ImageTransformer.php
    ├── LinkTransformer.php
    ├── NotificationTransformer.php
    ├── PermissionTransformer.php
    ├── ReplyTransformer.php
    ├── RoleTransformer.php
    ├── TopicTransformer.php
    └── UserTransformer.php

## database目录结构
├── factories 模型工厂定义
│   ├── LinkFactory.php
│   ├── ReplyFactory.php
│   ├── TopicFactory.php
│   └── UserFactory.php
├── migrations ddl语句定义
│   ├── 2014_10_12_000000_create_users_table.php
│   ├── 2014_10_12_100000_create_password_resets_table.php
│   ├── 2017_10_31_164855_add_avatar_and_introduction_to_users_table.php
└── seeds 使用模型工厂生成假数据
    ├── DatabaseSeeder.php
    ├── LinksTableSeeder.php
    ├── ReplysTableSeeder.php
    ├── TopicsTableSeeder.php
    └── UsersTableSeeder.php




