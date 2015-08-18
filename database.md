# 数据库文档

* v 1.0
* @sidong

---

### _User

用户表

字段 | 类型 | 必填 | 说明
:--- | :---: | :---: | :---:
objectId | String | 是 | 主键
wechatId | String | 否 | 微信 openid
nickname | String | 是 | 昵称，不能为空，长度 1 ~ 20 个字符
avatorUrl | String | 是 | 头像 url
gender | Number | 是 | 0 代表未知，1 代表男性，2 代表女性，默认为 0
mobilePhoneNumber | String | 否 | 手机号
username | String | 是 | 用户名，微信登录用户同 openid
password | String | 是 | 密码，未绑定手机微信登录用户同 openid

### Campus

学校表

字段 | 类型 | 必填 | 说明
:--- | :---: | :---: | :---:
objectId | String | 是 | 主键
name | String | 是 | 学校名
logoUrl | String | 是 | 学校 logo url

### Game

赛事表

字段 | 类型 | 必填 | 说明
:--- | :---: | :---: | :---:
objectId | String | 是 | 主键
name | String | 是 | 赛事名
campusId | Pointer | 是 | 学校指针
award | Number | 是 | 奖金池，默认为 0
awardLimit | Number | 是 | 奖金池上限，0 代表无奖金池
teams | Relation<Team> | 是 | 球队指针数组，默认为空
college | String | 是 | 学院名
isFinished | Bool | 是 | 是否结束，默认 false
follows | Number<计数器> | 是 | 关注人数，默认 0
coverUrl | String | 是 | 赛事海报封面

### GameFollow

赛事关注表

字段 | 类型 | 必填 | 说明
:--- | :---: | :---: | :---:
objectId | String | 是 | 主键
gameId | Pointer | 是 | 赛事指针
userId | Pointer | 是 | 用户指针

### Competition

比赛表

字段 | 类型 | 必填 | 说明
:--- | :---: | :---: | :---:
objectId | String | 是 | 主键
teamAId | Pointer | 是 | 球队A指针
teamBId | Pointer | 是 | 球队B指针
gameId | Pointer | 是 | 赛事指针
reportId | Pointer | 否 | 战况指针
status | String | 是 | "未开始" "进行中" "已完赛"
award | Number | 是 | 奖金池，默认为 0
awardMinimum | Number | 是 | 奖金池下限
awardLimit | Number | 是 | 奖金池上线，0 代表无奖金池
scoreId | Pointer | 是 | 分数指针
statics | String | 否 | 统计
level | Number | 是 | 比赛层级
type | String | 是 | 比赛类型 "小组赛" "A小组" "1/8 决赛" "1/4 决赛" "半决赛" "总决赛"
likesA | Number | 是 | 球队A关注人数，默认为0
likesB | Number | 是 | 球队B关注人数，默认为0
isLived | Bool | 是 | 代表比赛是否会做直播
beginTime | Date | 否 | 比赛开始时间

### CompetitionShare
字段 | 类型 | 必填 | 说明
:--- | :---: | :---: | :---:
objectId | String | 是 | 主键
competitionId | Pointer | 是 | 比赛指针
userId | Pointer | 是 | 用户指针

### TeamFollow

字段 | 类型 | 必填 | 说明
:--- | :---: | :---: | :---:
objectId | String | 是 | 主键
userId | Pointer | 是 | 用户指针
competitionId | Pointer | 是 | 比赛指针
team | Number | 是 | 队伍,1代表A队,2代表B队

### Score

分数表

字段 | 类型 | 必填 | 说明
:--- | :---: | :---: | :---:
objectId | String | 是 | 主键
scoreA | Number | 是 | A 分数，默认 0
scoreB | Number | 是 | B 分数，默认 0

### Team

球队表

字段 | 类型 | 必填 | 说明
:--- | :---: | :---: | :---:
objectId | String | 是 | 主键
name | String | 是 | 球队名
logoUrl | String |　是 | 球队 Logo url
info | String | 是 | 球队简介，默认空

### Report

报道表

字段 | 类型 | 必填 | 说明
:--- | :---: | :---: | :---:
objectId | String | 是 | 主键
title | String | 是 | 标题
content | String | 是 | 内容

### Comment

评论表

字段 | 类型 | 必填 | 说明
:--- | :---: | :---: | :---:
objectId | String | 是 | 主键
userId | Pointer | 是 | 用户指针
content | String | 是 | 评论内容，不为空
likes | Number<计数器> | 是 | 赞数，默认为 0
competitionId | Pointer | 是 | 比赛指针
atUser | Pointer | 否 | 被 @ 的用户

### CommentLike

字段 | 类型 | 必填 | 说明
:--- | :---: | :---: | :---:
objectId | String | 是 | 主键
commentId | Pointer | 是 | 评论指针
userId | Pointer | 是 | 用户指针
