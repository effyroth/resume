

#信息流串讲

[TOC]

名词解释
moment:动态
tantan-backend-moment:信息流服务
#信息流
##业务
###app功能
|业务|
|:
|动态
|话题
|音乐
|贴纸
|滤镜
|点赞
|评论
|通知
|设置
|关注
###业务泳道图


##技术
###系统架构
####整体架构图
###系统模块
|系统|备注|
|:
| moment-service | 用户信息流功能 |
| moment-worker	| dcl消息异步处理 |
| moment-cms	| 运营 |

|关联系统|备注
|:
|moderation |内容审核
|dcl |消息队列
|user |用户系统
|counter |记数统计
|eventlog |业务事件消息
#### 模块关系图
#### 数据流转图


----------


###消息队列
|生产事件
|:
|dcl.block
|dcl.userStatusChange
|dcl.popularity
|dcl.user
|dcl.moment
|dcl.momentLike
|dcl.moderation.comment
|dcl.moderation.moment

|消费事件
|:
|1


----------


###数据库
postgresql shard
(1*master + 1* slave) * 16
|表|描述
|:
|moments|动态
|moment_comments|动态评论
|moment_likes|动态点赞
|feeds|关注信息流
|activities|消息通知
|user_feed_settings
|user_read_moments
|medias
|musics
|music_moments
|followships|关注
|nearby_moments|附近信息流
|user_read_recommend_moments
|viewers
|
|brand_account_moment_comments|小助手
|brand_account_moment_likes|小助手
|
|user_search.users|用户
|user_search.brand_account_moments|小助手
|user_search.inspired_comments
|user_search.user_deleted_moments
|user_search.gender
|camera.camera_stickers|贴纸
|camera.category_stickers
|camera.camera_filters|滤镜


----------


###缓存
redis*16
|业务|描述
|:
|topic|话题
|inspiredMessage|小助手评论
|cameraCategories|贴纸分类
|cameracategoryList|贴纸分类
|user|陌生用户
|sticker|贴纸

cache key缺少规范太随意,一般需要带业务名称用:分割


----------


动态

发布->审核→展示



内容过滤



数据冗余

user

消费用户新增状态更新消息,异步同步多个moment分库,用于联表查询过滤条件



nearby moment 附近动态

审核通过后异步写表(经纬度分库分表)



feed moment 朋友圈

审核通过后异步写表(userid分库分表,写扩散)


----------


###moment代码逻辑
|层级|功能|说明
|:
|接口层|http|APP调用
||rpc|内部调用
|通用层|request parse|请求解析
||参数合法性校验|类型,空数据等
||tracer|分布式跟踪
||eventlog|业务数据采集
|业务层|数据校验|取值范围等
||权限校验| 用户权限 用户对资源权限
||数据访问|db cache 等
||数据过滤|可见性
||数据填充|关联数据
||数据转换| po;domain;external对象转换 国际化等
||异步逻辑 |dcl 等



问题
sql 事务

消息事务
