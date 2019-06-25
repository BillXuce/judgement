#法律数据集

###文件组成
**data_train.json**: 25w 
**data_valid.json**: 10W 
**data_test.json**: 7.5k  

###数据组成
数据中涉及 **183个法条**、**202个罪名**，均为刑事案件  

###数据清洗
数据中筛除了刑法中前101条(前101条并不涉及罪名)，并且为了方便进行模型训练，将罪名和法条数量少于30的类删去。

###数据格式
数据利用csv格式储存，每一行为一条数据，每条数据均为一个字典
#####字段及意义
* **ids**: 案件编号  
* **fact**: 事实描述
* **criminals**：嫌疑人  
* **accusation**: 罪名  
* **articles**: 相关法条  

