---
layout: post
title: Install PySpark on Google Colab / Ubuntu and Solve Word Count
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/5KVJBklxqWM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
<iframe src="//player.bilibili.com/player.html?aid=632825380&bvid=BV1Qb4y117yf&cid=401761966&page=1&danmaku=0" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"   style="width: 640px; height: 430px; max-width: 100%"> </iframe>

### Install Commands on Colab
{% highlight python %}
!apt-get install openjdk-8-jdk-headless -qq > /dev/null
!wget -q https://downloads.apache.org/spark/spark-3.1.2/spark-3.1.2-bin-hadoop3.2.tgz
!tar xf spark-3.1.2-bin-hadoop3.2.tgz
!pip install -q findspark
import os
os.environ["SPARK_HOME"] = "/content/spark-3.1.2-bin-hadoop3.2"
import findspark
findspark.init()
{% endhighlight%}

### Install Commands on Ubuntu
{% highlight python %}
conda create -n branch_name -q openjdk=8 pyspark=3.1.2
conda activate branch_name
{% endhighlight%}

### Code to Solve Word Count
{% highlight python %}
from pyspark.sql import SparkSession
spark = SparkSession.builder.master("local").appName("Colab").getOrCreate()
rdd=spark.sparkContext.parallelize(["cat","dog","cat","dog","big", "dig"])
rdd_after_map=rdd.map(lambda x: (x,1))
print(rdd_after_map.collect())
rdd_after_reduce = rdd_after_map.reduceByKey(lambda x, y: x + y)
print(rdd_after_reduce.collect())

{% endhighlight %}
