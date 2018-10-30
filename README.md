＃日志
好好积累，基础决定上层建筑
		组件：loggers, handlers, filters, formatters
		错误级别:critical>error>waring>info>debug
		获取logger：logger = loggins.getLoggers(__name__)
		打印普通日志logger.info()
		打印错误日志：logger.error()
		打印巨大的错误日志：logger.critical()
		打印调试日志: logger.debug()
	rest_framework
		安装： pip install djangorestframework
		配置：在settings.py中的INSTALLED_APPS中添加rest_framework
		在应用app的urls.py中定义SimpleRouter()的路由
		导入mixins, viewsets： ListModelMixin/CreateModelMixin/DestroyModelMixin.....
		定义queryset,所有数据 serializer_class序列化
		过滤:定义filter_class
		分页

###怎么建立一个连接在这里
