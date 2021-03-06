quickbundle骨架工程
================================================
目前包含：JavaEE标准版、跨平台的Mobile端phonegap版<br/>

quickbundle-rmwebdemo
------------------------------------------------
### 特性
* JavaEE 2.5项目骨架，Maven规范
* 主框架是jQuery-1.9 + Html4 + Spring MVC 3.2 + Spring 3.2 + MyBatis 3.2
* 集成了Jackson-2.1(Json) + Apache CXF-2.5(web service) + JFreeChart-1.0(图表) + JasperReport-4.7(报表) + mail-1.4(邮件) + jxl-2.6(Excel) + dom4j-1.6(xml) + slf4j-1.7(日志) + jython-2.7(Python运行库)
* 内置组织权限(设计思想源自Martin Fowler的《分析模式》) + 分布式调度(基于quartz-2.1增强了管理界面) + 编码数据管理 + 附件管理 + 业务日志 + 业务锁
* 待增加：Activiti-5.13(工作流引擎，增强了组织适配器、流程管理器等) + MuleESB-3.4(ESB企业服务总线) + Drools-6.0(规则引擎)

适用场景：企业应用、互联网应用后端。

### 一键编译quickbundle-4.0.0插件的方式（推荐）？
eclipse/plugins目录格式，直接复制到Eclipse下，安装快

		1，确保qb-core/eclipse-plugin/quickbundle-gp/t/j1下删掉了软链接目录quickbundle-rmwebdemo
		2，先安装qb-core到$M2_REPO。
			cd qb-core/
			mvn install -o 【-o表示离线模式，不用每次都检查tycho库。首次执行要去掉-o】
		3，打包。
			cd qb-archetype/build/build-rmwebdemo
			mvn clean package
		4，安装插件包。
			复制qb-archetype/build/build-rmwebdemo/target/eclipse目录到$ECLIPSE_HOME/links/org.quickbundle目录
		5，重启Eclipse即可

		
quickbundle-phonegapdemo
------------------------------------------------
### 特性
* mobile appliation archetype, corporate with java-archetype backend server<br/>
* 提供一个跨平台移动终端方案，一套代码支持iOS、Android、Windows Phone等移动平台
* 主框架是PhoneGap-2.0 + jQuery-1.5 + jQuery Mobile-1.0 + jQuery JSONP-2.4 + Html5

适用场景：要求跨平台的移动端接入。

### 如何一键编译phonegap：
		1，打开~/.m2/settings.xml，加入配置：
			<servers>
				<server>
					<id>phonegap-build</id>
					<username>yourmail@gmail.com</username>
					<password>yourpassword******</password> 
				</server>
			</servers>
		............
			<profiles>
				<profile>
					<id>dev</id>
					<properties>
						<phonegap-build.server>phonegap-build</phonegap-build.server>
					</properties>
		......
		2，免费build.phonegap.com帐号只能上传一个private app，因此执行mvn phonegap-build:scorch清理掉已存在的private app（谨慎操作）
		3，cd /quickbundle-phonegapdemo> mvn clean install -Dmaven.test.skip=true
		4，apk、xap等文件，在$M2_REPO/org/quickbundle/quickbundle-phonegapdemo/4.0.0

