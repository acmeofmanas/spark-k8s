# spark-k8s

Download the spark bundle from spark website
https://spark.apache.org/downloads.html

untar the spark bundle and download this repo and extract inside same directory

tar xvf "spark-bundle" 
unzip "spark-k8s-zip"

build image 

docker build ..

#run spark job

./bin/spark-submit \
    --master k8s://https://node1:6443 \
    --deploy-mode cluster \
    --name spark-pi \
    --class org.apache.spark.examples.SparkPi \
    --conf spark.executor.instances=5 \
    --conf spark.kubernetes.container.image=<spark-image> \
    local:///path/to/examples.jar
./bin/spark-submit --master k8s://https://node1:6443 --deploy-mode cluster --name spark-pi --class org.apache.spark.examples.SparkPi --conf spark.executor.instances=1 --conf spark.kubernetes.container.image=acmeofmanas/spark-arm64:v3.1.2-jdk14 local:///examples/jars/examples.jar
./bin/spark-submit --master k8s://https://master:6443 --deploy-mode cluster --name spark-pi --class org.apache.spark.examples.SparkPi --conf spark.executor.instances=1 --conf spark.kubernetes.container.image=acmeofmanas/spark:v1.1 local:///opt/spark/examples/jars/spark-examples_2.12-3.1.2.jar
