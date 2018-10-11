以下情况@Transactional事务会失效。
1.首先检查配置，在项目的spring配置文件检查是否配置开启事务
2.同一个类中, 一个未标注@Transactional的方法去调用标有@Transactional的方法, 事务会失效
3. 在非public方法上标注@Transactional, 事务无效