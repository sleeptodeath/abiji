

教程:

> Vue官方教程：https://cn.vuejs.org/v2/guide/　，　虽然实践内容虽然用不上，但是日后要经常查阅。
>
> Axios官方文档： https://github.com/axios/axios
>
> Vue-router官方教程： https://router.vuejs.org/zh/
>
> Blog:
>
> https://blog.csdn.net/Neuf_Soleil/article/details/88925013
>
> GitHub地址:
>
> https://github.com/Antabot/White-Jotter
>
> ElementUI官网: https://element.eleme.cn/#/zh-CN





### 2 技术栈

#### 2.1 前端技术栈

1. Vue.js 

2. ElementUI

3. axios

#### 2.2 后端技术栈

1. SpringBoot
2. SpringSecurity 未用到 

3. MySql

### 2.3 服务器

前端服务器: Nginx

后端服务器: Tomcat



服务器: 华为云

​	ip: 119.3.211.100

​	name: root

​	password: xqy123456.

### 2.4 IDE

1. IDEA

   

### 需求分析

书籍,影视,小组

登录注册

检索

评论

管理员--管理小组成员



## Vue.js设计

#### 页面:

主页: 

path: / 

包括内容：流行书籍，流行影视





## 华为云部署教程

### SpringBoot项目构建部署

参照软工Lab6课件

#### 构建

模板选Maven，构建步骤默认，记住构建包的路径，需要填到部署中，执行构建

#### 部署

模板选SpringBoot应用部署，选择主机组，

如果第一次部署，删去停止SpringBoot服务，

启动/停止SpringBoot服务:

​	服务操作类型：停止服务

​	服务对应的绝对路径: /usr/local/构建时的包名， 

选择部署来源: 

​	选择源类型： 构建任务

​	部署目录： /usr/local	

启动SpringBoot服务:

​	服务操作类型：启动服务

​	服务对应的绝对路径：/usr/local/构建时的包名(demo-0.0.1-SNAPSHOT.jar)

​	命令行参数: --server.port=8080  (设置访问端口)

### Vue构建部署

构建

部署在nginx下







## Vue知识

### 一.安装Vue Cli

#### Step1： 安装Nodejs

win10安装见： `编程环境配置中的Nodejs安装`

需要使用npm进行安装，npm集合在Node.js中，`先安装Node.js`

验证Node.js是否安装成功

```
node -v
npm -v
```

之后可以选择安装 cnpm，即 npm 的国内镜像。使用 cnmp 的好处是在日后下载内容时会比较快，但是下载的包可能不是最新的。安装 cnpm 的命令为

```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

#### Step2： 使用npm安装Vue-cli

```shell
npm install -g vue-cli

# -g 全局安装
```

#### Step3: 创建工程项目

​	使用一下命令行创建,这里 webpack 是以 webpack 为模板指生成项目，还可以替换为 pwa、simple 等参数。 wj-vue 是我们的项目名称，也可以起别的名字。

​	程序执行的过程中会有一些提示，可以按照默认的设定一路回车下去, 但要选择vue-router和es-lint

```shell
mkdir workspace # 创建工作目录
cd workspace 

vue init webpack wj-vue  # wj-vue 项目名称，
```

vue-cli创建的项目图，其中我们最常修改的部分就是 components 文件夹了，几乎所有需要手动编写的代码都在其中。

![](/media/xuqingyuan/Data/Study/biji/img/vue-cli-directory.png)

#### Step4： 运行测试

进入项目目录，使用npm install安装项目所需的依赖包，即node_modules. 执行npm run dev进行测试

```shell
# 进入工作目录
cd wj-vue

# 安装依赖包
npm install 

# 执行
npm run dev

# 接着可以访问 http://localhost:8080, 进行测试，查看Demo
```



### 二. 安装axios进行反向代理

#### Step1: 使用npm进行安装axios

```shell
npm instsall axios --save

# --save安装会保存到package.json,  等价于 npm i axios -S
```

#### Step2: 在main.js引入axios 

```
// １导入axios, 设置反向代理
import axios from 'axios'

// ２设置反向代理，前端请求默认发送到 http://localhost:8443/api,
// 注意：部署到服务器上，要将localhost替换成具体的IP地址
axios.defaults.baseURL = 'http://localhost:8443/api'

// ３全局注册，之后可在其他组件中通过 this.$axios 发送数据
Vue.prototype.$axios = axios
```

#### Step3: 在config/index.js中配置跨域支持

找到 proxyTable 位置，修改为以下内容

```
proxyTable: {
      '/api': {
        target: 'http: //localhost:8443',
        changeOrigin: true,
        pathRewrite: {
          '^/api': ''
        }
      }
    },
