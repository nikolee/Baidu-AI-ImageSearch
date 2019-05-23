# Baidu-AI-ImageSearch

1. 下载php SDK压缩包 http://ai.baidu.com/download?sdkId=64  
1. 将下载的aip-php-sdk-version.zip解压后，复制AipImageSearch.php以及lib/* 到工程文件夹中  
1. 新建AipImageSearch  

		<?php
		date_default_timezone_set('Asia/Singapore');
		require_once __DIR__.'/AipImageSearch.php';

		const APP_ID = '<app_id>';
		const API_KEY = '<api_key>';
		const SECRET_KEY = '<secret_key>';

		$client = new AipImageSearch(APP_ID, API_KEY, SECRET_KEY);
		?>
1. 相似图检索—入库  

		// 调用相似图检索—入库, 图片参数为本地图片
		$image = file_get_contents('example.jpg');

		// 调用相似图检索—入库, 图片参数为远程url图片
		$url = "http//www.x.com/sample.jpg";

		// 如果有可选参数
		$options = array();
		$options["brief"] = "{\"name\":\"周杰伦\", \"id\":\"666\"}";
		$options["tags"] = "100,11";

		// 带参数调用相似图检索—入库, 图片参数为本地图片
		$client->similarAdd($image, $options);

		// 带参数调用相似图检索—入库, 图片参数为远程url图片
		$client->similarAddUrl($url, $options);
1. 相似图检索—入库 返回数据参数详情

|字段|是否必选|类型|说明|
|-|-|-|-|
|log_id|是|uint64|唯一的log id，用于问题定位|
|cont_sign|是|string|输入图片签名，可用于删除|

返回示例：

		{
			"log_id": 2263663554,
			"cont_sign": "4261577168,501945506"
		}
