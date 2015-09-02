# 数据库文档

* v 1.0.0
* @empty

---

### _User

用户表

字段 | 类型 | 必填 | 说明
:--- | :---: | :---: | :---:
objectId | String | 是 | 主键
ID | String | 否 | 身份证号码，完善资料时必填
name | String | 否 | 真实姓名，完善资料时必填
avatorUrl | String | 否 | 头像 url
email | String | 是 | 邮箱
mobilePhoneNumber | String | 否 | 手机号，完善资料时必填
username | String | 是 | 用户名
password | String | 是 | 密码
requirement | String | 否 | 用户符合条件，完善资料时必填

### Gradient

梯度表

字段 | 类型 | 必填 | 说明
:--- | :---: | :---: | :---:
objectId | String | 是 | 主键
projectId | Pointer | 是 | 对应的项目指针
money | Number | 是 | 梯度对应融资量
number | Number | 是 | 梯度预定的人数
start | Date | 是 | 梯度筹集开始的时间
end | Date | 是 | 梯度结束筹集的时间

### Leader

领头人表

字段 | 类型 | 必填 | 说明
:--- | :---: | :---: | :---:
objectId | String | 是 | 主键
userId | Pointer | 是 | 领头人对应用户指针
projectId | Pointer | 是 | 项目指针
identify | String | 是 | 领头人身份
sendword | String | 是 | 领头人寄语

### Project

项目表

字段 | 类型 | 必填 | 说明
:--- | :---: | :---: | :---:
objectId | String | 是 | 主键
name | String | 是 | 项目名称
amount | Number | 是 | 项目融资目标金额
start | Date | 是 | 项目融资开始时间
end | Date | 是 | 项目融资结束时间

### ProjectFollow

跟投表

字段 | 类型 | 必填 | 说明
:--- | :---: | :---: | :---:
objectId | String | 是 | 主键
projectId | Pointer | 是 | 项目指针
gradientId | Pointer | 是 | 梯度指针
userId | Pointer | 是 | 用户指针
isLeader | Boolean | 是 | 是否为领头人，默认是false，是的话值为true
isVerify | Boolean | 是 | 信息是否认证通过，默认是false，通过之后值为true
