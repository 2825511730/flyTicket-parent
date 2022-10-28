@文章目录[toc]


![微信扫码关注这个有温度的程序猿](https://img-blog.csdnimg.cn/c5b40e17bc614f5d99a5d6e179a0447b.png )

获取完整源码请关注公众号：【IT学长】，回复关键词“基于web的机票管理系统”或者“机票管理系统”

开发文档：[《基于Web的机票管理系统设计与实现（附源码下载地址）》](https://mp.weixin.qq.com/s/G9JiMfcU6Mucp1_rP0A2MA)

运行教程：[《基于Web的机票管理系统运行教程》](https://mp.weixin.qq.com/s/L0Q1dUzOSckPxpURsUu6Eg)


近年来，我国发展迅速，对交通工具的需求量大幅度增加。飞机作为出行工具之一，花费时间短、用户体验度好，价格实惠、安全性高等优点自然成为人们的首选，这也导致等待时间长、购票效率低等一系列问题的出现，给用户和航空公司造成严重困扰。面对这些问题，在线机票预订系统显得格外重要。

本系统使用Eclipse开发工具，使用Redis、MySQL数据库，采用MVC三层架构的方式，结合当前最流行的SSM框架以及支付宝沙箱支付环境来实现各个功能。系统分为用户端和管理员端。用户端实现了用户注册与登录、用户评论、机票查询，机票预订，订单查询、广告展示等功能。管理员端包括航班信息管理模块、订单信息管理模块、用户信息管理模块、留言评论管理模块、广告信息管理模块、个人信息管理模块等六大模块，具有开放体系结构的、易扩充的、易维护的、具有良好人机界面的优点。

经过充分的测试，测试数据均正确无误，各个模块运行良好。机票预订系统的推出，为乘客出行提供方便，便于机场工作人员对机票信息进行管理，提高了机场工作人员对机票管理的工作效率。

**关键词：机票预订系统； 数据库； MVC； SSM； 面向对象**

## 1 相关技术

#### 1.1 Java web

Java Web，是用Java技术来解决相关web互联网领域的技术总和。随着Web互联网技术的出现和推广，基于Java技术的Java Web技术应运而生，并为解决互联网相关问题提出解决方案。我们知道，Web是由服务器和客户端两方面组成，基于Java语言的Web框架有很多种，用以适用不同的技术需求，但是都遵循最基本的原则和技术路线，即采用了MVC的架构设计思想，并通过Servlet或者Filter进行请求拦截，同时使用约定，XML或Annotation来实现必备的相关配置，充分利用其面向对象的特质，实现前台用户请求和后台程序响应的工作流程。

#### 1.2 三大框架SSM

SSM框架，是Spring + Spring MVC + MyBatis的缩写，这个是继SSH之后，目前比较主流的Java EE企业级框架，适用于搭建各种大型的企业级应用系统。

Spring是一个开源框架，Spring是于2003年兴起的一个轻量级的Java开发框架，由Rod Johnson在其著作Expert One-On-One J2EE Development and Design中阐述的部分理念和原型衍生而来。它是为了解决企业应用开发的复杂性而创建的。Spring使用基本的JavaBean来完成以前只可能由EJB完成的事情。然而，Spring的用途不仅限于服务器端的开发。从简单性、可测试性和松耦合的角度而言，任何Java应用都可以从Spring中受益。 简单来说，Spring是一个轻量级的控制反转（IoC）和面向切面（AOP）的容器框架。

Spring MVC属于Spring Framework的后续产品，已经融合在Spring Web Flow里面，它原生支持的Spring特性，让开发变得非常简单规范。Spring MVC 分离了控制器、模型对象、分派器以及处理程序对象的角色，这种分离让它们更容易进行定制。

MyBatis本是apache的一个开源项目iBatis, 2010年这个项目由apache software foundation 迁移到了google code，并且改名为MyBatis 。MyBatis是一个基于Java的持久层框架。iBATIS提供的持久层框架包括SQL Maps和Data Access Objects（DAO）MyBatis消除了几乎所有的JDBC代码和参数的手工设置以及结果集的检索。MyBatis使用简单的XML或注解用于配置和原始映射，将接口和Java的POJOs（Plain Old Java Objects，普通的 Java对象）映射成数据库中的记录。

#### 1.3 前端框架AngularJS

AngularJS是一个开发动态Web应用的框架。它让你可以使用HTML作为模板语言并且可以通过扩展的HTML语法来使应用组件更加清晰和简洁。它的创新之处在于，通过数据绑定和依赖注入减少了大量代码，而这些都在浏览器端通过JavaScript实现。

#### 1.4 数据库MySQL

MySQL是一种开放源代码的关系型数据库管理系统（RDBMS），使用最常用的数据库管理语言--结构化查询语言（SQL）进行数据库管理。MySQL是开放源代码的，因此任何人都可以在General Public License的许可下下载并根据个性化的需要对其进行修改。MySQL因为其速度、可靠性和适应性而备受关注。大多数人都认为在不需要事务化处理的情况下，MySQL是管理内容最好的选择。

#### 1.5 数据库Redis 

Redis（Remote Dictionary Server )，即远程字典服务，是一个开源的使用ANSI C语言编写、支持网络、可基于内存亦可持久化的日志型、Key-Value数据库，并提供多种语言的API。

Redis是一个key-value存储系统。和Memcached类似，它支持存储的value类型相对更多，包括string(字符串)、list(链表)、set(集合)、zset(sorted set --有序集合)和hash（哈希类型）。这些数据类型都支持push/pop、add/remove及取交集并集和差集及更丰富的操作，而且这些操作都是原子性的。在此基础上，redis支持各种不同方式的排序。与memcached一样，为了保证效率，数据都是缓存在内存中。区别的是redis会周期性的把更新的数据写入磁盘或者把修改操作写入追加的记录文件，并且在此基础上实现了master-slave(主从)同步。

#### 1.6 开发工具Eclipse

Eclipse 是一个开放源代码的、基于Java的可扩展开发平台。就其本身而言，它只是一个框架和一组服务，用于通过插件组件构建开发环境。幸运的是，Eclipse附带了一个标准的插件集，包括Java开发工具（Java Development Kit，JDK）。

## 2 需求分析

#### 2.1 系统实现目标

如今，互联网遍布于生活的每个角落，不断改变着人们的生产生活，基于Web的机票预订系统就是借助互联网发展的热潮，方便大众，服务大众。具体实现以下两个目标：

 （1）	方便用户购票
 
用户可以访问前台系统浏览、查询航班信息，足不出户，预订机票，免去了以往寻找购票网点，排队购票的麻烦。

（2）	航空公司实现办公自动化

后台系统能使航空公司办事效率大幅度提高，它将所有的工作流程按照一系列流程进行规范化，从而减少工作时间，提高了人员的办事效率。

#### 2.2 系统功能分析

 - 后台航班信息管理：主要是指添加航班信息，删除航班信息，查询航班信息和航班信息详细情况查看等。
 - 
   后台订单信息管理：后台订单信息管理主要包括订单列表，查询订单信息，订单信息的删除等。
 
 - 后台用户信息管理：主要指注册用户的展示与按条件查询注册用户。

 - 后台留言评论管理：主要指展示用户的留言信息和按留言日期、留言用户查找留言信息等。

 - 后台广告信息管理：主要指添加广告信息，删除广告信息，设置广告的有效性等。

 - 后台个人信息管理：主要指查看个人信息，修改个人信息。

 - 前台登录与注册管理：包括前台系统用户的注册与登录。

 - 前台首页信息展示：主要是指航班信息展示、航班信息查询、航班信息详情、登录用户信息展示、留言板和个人信息详情与修改等。

 - 前台订单页面：主要是订单内容的填写和订单详情。 
 
 - 前台订单支付：是指使用支付宝沙箱环境支付订单。
 
 - 前台订单查询页面：查询当前登录用户所有历史订单信息。
 
 - 前台用户登录、注册：用于用户登录、注册。

#### 2.3 系统用例图

**系统前台功能用例图**

![](https://img-blog.csdnimg.cn/2020062913054442.png)

**系统后台功能用例图**

![](https://img-blog.csdnimg.cn/20200629130651305.png)

## 3 工程结构及其说明

下载本项目源码并导入到Eclipse后，工程结构目录如下图所示：

![](https://img-blog.csdnimg.cn/24699f1c519d4b0c847bfeff130d473f.png)

| 名称 | 解释 |
|--|--|
| flyTicket-parent | 父工程，用于管理子项目（如：maven依赖版本） |
| flyTicket-dao | 子项目，用于存放所有对数据库的操作文件  |
| flyTicket-pojo |  子项目，用于存放所有Java实体类文件 |
| flyTicket-manage-web | 子项目，用于存放后台系统页面文件、controller文件  |
| flyTicket-manage-service | 子项目，用于后台系统业务逻辑实现  |
|flyTicket-portal-web  | 子项目，用于存放前台系统页面文件、controller文件  |
| flyTicket-portal-service |  子项目，用于前台系统业务逻辑实现  |


## 4 系统总体设计

#### 4.1 软件架构设计

此项目使用经典的三层架构模式，分别是表现层，业务逻辑层和数据持久层，如下图所示。

![](https://img-blog.csdnimg.cn/20200629161925742.png)

表现层：表现层也称为表示层，位于最外层（最上层），离用户最近。用于显示数据和接收用户输入的数据，为用户提供一种交互式操作的界面。

业务逻辑层：业务逻辑层（Business Logic Layer）无疑是系统架构中体现核心价值的部分。它的关注点主要集中在业务规则的制定、业务流程的实现等与业务需求有关的系统设计，也即是说它是与系统所应对的领域（Domain）逻辑有关，很多时候，也将业务逻辑层称为领域层。

数据持久层：数据持久层也称为是数据访问层，其功能主要是负责数据库的访问，可以访问数据库系统、二进制文件、文本文档或是XML文档。简单的说法就是实现对数据表的select、insert、update以及delete的操作。

#### 4.2 总体功能模块设计

本系统主要分为前台子系统和后台子系统，两个子系统包含的具体功能如下：

1.	前台子系统功能包括：
A.	用户登录
B.	用户注册
C.	航班查询
D.	机票详情
E.	机票预订
F.	订单支付
G.	订单查看
H.	用户留言
I.	个人信息查看与修改

2.	后台子系统功能包括：
A.	航班信息管理
B.	订单信息管理
C.	用户信息管理
D.	留言评论管理
E.	广告管理
F.	个人信息管理
	
前台子系统和后台子系统详细功能如下图所示：

![](https://img-blog.csdnimg.cn/20200629162123983.png)

（1）	前台子系统功能设计

A.	用户登录功能，详细功能说明如表4.1所示

![](https://img-blog.csdnimg.cn/20200629162203700.png)

B.	用户注册功能，详细功能说明如表4.2所示

![](https://img-blog.csdnimg.cn/20200629162233245.png)

C.	航班查询功能，详细功能说明如表4.3所示

![](https://img-blog.csdnimg.cn/2020062916225818.png)

D.	机票详情功能，详细功能说明如表4.4所示

![](https://img-blog.csdnimg.cn/20200629162329946.png)

E.	机票预订功能，详细功能说明如表4.5所示

![](https://img-blog.csdnimg.cn/20200629162359190.png)

F.	订单支付功能，详细功能说明如表4.6所示

![](https://img-blog.csdnimg.cn/20200629162434840.png)

G.	订单查看功能，详细功能说明如表4.7所示

![](https://img-blog.csdnimg.cn/20200629162503226.png)

H.	用户留言功能，详细功能说明如表4.8所示

![](https://img-blog.csdnimg.cn/20200629162541553.png)

I.	个人信息查看与修改功能，详细功能说明如表4.9所示

![](https://img-blog.csdnimg.cn/20200629162642681.png)

（2）	后台子系统功能设计

A.	航班信息管理模块功能，详细功能说明如表4.10所示

![](https://img-blog.csdnimg.cn/20200629162734948.png)

B.	订单信息管理模块功能，详细功能说明如表4.11所示

![](https://img-blog.csdnimg.cn/20200629162803297.png)

C.	用户信息管理模块功能，详细功能说明如表4.12所示

![](https://img-blog.csdnimg.cn/20200629162830600.png)

D.	留言评论管理模块功能，详细功能说明如表4.13所示

![](https://img-blog.csdnimg.cn/20200629162857199.png)

E.	广告管理模块功能，详细功能说明如表4.14所示

![](https://img-blog.csdnimg.cn/20200629162923133.png)

F.	个人信息管理模块功能，详细功能说明如表4.15所示

![](https://img-blog.csdnimg.cn/20200629163025889.png)

#### 4.3 数据库设计

##### 4.3.1 数据库结构设计

通过建立该系统各个模块的E-R图，使整个模块之间的功能变得更加清晰，模块间所具有的耦合性变的越低。管理员实体（Admin），留言评论实体（Discuss），航班实体（Flight），订单（Order）实体，普通用户实体（User）和广告信息实体（content）E-R图分别如下图所示。


**管理员实体（Admin）E-R图**

![](https://img-blog.csdnimg.cn/20200629163219407.png)

**留言评论实体（Discuss）E-R图**

![](https://img-blog.csdnimg.cn/20200629163243659.png)

**航班实体（Flight）E-R图**

![](https://img-blog.csdnimg.cn/20200629163314340.png)


**订单实体（Order）E-R图**

![](https://img-blog.csdnimg.cn/20200629163338765.png)

**普通用户实体（User）E-R图**

![](https://img-blog.csdnimg.cn/20200629163406306.png)

**广告信息实体（Content）E-R图**

![](https://img-blog.csdnimg.cn/20200629163437515.png)

##### 4.3.2 数据库表设计

为实现数据库的设计，对数据进行分表处理，每一个表格代表不同的信息和功能，分别如下图所示。


1.	管理员信息表（admin），用于存放管理员信息，表结构如表4.16所示

![](https://img-blog.csdnimg.cn/20200629163612350.png)

2.	留言评论信息表（discuss），用于存放留言评论信息，表结构如表4.17所示

![](https://img-blog.csdnimg.cn/20200629163642277.png)

3.	航班信息表（flight），用于存放航班信息，表结构如表4.18所示

![](https://img-blog.csdnimg.cn/20200629163711492.png)

4.	订单信息表（order），用于存放订单信息，表结构如表4.19所示

![](https://img-blog.csdnimg.cn/20200629163742666.png)

5.	普通用户信息表（user），用于存放用户信息，表结构如表4.20所示

![](https://img-blog.csdnimg.cn/202006291638194.png)

## 5 系统详细设计及实现

#### 5.1 添加航班信息

系统管理员登录后台系统后，点击侧边栏的航班信息管理按钮会出现下拉列表菜单，继续点击添加航班信息按钮可以进行添加航班信息操作。添加航班时输入航班号、起点、终点、始发机场、到达机场等信息，如下图所示。

![](https://img-blog.csdnimg.cn/20200630115259887.png)

添加航班信息的过程如下：后台系统管理员进入添加航班信息页面后，填写航班号、起点、终点、始发机场、到达机场等相关信息后点击保存按钮，这时会随机生成flightId并与数据库中已经存在的flightId进行比较，保证航班Id唯一，之后继续判断输入的机票价格，航班座位数等数据是否有效，核对信息的有效性和完整性，最后存入数据库。具体流程如下图所示。

![](https://img-blog.csdnimg.cn/20200630115402765.png)

**主要代码：**

```java
@RequestMapping("addFlight")
	public Result addFlight(@RequestBody Flight flight ) {
		//设置日期格式
		SimpleDateFormat df = new SimpleDateFormat("yyyyMMddHHmmss");
		// new Date()为获取当前系统时间
        flight.setFlightId("F"+df.format(new Date()));  
        try {
        	flightManageService.addFlight(flight);
        	return new Result(true,"添加成功");
		} catch (Exception e) {
			e.printStackTrace();
			return new Result(false,"添加失败");
		}
}
```

#### 5.2 航班信息列表

系统管理员登录系统后有查看航班列表的权限，航班列表界面有添加航班，删除航班，搜索航班信息，航班信息详情，航班信息修改等功能，具体见下图，各个功能详细说明如表5.1所示。

![](https://img-blog.csdnimg.cn/20200630115701888.png)

![](https://img-blog.csdnimg.cn/20200630115716774.png)

**主要代码这里以航班查询功能service层代码为例：**

```java
public PageResult search(int pageNum, int pageSize, String searchEntity) {
		PageHelper.startPage(pageNum,pageSize);
		List<Flight> flightsList=flightManageMapper.select(searchEntity);
		Page<Flight> page=(Page<Flight>) flightsList;
		return new PageResult(page.getTotal(), page.getResult());
	}
```

#### 5.3 订单信息列表

订单信息列表是订单信息管理模块的一个子功能，展示的是前台所有用户的机票订单信息，如下图所示。系统管理员可以对订单进行查询，删除操作，各个功能详细说明如表5.2所示。

![](https://img-blog.csdnimg.cn/20200630115908692.png)

![](https://img-blog.csdnimg.cn/20200630115924485.png)

**主要代码这里以订单删除功能dao层的mapper代码为例：**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd" >
<mapper namespace="com.cafuc.mapper.IOrderManageMapper">
  <delete id="delete" parameterType="String">
    delete from `order` where order_id in
    <foreach collection="selectIds" item="ids" open="(" close=")" separator=",">
      #{ids}
    </foreach>
  </delete>
</mapper>
```

#### 5.4 用户信息列表

用户信息列表是用户信息管理模块的子功能，它是指把前台系统所有注册用户信息以列表的形式展示给后台系统管理员，方便系统管理员精确定位到每一个机票预订系统的使用者，对其进行管理，用户信息列表的界面如下图所示。系统管理员有查找系统使用用户和删除违反平台规定用户的权利，各个功能详细说明如表5.3所示。

![](https://img-blog.csdnimg.cn/20200630120106975.png)

![](https://img-blog.csdnimg.cn/20200630120121891.png)

**主要代码以用户搜索功能dao层的mapper代码为例：**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd" >
<mapper namespace="com.cafuc.mapper.IUserManageMapper">
  <select id="select" resultType="com.cafuc.pojo.User">
     select DISTINCT * from `user` as u where 
		u.user_name like concat('%',#{searchEntity},'%')
  </select>
</mapper>
```

#### 5.5 留言评论列表

留言评论是前台系统使用者完成注册后具有的功能，用户可以通过留言评论功能对所购班次机票进行全方位的评价，也可以对其在使用过程中遇到的问题进行反馈，等待工作员处理。后台系统管理员对用户留言具有管理的权限，见下图。各功能详情见表5.4。

![](https://img-blog.csdnimg.cn/20200630120330548.png)

![](https://img-blog.csdnimg.cn/20200630120346388.png)

**主要代码以后台系统留言评论模块controller层DiscussManageController.java类为例：**

```java
package com.cafuc.controller;
import javax.annotation.Resource;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;
import com.cafuc.pojo.PageResult;
import com.cafuc.pojo.Result;
import com.cafuc.service.IDiscussManageService;
import com.cafuc.service.IOrderManageService;

@RestController
@RequestMapping("discussManage")
public class DiscussManageController {
	@Resource
	private IDiscussManageService discussManageService;
	@RequestMapping("search")
	public PageResult search(int pageNum ,int pageSize,String searchEntity){
		System.out.println(pageNum+" "+pageSize+" "+searchEntity);
		PageResult pageResult=discussManageService.search(pageNum, pageSize, searchEntity);
		return pageResult;
	}
	@RequestMapping("deleteBySelectIds")
	public Result deleteBySelectIds(String []selectIds) {
        try {
        	discussManageService.deleteBySelectIds(selectIds);
        	return new Result(true,"删除成功");
		} catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
			return new Result(false,"删除失败");
		}
	}
}
```

#### 5.6 添加广告信息

广告作为网站的必要元素，在机票系统的前台页面也有广告展示的功能，后台增加了相应的管理模块，界面如下图所示。

![](https://img-blog.csdnimg.cn/20200630120539668.png)

后台系统添加广告的步骤：管理员登录后台系统后点击广告管理按钮，在出现的下拉列表选项中选择添加广告信息并点击进入广告添加页面，在页面输入广告图片、广告链接，广告说明等信息，点击保存按钮，进行数据校验，检查数据的有效性和完整性，保证数据无误之后将数据信息持久化到mysql数据库。流程图如下图所示。

![](https://img-blog.csdnimg.cn/20200630120617957.png)

**主要代码以后台系统controller层ContentManageController.java类为例：**

```java
@RequestMapping("addContent")
	public void addContent(@RequestParam("file") MultipartFile file,HttpServletRequest request,HttpServletResponse response) 
	throws IOException {
		String describe="";
		String url="";
		String picture="";
		if(request.getParameter("describe")!=null) {
			describe=request.getParameter("describe");
		}
		if(request.getParameter("url")!=null) {
			url=request.getParameter("url");
		}
		// 判断文件是否为空，空则返回失败页面
		if (!file.isEmpty()) {
			try {
				// 获取文件存储路径（绝对路径）
				String path = request.getServletContext().getRealPath("/WEB-INF/file");
				// 获取原文件名
				String fileName = file.getOriginalFilename();
				// 创建文件实例
				File filePath = new File(path, fileName);
				// 如果文件目录不存在，创建目录
				if (!filePath.getParentFile().exists()) {
					filePath.getParentFile().mkdirs();
					System.out.println("创建目录" + filePath);
				}
				picture=filePath+"";
				// 写入文件
				file.transferTo(filePath);
				Content content=new Content();
				//设置日期格式
				SimpleDateFormat df = new SimpleDateFormat("yyyyMMddHHmmss");
				// new Date()为获取当前系统时间
				content.setContentId("C"+df.format(new Date()));
				content.setDescribe(describe);
				content.setPicture(picture);
				content.setUrl(url);
			    contentManageServiceImpl.addContent(content);
			    response.sendRedirect(request.getContextPath()+"/admin/list_content.html");
			} catch (Exception e) {
				e.printStackTrace();
				response.sendRedirect(request.getContextPath()+"/admin/add_content.html");
			}
		}
		else {
			response.sendRedirect(request.getContextPath()+"/admin/add_content.html");
		}
		
	}
```

#### 5.7 广告信息列表

后台系统管理员完成添加广告以后跳转到广告信息列表页面，本页面展示的是添加到数据库的所有广告信息，如下图所示，系统管理员可以通过查询，删除等操作来管理广告信息，详情见表5.5。

![](https://img-blog.csdnimg.cn/20200630120807856.png)

![](https://img-blog.csdnimg.cn/20200630120829741.png)

#### 5.8 查看个人信息

后台系统管理员可以查看个人的用户名，密码，邮箱，手机号等信息，由于时间有限，这里实现了查看用户名，密码等功能，见下图所示。

![](https://img-blog.csdnimg.cn/20200630121049702.png)

由于系统管理员在登陆系统后把个人信息存到redis数据库中，在页面初始化时从redis数据库中查找出个人信息存到cookie中，查看个人信息就是从cookie中提取数据并设置到页面中，具体代码如下：

```javascript
//初始化
$scope.adminEntity={};
$scope.init=function () {
	console.log($.cookie('key'));
	adminManageService.init($.cookie('key')).success(function (res) {
	      console.log(res) 
	      $scope.adminEntity=res;
	    });
}
```

#### 5.9 修改个人信息

后台系统管理员也对用户名，密码，邮箱，手机号等信息进行修改，点击个人信息修改按钮进入页面修改个人信息，修改后点击保存等检查填写的信息无误后提示完成修改，为了确保用户名字段的唯一性，用户名一项无法修改。主要代码以controller层为例:

```java
@RequestMapping("editAdmin")
	public Result editAdmin(@RequestBody AdminUser adminUser){
		
		try {
			adminManageServiceImpl.editAdmin(adminUser);
			redisTemplate.boundValueOps(adminUser.getUser()).set(adminUser);
			return new Result(true, "修改成功");
		} catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
			return new Result(false, "修改失败");
		}
	}
```

#### 5.10 用户登录

用户在进行机票预定，留言评论等功能时需要登录前台系统后才能进行，在浏览器地址栏输入 http://localhost:8081/flyTicket-portal-web/default/login.html 回车进入如下图所示界面。

![](https://img-blog.csdnimg.cn/20200630121327613.png)

用户进行到登录界面，输入正确的用户名和密码就可以登录到前台系统，登录顺序图如下图所示。

![](https://img-blog.csdnimg.cn/20200630121401198.png)

**主要代码以controller层代码为例：**

```java
app.controller('portalLoginManageController',function($scope,$controller,portalLoginManageService){
	$controller('baseController',{$scope:$scope});
	//初始化
	 $scope.userEntity={userName:null,userPwd:null};
	 $scope.login=function(){
		 if($scope.userEntity.userName==null || $scope.userEntity.userName.trim()==""){
			 alert("用户名为空");
		 }
		 else{
			 if($scope.userEntity.userPwd==null || $scope.userEntity.userPwd.trim()==""){
				 alert("密码为空");
			 }
			 else{			 portalLoginManageService.login($scope.userEntity).success(function(res){
					 if(res.result==false){
						 alert(res.message)
					 }
					 else{
						 window.location.href="index.html#?key="+$scope.userEntity.userName; 
					 }
				 }); 
			 }
		 };
	 }
});
```

#### 5.11 航班信息展示

在浏览器地址栏输入 http://localhost:8081/flyTicket-portal-web/default/index.html 出现如下图所示界面，首页面展示所有航班信息。每一条信息包含出发城市、到达城市、出发机场、到达机场，出发时间、到达时间、机票价格等信息。

![](https://img-blog.csdnimg.cn/20200630121525490.png)

#### 5.12 航班信息查询
用户可以通过航班查询功能精确查找到所需信息，节省时间简化操作。通过输入航班类型、出发时间、出发城市、到达城市等搜索条件实现航班查询。以成都为到达城市为例，搜索结果如下图所示。

![](https://img-blog.csdnimg.cn/20200630121619347.png)

**代码以dao层PortalManageMapper.xml类例：**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd" >
<mapper namespace="com.cafuc.mapper.IPortalManageMapper">
  <select id="select" resultType="com.cafuc.pojo.Flight">
     select * from flight as f 
      <where>
        <if test="flightStartTime1 !=null and flightStartTime1 !=''">
          and f.flight_start_time like concat('%',#{flightStartTime1},'%')
        </if>
        <if test="flightStartPlace !=null and flightStartPlace !=''">
          and f.flight_start_place like concat('%',#{flightStartPlace},'%')
        </if>
        <if test="flightEndPlace !=null and flightEndPlace !=''">
          and f.flight_end_place like concat('%',#{flightEndPlace},'%')
        </if>
     </where>
  </select>
</mapper>
```

#### 5.13 航班信息详情

航班信息详情是对某一航班信息的详细情况进行展示，如下图所示。用户点击选定航班，航班详细信息以下拉列表的形式展现给用户。

![](https://img-blog.csdnimg.cn/20200630121759179.png)

**主要代码如下：**

```javascript
//保留n位小数
	$scope.weishu=function(price,n){
		return new Number(price).toFixed(n);
	}
	//下拉详情
	$scope.lists=function(flightNumber){
		//收缩状态
		if($("#F_"+flightNumber).is(":visible")){
			$scope.reloadList();
		}
		$("#F_"+flightNumber).animate({
		      height:'toggle'
		    });
	}
	//判断最低价
	$scope.minPrice=function(flightHighPrice,flightMiddlePrice,flightBasePrice){
		return (flightHighPrice<=flightMiddlePrice?flightHighPrice:flightMiddlePrice)<=flightBasePrice?(flightHighPrice<=flightMiddlePrice?flightHighPrice:flightMiddlePrice):flightBasePrice
	}
	//判断是否有票
	$scope.isKickets=function(kicketsNumber,flightNumber,temp){
		/*console.log(flightNumber)*/
		if(kicketsNumber>0){
			$("#"+temp+"_"+flightNumber).css({
				color:"green"
			});
			return "有票";
		}
		else{
			$("#"+temp+"_"+flightNumber).css({
				color:"red"
			});
			return "无票";
		}
	}
```

#### 5.14 登录用户信息展示

游客访问前台系统时，在页面头部显示“请登录”字样，如下图所示信息，而网站用户登录后则显示“您好，XXX”字样，如下图所示。

![](https://img-blog.csdnimg.cn/20200630121938901.png)

![](https://img-blog.csdnimg.cn/20200630121950414.png)

#### 5.15 留言板

点击前台系统右上角“留言板”按钮进入到留言页面如下图所示。留言评论是前台系统使用者完成注册后具有的功能，用户可以通过留言评论功能对所购班次机票进行全方位的评价，也可以对其在使用过程中遇到的问题进行反馈。

![](https://img-blog.csdnimg.cn/20200630122050950.png)

**主要代码以前台系统controller层DiscussManageController.java类例：**

```java
package com.cafuc.controller;
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.List;
import javax.annotation.Resource;
import org.apache.commons.collections.FastArrayList;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.data.redis.core.RedisTemplate;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;
import com.cafuc.pojo.Discuss;
import com.cafuc.pojo.Flight;
import com.cafuc.pojo.PageResult;
import com.cafuc.pojo.Result;
import com.cafuc.service.IDiscussManageService;
import com.cafuc.service.IPortalManageService;
@RestController
@RequestMapping("discussManage")
public class DiscussManageController {
	@Resource
	private IDiscussManageService discussManageService;
	@RequestMapping("addDiscuss")
	public Result addDiscuss(@RequestBody Discuss discuss){
		try {
			System.out.println(discuss);
			discussManageService.addDiscuss(discuss);
			return new Result(true, "评论成功");
		} catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
			return new Result(false, "评论失败");
		}
	}
	@RequestMapping("init")
	public List<Discuss> init(){
		return discussManageService.init();
	}
}
```

#### 5.16 订单填写
订单填写是机票预定中不可缺少的步骤之一，用户找到自己所需班次后点击订票按钮进入订单信息填写页面，用户所填写的信息包括乘机人信息和联系人信息量大模块，如下图所示。填写完信息后点击提交订单按钮，等待验证数据的有效性，确定填写无误后完成提交，填写订单的前提是用户已经登录系统。

![](https://img-blog.csdnimg.cn/20200630122238229.png)

#### 5.17 订单详情

填写订单信息完成订单提交后弹出订单详情页面提示用户检查航班信息和填写的用户信息，如下图所示。确保信息无误后点击确认付款按钮跳转到订单支付页面。

![](https://img-blog.csdnimg.cn/20200630122336837.png)

**订单确认功能主要代码如下：**

```java
@RequestMapping("/ack")
	public void ack(Order order,HttpServletRequest request,HttpServletResponse response) throws IOException {
		try {
			if(order.getOrderDate() ==null) {
				order.setOrderDate(new Date());
			}
			HttpSession httpSession=request.getSession();
			httpSession.setAttribute("order", order);
			System.out.println(request.getSession().getAttribute("order"));
			response.sendRedirect(request.getContextPath()+"/pay/index.jsp");
		} catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
		}
	}
```

#### 5.18 订单支付

机票预订系统的订单支付功能使用的是支付宝沙箱环境支付，蚂蚁沙箱环境 (Beta) 是协助开发者进行接口功能开发及主要功能联调的辅助环境。登录支付宝沙箱平台依次完成生成买家和卖家账号信息、生成RSA秘钥、设置公钥信息、设置应用网关等应用环境配置。完成配置后下载官方测试代码，本系统选择的是电脑应用java版本，然后将下载的项目导入到eclipse工作空间。最后设置核心配置文件信息，打开flyTicket-portal-web项目下com.alipay.config包中的AlipayConfig.java文件配置如下信息：


```java
//沙箱APPID
public static final  String app_id = "**这里需要自己申请**";
//沙箱私钥
public static final  String merchant_private_key = "**这里需要自己申请**";
//支付宝公钥
public static final  String alipay_public_key = "**这里需要自己申请**";
//沙箱网关地址
public static final  String gatewayUrl = "https://openapi.alipaydev.com/gateway.do";

//服务器异步通知页面路径  需http://格式的完整路径，不能加?id=123这类自定义参数，必须外网可以正常访问
public static String notify_url = "http://localhost:8081/flyTicket-portal-web/pay/notify_url.jsp";

//页面跳转同步通知页面路径 需http://格式的完整路径，不能加?id=123这类自定义参数，必须外网可以正常访问
public static String return_url = "http://localhost:8081/flyTicket-portal-web/orderManage/complete";
```

完成以上配置后就可以实现订单支付功能了。点击确认付款后跳转到如下图所示界面。

![](https://img-blog.csdnimg.cn/20200630122830766.png)

点击付款按钮后如下图所示，可以登录账户付款，也可以使用手机端沙箱支付宝完成付款。

![](https://img-blog.csdnimg.cn/20200630122908819.png)

完成付款后如下图所示

![](https://img-blog.csdnimg.cn/20200630122941862.png)

**主要代码如下：**

```java
//支付完成后
@RequestMapping("complete")
public void complete(HttpServletRequest request,HttpServletResponse response) throws IOException {
	System.out.println(request.getSession().getAttribute("order"));
	Order order=(Order)request.getSession().getAttribute("order");
	try {
		//将数据插入到订单表中
		orderManageService.insertOrder(order);
		//更改库存
		Flight flight=orderManageService.findOneByFlightNumber(order.getFlightNumber());
		if(order.getGrade().equals("f")) {
			flight.setFlightHighNumber(flight.getFlightHighNumber()-1);
		}
		else if(order.getGrade().equals("b")) {
			flight.setFlightMiddleNumber(flight.getFlightMiddleNumber()-1);
		}
		else {
			flight.setFlightBaseNumber(flight.getFlightBaseNumber()-1);
		}
		orderManageService.updatesNum(flight);
		} catch (Exception e) {
			e.printStackTrace();
		}
		response.sendRedirect(request.getContextPath()+"/default/index.html");
	}
```

## 6 源码下载

获取完整源码请在公众号：【IT学长】回复“基于web的机票管理系统”或者“机票管理系统”

## 7 运行教程

详细运行步骤及常见问题解答请看“基于Web的机票预订系统”源码包中 README.md 文件。

通过第6步下载源码包并解压后如下图所示：

![](https://img-blog.csdnimg.cn/a295aa678fc348fb8f4b827e0ad08fc7.png)

## 8 相关说明

 1. 制作不易，记得点赞+收藏+转发
 3. 本人技术有限，若有错误欢迎指正
 4. 本系统和文章均属于【IT学长】原创，转载请注明出处

