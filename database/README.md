
# 数据库设计

## 说明

数据库使用Mongodb，在nodeJS环境中，使用mongoose来进行数据库的连接及增删改查的操作。


## 数据库列表

1. 用户表

* 表名： food_user
* 表结构 
        
        {
            _id: String,    //唯一ID，数据库自动生成
            username: String,   //用户名
            password: String,   //密码
            email: String,       //邮箱
            isDeleted: Boolean,  //是否删除（新增时，默认为false）
            createTime: Date,   //创建时间
            creatorName: String,    //创建人用户名
            updateTime: Date,    //更新时间（修改密码，删除用户时）
            updaterName: String     //更新人用户名
        }
        
2. 餐单表

* 表名： food_menu
* 表结构

        {   
            _id: String,    //唯一id，数据库自动生成
            menuName: String,   //餐单名
            dishes: [{
                dishName: String,   //菜名   
                price: Number   //单价
            }],
            isDeleted: Boolean,     //是否删除
            creatorName: String,   //创建者用户名
            createTime: Date,   //创建时间
            updaterName: String,    //更新者用户名
            updateTime: Date    //更新时间
        }
        
3. 团队表

* 表名： food_team
* 表结构

        {   
            _id: String,    //唯一id,数据库自动生成
            teamName: String,   //团队名
            teamDesc: String,   //团队描述
            members: ['feiyu', 'corona'],   //团队成员
            menus: [{
                menuId: String, //餐单_id
                menuName: String    //餐单名称
            }], //该团队关联餐单
            isDeleted: Boolean,     //是否删除
            creatorName: String,    //创建者用户名
            createTime: Date,       //创建时间
            updaterName: String,    //更新者用户名
            updateTime: Date        //更新时间
        }

4. 订单表

* 表名： food_order
* 表结构

        {
            _id: String,    //唯一id，数据库自动生成
            teamId: String, //团队_id
            menuId: String, //餐单_id
            dishes: [{
                dishId: String, //菜 id值 
                dishName: String,   //菜名
                price: Number,  //单价
                no: Number  //份数
            }],
            members: [String],  //参与点餐的用户
            total: Number,  //订单总价
            status: Number, //订单状态 0: 未完成，1: 已完成，2: 已取消，3: 超时自动取消
            isDeleted: Boolean, //是否删除
            creatorName: String,    //创建者用户名
            createTime: Date,   //创建时间
            updaterName: String, //更新者用户名
            updateTime: Date    //更新时间
        }