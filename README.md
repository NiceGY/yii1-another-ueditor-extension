yii1-another-ueditor-extension
==============================

这只是一个yii1的百度编辑器ueditor扩展,因为别人做过一个类似的扩展了，所以我只好叫another

###ueditor版本：1.4.3

目录结构
------
baiduUeditor       
|--resource //ueditor资源包     
|--views  //widget的视图    
|--config.php //后端配置文件 包括文件格式 大小 目录 路径 文件名等等
|--UeditorController.php  //后端主控制器  可以修改继承类为自定义的基类   
|--UeditorWidget.php    //widget主要渲染编辑器  
|--Uploader.class.php   //上传等主要处理类  

使用
------

1. 将*baiduUeditor*拷贝到*protected/extensions/*目录下
2. 添加以下代码到*config/main.php*

	```
	'controllerMap'=>array(
	        'ueditor'=>array(
	            'class'=>'ext.baiduUeditor.UeditorController',
	        ),
	    ),

	```

	如果你想只在某个module里使用，请添加以下代码到*modules/moduleName/moduleNameModule.php*

	```
	$this->controllerMap=array(

	            'ueditor'=>array(
	                'class'=>'ext.baiduUeditor.UeditorController',
	            ),

	        );

	```

3. 在要显示编辑器的view中放置如下代码
```
<?php
    $this->widget('ext.baiduUeditor.UeditorWidget',
        array(
            'id'=>'article_content',//容器的id 唯一的[必须配置]
            'name'=>'content',//post到后台接收的name [必须配置]
            'content'=>'',//初始化内容 [可选的]
            
            //配置选项，[可选的]
            //将ueditor的配置项以数组键值对的方式传入,具体查看ueditor.config.js
            //不要配置serverUrl(即使配置也会被覆盖)程序会自动处理后端url
            'config'=>array(
                'toolbars'=>array(array('fullscreen', 'source', '|')),//toolbars注意是嵌套两个数组
                'lang'=>'en'
            )
        )
    );
?>
```

提问题
-------
[戳这里](https://github.com/mojifan/yii1-another-ueditor-extension/issues 'issue')



