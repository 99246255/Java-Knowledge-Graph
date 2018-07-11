1,资源收集
http://orchome.com/kafka/index

http://cwiki.apachecn.org/display/Kafka/   中文


https://blog.gmem.cc/apache-kafka-study-note


// official  https://kafka.apache.org/documentation/

vs rabbitMQ https://content.pivotal.io/blog/understanding-when-to-use-rabbitmq-or-apache-kafka

//kafka入门：简介、使用场景、设计原理、主要配置及集群搭建

http://www.cnblogs.com/likehua/p/3999538.html

//kafka 深度解析

http://www.jasongj.com/2015/01/02/Kafka深度解析/

//stream API

https://docs.confluent.io/current/streams/

//Ben

https://www.confluent.io/blog/author/ben/

//kafka connect

http://sparkgis.com/java/2017/10/kafka-connect%E4%BB%8B%E7%BB%8D%E3%80%81%E9%83%A8%E7%BD%B2%E5%8F%8A%E5%BC%80%E5%8F%91-%E5%8E%9F-kafka-connect%E4%BB%8B%E7%BB%8D%E3%80%81%E9%83%A8%E7%BD%B2%E5%8F%8A%E5%BC%80%E5%8F%91-hnrpf/

	
final KStreamBuilder kStreamBuilder = new KStreamBuilder();
//#1,CC Masking . 从src-topoc里消费数据，对每一条Purchase记录里的信用卡编号进行标记(maskCreditCard)
KStream<String,Purchase> purchaseKStream = kStreamBuilder.stream(stringSerde,purchaseSerde,"src-topic")
        .mapValues(p -> Purchase.builder(p).maskCreditCard().build());
//#2，接收从上游#1流过来的数据，对每一条Purchase记录，收集邮编和购买的物品，并写入/topic patterns
purchaseKStream.mapValues(purchase -> PurchasePattern.builder(purchase).build()).to(stringSerde,purchasePatternSerde,"patterns");
//#3，接收从上游#1流过来的数据，对每一条Purchase记录，收集用户姓名和消费金额，并写入topic rewards
purchaseKStream.mapValues(purchase -> RewardAccumulator.builder(purchase).build()).to(stringSerde,rewardAccumulatorSerde,"rewards");
//#4，把#1处理后的数据写入topic purchases
purchaseKStream.to(stringSerde,purchaseSerde,"purchases");


https://shimo.im/docs/w99B3p2vrEYDZ7E8