```

#### Step4: 使用

```js
this.$axios
    .post('/login', {
		username: this.loginForm.username,
		password: this.loginForm.password
	})
    .then(successResponse => {
        if (successResponse.data.code === 200) {
          this.$router.replace({path: '/index'})
        }
	})
    .catch(failResponse => {
        console.log(failResponse.data)
        console.log(failResponse.status)
	})

```



### 三. 安装Element-UI，利用组件搭建网站

#### Step1： 使用npm安装element-ui

```
npm install element-ui --save

# --save安装会保存到package.json, 
```

#### Step2: 在main.js中引入element-ui

```
import ElementUI from 'element-ui'
import 'element-ui/lib/theme-chalk/index.css'

Vue.use(ElementUI)
```



### 四. 使用History模式

Hash模式 #

#### Step1: 使用History模式

router/index.js中加入 `mode: 'history'`

```
export default new Router({
  mode: 'history',
  routes: [
    {
      path: '/login',
      name: 'Login',
      component: Login
    },
  ]
}）
```

运行项目，访问不加 `#` 号的 http://localhost:8080/login ，成功加载页面。



### 五. Vuex 与前端登录拦截器

#### Step1: 引入Vuex

```
npm install vuex --save
```

在src目录下新建文件夹`store`, 并在store中新建`index.js`

```
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex)

export default new Vuex.Store({
  state: {
    user: {
      username: window.localStorage.getItem('user' || '[]') == null ? '' : JSON.parse(window.localStorage.getItem('user' || '[]')).username
    }
  },
  mutations: {
    login (state, user) {
      state.user = user
      window.localStorage.setItem('user', JSON.stringify(user))
    }
  }
})
```

这里我们还用到了 `localStorage`，即本地存储，在项目打开的时候会判断本地存储中是否有 user 这个对象存在，如果存在就取出来并获得 `username` 的值，否则则把 `username` 设置为空。这样我们只要不清除缓存，登录的状态就会一直保存。



## Spring Boot知识

### 构建项目

这里采用idea进行快速构建, 多练习几次就会了



#### 注解

|                                                     |                                             |      |
| --------------------------------------------------- | ------------------------------------------- | ---- |
| @Controller                                         | 控制类，                                    |      |
| @CrossOrigin                                        | 防止跨域攻击                                |      |
| @ResponseBody                                       | 返回json数据                                |      |
| @PostMapping(value='login')                         | Post请求                                    |      |
| @GetMapping(value='login')                          | Get请求                                     |      |
|                                                     |                                             |      |
| @GeneratedValue(strategy = GenerationType.IDENTITY) | JPA中，主键生成策略，<br />IDENTITY自动增长 |      |
|                                                     |                                             |      |
| @Entity                                             | 实体类                                      |      |
| @Service                                            |                                             |      |
| @Id                                                 | 标识主键                                    |      |
| @Autowired                                          |                                             |      |
|                                                     |                                             |      |
|                                                     |                                             |      |
|                                                     |                                             |      |
|                                                     |                                             |      |
|                                                     |                                             |      |
|                                                     |                                             |      |
|                                                     |                                             |      |



### 引入MySql数据库

#### Step1: 修改pom.xml， 添加配置依赖

在pom.xml中添加jpa和mysql

```
<!-- jpa-->
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>

<!-- mysql-->
<dependency>
	<groupId>mysql</groupId>
	<artifactId>mysql-connector-java</artifactId>
</dependency>

```

#### Step2: 在application.properties中配置mysql

jpa会使用properties中的datasource的配置，

jpa使用hibernate实现，spring.jpa.hibernate.ddl-auto用来数据库初始化

```
# mysql配置
spring.datasource.url=jdbc:mysql://127.0.0.1:3306/white_jotter?characterEncoding=UTF-8
spring.datasource.username=root  
spring.datasource.password=123456 	
spring.jpa.hibernate.ddl-auto = none
```

#### Step3: 通过继承JpaRepository构建DAO

这里关键的地方在于方法的名字。由于使用了 JPA，无需手动构建 SQL 语句，而只需要按照规范提供方法的名字即可实现对数据库的增删改查。

```java
// <类名,　主键类型>
public interface UserDAO extends JpaRepository<User,Integer> {
    User findByUsername(String username);
    User getByUsernameAndPassword(String username,String password);
}

```



### SpringBoot Mysql JPA, RESTFUL CRUD 

> 入门案例Note教程： https://www.callicoder.com/spring-boot-rest-api-tutorial-with-mysql-jpa-hibernate/

API测试： postman

### JPA方法

```JAVA
// 查找
List<T> findAll();

userDAO.findByUsername(username)
userDAO.findByUsernameAndPassword(username, password)
// 保存
userDAO.save(user) 
```



### 登录拦截