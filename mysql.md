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
```
create table category(
  id  int(11) not null auto_increment comment '类别id',
  parent_id  int(11) not null default 0 comment '父类id',
  name varchar(50) not null comment '类别名称',
  status  int(4) default 1 comment '类别状态1：正常 0：废弃',
  create_time datetime comment '创建时间',
  update_time datetime comment '修改时间',
  primary key(id)
)engine=InnoDB default charset=utf8;

## 商品表
create table product(
  id  int(11) not null auto_increment comment '商品id',
  category_id int(11) not null comment '商品类别id，引用类别表id',
  name varchar(100) not null comment '商品名称',
  detail  text comment '商品详情',
  subtitle varchar(200) comment '商品副标题',
  main_image varchar(100) comment '商品主图',
  sub_images varchar(200) comment '商品子图',
  price decimal(20,2) not null comment'商品价格',
  stock int(11) comment '商品库存',
  status  int(6) default 1 comment '商品状态 1.在售 2.下架 3.删除',
  create_time datetime comment '创建时间',
  update_time datetime comment '修改时间',
  primary key(id)
)ENGINE=InnoDB default charset=utf8;
```
## 购物车表
```
create table cart(
  id int(11)  not null auto_increment comment '购物车id',
  user_id  int(11)  not null comment '用户id',
  product_id  int(11)  not null comment '商品id',
  quantity  int(11)  default 1 comment '购买数量',
  create_time datetime comment '创建时间',
  update_time datetime comment '修改时间',
  primary key(id),
  unique key user_id_index(user_id) using btree
)ENGINE=InnoDB  default charset=utf8;
```
## 订单表
```
  create table dorder(
  id           int(11)    not null  auto_increment comment '订单id,主键',
  order_no     bigint(20) not null  comment '订单编号',
  user_id      int(11)  not null  comment '用户id',
  payment      decimal(20,2) not null comment '付款总金额，单位元，保留两位小数',
  payment_type int(4) not null default 1 comment '支付方式 1:线上支付 ',
  status       int(10) not null  comment '订单状态 0-已取消  10-未付款 20-已付款 30-已发货 40-已完成  50-已关闭',   
  shipping_id  int(11) not null comment '收货地址id',
  postage      int(10) not null default 0 comment '运费', 
 payment_time datetime  default null  comment '已付款时间',
  send_time      datetime  default null  comment '已发货时间',
  close_time     datetime  default null  comment '已关闭时间',
  end_time      datetime  default null  comment '已结束时间',
  create_time    datetime  default null  comment '已创建时间',
  update_time    datetime  default null  comment '更新时间',
   PRIMARY KEY(id),
   UNIQUE KEY order_no_index(order_no) USING BTREE
  )ENGINE=InnoDB DEFAULT CHARSET=UTF8;
```
## 订单明细表
```
create table neuedu_order_item(
 id           int(11)    not null  auto_increment comment '订单明细id,主键',
 order_no     bigint(20) not null  comment '订单编号',
 user_id      int(11)  not null  comment '用户id',
 product_id   int(11)  not null comment '商品id',
 product_name varchar(100)  not null comment '商品名称',
 product_image  varchar(100)  comment '商品主图', 
 current_unit_price decimal(20,2) not null comment '下单时商品的价格，元为单位，保留两位小数',
 quantity     int(10)  not null comment '商品的购买数量',
 total_price  decimal(20,2) not null comment '商品的总价格，元为单位，保留两位小数',
 create_time    datetime  default null  comment '已创建时间',
 update_time    datetime  default null  comment '更新时间',
  PRIMARY KEY(id),
  KEY order_no_index(order_no) USING BTREE,
  KEY order_no_user_id_index(order_no,user_id) USING BTREE
)ENGINE=InnoDB DEFAULT CHARSET=UTF8;
```

## 支付表
```
 create table payinfo(
 id           int(11)    not null  auto_increment comment '主键',
 order_no     bigint(20) not null  comment '订单编号',
 user_id      int(11)  not null  comment '用户id',
 pay_platform int(4)  not null default 1  comment '1:支付宝 2:微信', 
 platform_status  varchar(50) comment '支付状态', 
 platform_number  varchar(100) comment '流水号',
 create_time    datetime  default null  comment '已创建时间',
 update_time    datetime  default null  comment '更新时间',
  PRIMARY KEY(id)
 )ENGINE=InnoDB DEFAULT CHARSET=UTF8;
 ```
 ## 地址表
 ```
 create table shipping(
 id       int(11)      not null  auto_increment,
 user_id       int(11)      not  null  ,
 receiver_name       varchar(20)      default   null  COMMENT '收货姓名' ,
 receiver_phone       varchar(20)      default   null  COMMENT '收货固定电话' ,
 receiver_mobile       varchar(20)      default   null  COMMENT '收货移动电话' ,
 receiver_province       varchar(20)      default   null  COMMENT '省份' ,
 receiver_city       varchar(20)      default   null  COMMENT '城市' ,
 receiver_district       varchar(20)      default   null  COMMENT '区/县' ,
 receiver_address       varchar(200)      default   null  COMMENT '详细地址' ,
  receiver_zip       varchar(6)      default   null  COMMENT '邮编' ,
 create_time      datetime      not null   comment '创建时间',
 update_time       datetime      not null   comment '最后一次更新时间',
  PRIMARY KEY(id)
 )ENGINE=InnoDB AUTO_INCREMENT=32 DEFAULT CHARSET=utf8;
 ```
 
 