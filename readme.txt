这是学习了javabean后的第一个开发
模块一：
技术：  Ajax+javabean+mysql数据库相关操作
用户注册，用户登录，用户修改信息
用户注册模块：
	
	首先有个败笔的地方，数据库中的T表示注册时间没有用TimeStamp对象。

	用Ajax实现异步请求和刷新，（主要用于 用户名是否已经注册过）
	用User类（javabean类)进行持久化，
	用SqlManager类操作数据库，
	用JGraph组件完成有关验证码图片的生成，
	用JMail组件完成注册成功后邮件验证的发送。

	其中SqlManager类有   根据用户名查找信息的功能，添加用户信息到数据库的功能.
		将SqlManager类设计成单例模式，只允许有一个SqlManager对象操作数据库
		要想连接到数据库，需要读取动态的配置参数，有驱动程序和连接字。
		导入mysql-connector-java.jar包
		
	User类是持久化类，是一个Javabean类
	测试User类和SqlManager类成功后，
	先编写Register.jsp文件和Register_Handle.jsp文件。
	用pageContext.forward()和scope="request"实现两个界面用同一个javabean(User对象)
	
	用Ajax编写异步检测，查看用户名是否已经注册过， 注意在JSP页面引入JS文件，出现乱码问题，将《%@page 中的charset设为utf-8%》同时<script charset="utf-8"></script>
	用JS编写 格式检测 规整email和tel的格式。
	在Register.js中判断xmlHttp.reponseText的值是否和预定值相等用来输出结果时，相当痛苦，总是判断false，无论有数据库中有没有name，User类和R_H.jsp处理的成功，但是JS文件中就是不能
	成功，不是逻辑的问题，只是js文件中响应的数据怎么和数字或字符串进行对比的问题。明明输出的结果一样但就是不相等。
	
	原因：你用alert输出reponseText可以看见响应有html的标签，所以要进行处理。原来是我返回错误，因为R_H.jsp页面有html标签，会返回。
	
	在编写JMail类时，抛出错误
	javax.mail.MessagingException: Could not connect to SMTP host: localhost, port: 25, response: -1
	at com.sun.mail.smtp.SMTPTransport.openServer(SMTPTransport.java:1270)
	at com.sun.mail.smtp.SMTPTransport.protocolConnect(SMTPTransport.java:370)
	at javax.mail.Service.connect(Service.java:275)
	at javax.mail.Service.connect(Service.java:156)
	at util.JMail.sendMail(JMail.java:98)
	at util.JMail.main(JMail.java:114)

	不知道为什么前几天好好的hmailserver邮件服务器 ，又不会连接了。
	暂时先将 JMail模块放一放 JGraph模块也放一放
	
登录模块：
	
	首先有登录界面， 姓名，密码，验证码（先略去）
	登录处理界面，根据姓名查找密码，是否一致，  (额，由于我比较省事，用了之前的数据库，所以竟然没有密码字段，额只能将邮件，当做密码了）
	
	在做到某个点的时候，发现User中的getName方法操作后得不到 ResultSet的结果，
	原因是因为  sql语句中的 String sql="select * from user where name=' 空格" + name +" 空格 '";中有空格，即SQL操作语句有错误，注意
	
	超委屈的一个错误，因为usebean 中的class的值没有用双引号引起来，而且查了大半天。
	编写了一个OnlineUser类，用于显示在线人数,很遗憾没有排除相同的用户不断的登录的问题。
	用session显示当前用户，当用不同的浏览器打开时，有不同的session.
	
修改用户信息模块：

	首先在登录模块处有个链接，然后登录修改页面，这里也用到了  Ajax异步处理，填写完姓名后，检查是否在线，是否和Session中的对象一致，一致了才让修改，不一致无权修改
	我发现当 submit按钮时不显示的时候，无法进行页面的提交，这省了我很多的代码想法
	
结尾：数据库中存入 汉字会出现乱码的情况，每次后台都会打印出 连接数据库和关闭数据库的信息， 如果某用户登上后，数据库就打开知道某用户离开数据库才关闭，这样好么？？