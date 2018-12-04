# 数据库设计
# 创建数据库
```
    create database dspt;
    use dspt;
``` 
## 用户表
```
create table user(
  id  int(11) not null comment '用户id',
  username  varchar(50) not null comment '用户名',
  password  varchar(50) not null comment '密码',
  email  varchar(50) not null comment '邮箱',
  phone  varchar(11) not null comment '电话',
  question varchar(100) not null comment '密保问题',
  answer varchar(100) not null comment '密保答案',
  role  int(4) default 1 comment '用户角色',
  create_time datetime comment '创建时间',
  update_time datetime comment '修改时间',
  primary key(id),
  unique key user_name_index(username)using btree
)engine=InnoDB default charset=utf8;
```
## 类别表
create table vategory(
  id  int(11) not null auto_increment comment '类别id',
  parent_id  int(11) not null default 0 comment '父类id',
  name varchar(50) not null comment '类别名称',
  
);