# konwledge 
好好积累，基础决定上层建筑
### Django基础知识点
   #### 一、搭建虚拟环境virtualenv：
		第一步：安装：pip install virtualenv：
		参数：virtualenv 中的参数
			-p： 指定安装在虚拟环境中的python版本，如果不指定则虚拟环境中安装的python版本为环境变量中设置的python版本
			--no-site-packages：指定虚拟环境中没有安装任何的包
		第二步：使用python3创建虚拟环境：
		
		创建指令：virtualenv -p  python3安装路径\python.exe  --no-site-packages 虚拟环境文件名称 
		使用python3自带的安装虚拟环境
			创建：python -m venv name
		第三步：激活虚拟环境/退出虚拟环境：
			激活虚拟环境
			windows：直接执行activate.bat （进入虚拟环境）
			mac/linux：source  activate
			退出虚拟环境：
			windows：直接执行deactivate.bat
			mac/linux：deactivate  （退出虚拟环境）
		第四步：安装Django：
			安装：pip install django==1.11
			查询django有哪些版本：pip install django==1.11.11111111 （故意将其版本号打错，就会提示Django的所有版本）

		第五步：创建一个完整的项目
			创建工程目录（前提是在虚拟环境下创建）：django-admin startproject day01   
				对工程目录结构下的py文件进行配置：
				__init__.py
					配置数据库的驱动：pymysql.install_as_mysqldb()
				urls.py
					根路由地址，管理URL匹配规则
					添加应用app的路径到工程目录下（就是与项目名相同的文件）的url中：
					这里的应用app可以根据自己需要进行更改名字，如：user，house，goods，cars等都可以的。
					url(r'^/app',include('app.urls',namespace='app'))
				settings.py （很重要的文件夹）
				配置的地方：
					1. DEBUG模式：DEBUG=True
					2. 数据库DATABASES：（六点）
					ENGINE：修改为mysql，
					USER：用户名，
					PASSWORD：密码，
					NAME：数据库名，
					HOST:ip地址，
					PORT：端口（如：3306）
					3. INSTALLED_APPS:添加自己创建的应用app后面，以同样的格式。
					4. MIDDLEWARE =[ ] 添加中间件的位置
					5. TEMPLATES=[{'DIRS':[os.path.join(BASE_DIR,'templates')], }} 设置解析模板的路径。
					6. 设置时区：Asia/Shanghai
					7. 设置中文：zh-hans
					8. 设置静态资源static，static中一般存放的文件有css，js，image。
		第六步：创建应用app：
				创建指令：python manage.py  startapp  app_name
				注意：一定要在自己建虚拟环境下建立应用app_name
			    应用目录结构
				__init__.py
				models.py
					模型的设计很重要，
					定义模型：
					字段类型：IntegerFiled，CharFiled。
					参数：default，max_length
					定义模型映射到数据库中的表名: db_table='student'
						如果不指定db_table参数，则在迁移后，数据库中的表名为appname_模型名(小写)
				views.py
					写业务逻辑 （写方法，写功能模块）
				admin.py
					注册模型: adinn.site.register(模型)
				tests.py
					测试接口文件
		第七步：数据迁移：
			生成迁移文件:python manage.py makemigrations
				如果models.py中模型没有任何改动，是提示'no change xxx'
				如果modes.py中模型改动了，但是还是提示'no change xxx'，则修改迁移命令强制迁移：python manage.py makemigrations app_name
				如果还不行，那就去数据库里删除记录，再重新迁移数据，但是一般不这样，学习的时候可以。
			执行迁移:python manage.py migrate
				在django_migrations表中存迁移文件信息，若要重新迁入数据库有时会不成功，可以将其中相应的记录删除后再试试。
		管理后台：
		创建超级用户
			命令：python manage.py createsuperuser
			数据存在auth_user表中
在admin.py中注册模型：admin.site.register(模型名)
