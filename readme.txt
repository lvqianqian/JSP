����ѧϰ��javabean��ĵ�һ������
ģ��һ��
������  Ajax+javabean+mysql���ݿ���ز���
�û�ע�ᣬ�û���¼���û��޸���Ϣ
�û�ע��ģ�飺
	
	�����и��ܱʵĵط������ݿ��е�T��ʾע��ʱ��û����TimeStamp����

	��Ajaxʵ���첽�����ˢ�£�����Ҫ���� �û����Ƿ��Ѿ�ע�����
	��User�ࣨjavabean��)���г־û���
	��SqlManager��������ݿ⣬
	��JGraph�������й���֤��ͼƬ�����ɣ�
	��JMail������ע��ɹ����ʼ���֤�ķ��͡�

	����SqlManager����   �����û���������Ϣ�Ĺ��ܣ�����û���Ϣ�����ݿ�Ĺ���.
		��SqlManager����Ƴɵ���ģʽ��ֻ������һ��SqlManager����������ݿ�
		Ҫ�����ӵ����ݿ⣬��Ҫ��ȡ��̬�����ò���������������������֡�
		����mysql-connector-java.jar��
		
	User���ǳ־û��࣬��һ��Javabean��
	����User���SqlManager��ɹ���
	�ȱ�дRegister.jsp�ļ���Register_Handle.jsp�ļ���
	��pageContext.forward()��scope="request"ʵ������������ͬһ��javabean(User����)
	
	��Ajax��д�첽��⣬�鿴�û����Ƿ��Ѿ�ע����� ע����JSPҳ������JS�ļ��������������⣬����%@page �е�charset��Ϊutf-8%��ͬʱ<script charset="utf-8"></script>
	��JS��д ��ʽ��� ����email��tel�ĸ�ʽ��
	��Register.js���ж�xmlHttp.reponseText��ֵ�Ƿ��Ԥ��ֵ�������������ʱ���൱ʹ�࣬�����ж�false�����������ݿ�����û��name��User���R_H.jsp����ĳɹ�������JS�ļ��о��ǲ���
	�ɹ��������߼������⣬ֻ��js�ļ�����Ӧ��������ô�����ֻ��ַ������жԱȵ����⡣��������Ľ��һ�������ǲ���ȡ�
	
	ԭ������alert���reponseText���Կ�����Ӧ��html�ı�ǩ������Ҫ���д���ԭ�����ҷ��ش�����ΪR_H.jspҳ����html��ǩ���᷵�ء�
	
	�ڱ�дJMail��ʱ���׳�����
	javax.mail.MessagingException: Could not connect to SMTP host: localhost, port: 25, response: -1
	at com.sun.mail.smtp.SMTPTransport.openServer(SMTPTransport.java:1270)
	at com.sun.mail.smtp.SMTPTransport.protocolConnect(SMTPTransport.java:370)
	at javax.mail.Service.connect(Service.java:275)
	at javax.mail.Service.connect(Service.java:156)
	at util.JMail.sendMail(JMail.java:98)
	at util.JMail.main(JMail.java:114)

	��֪��Ϊʲôǰ����úõ�hmailserver�ʼ������� ���ֲ��������ˡ�
	��ʱ�Ƚ� JMailģ���һ�� JGraphģ��Ҳ��һ��
	
��¼ģ�飺
	
	�����е�¼���棬 ���������룬��֤�루����ȥ��
	��¼������棬���������������룬�Ƿ�һ�£�  (������ұȽ�ʡ�£�����֮ǰ�����ݿ⣬���Ծ�Ȼû�������ֶΣ���ֻ�ܽ��ʼ������������ˣ�
	
	������ĳ�����ʱ�򣬷���User�е�getName����������ò��� ResultSet�Ľ����
	ԭ������Ϊ  sql����е� String sql="select * from user where name=' �ո�" + name +" �ո� '";���пո񣬼�SQL��������д���ע��
	
	��ί����һ��������Ϊusebean �е�class��ֵû����˫���������������Ҳ��˴���졣
	��д��һ��OnlineUser�࣬������ʾ��������,���ź�û���ų���ͬ���û����ϵĵ�¼�����⡣
	��session��ʾ��ǰ�û������ò�ͬ���������ʱ���в�ͬ��session.
	
�޸��û���Ϣģ�飺

	�����ڵ�¼ģ�鴦�и����ӣ�Ȼ���¼�޸�ҳ�棬����Ҳ�õ���  Ajax�첽������д�������󣬼���Ƿ����ߣ��Ƿ��Session�еĶ���һ�£�һ���˲����޸ģ���һ����Ȩ�޸�
	�ҷ��ֵ� submit��ťʱ����ʾ��ʱ���޷�����ҳ����ύ����ʡ���Һܶ�Ĵ����뷨
	
��β�����ݿ��д��� ���ֻ��������������ÿ�κ�̨�����ӡ�� �������ݿ�͹ر����ݿ����Ϣ�� ���ĳ�û����Ϻ����ݿ�ʹ�֪��ĳ�û��뿪���ݿ�Źرգ�������ô����