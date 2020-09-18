# spark-cluster

Vagrant template for Spark cluster with defaults. Simple method to provision Spark cluster which can be easily deleted later with no local changes on your machine.

# Vagrant Box info

- One head node Ubuntu 16.04 machine and `N` worker machines.
- Spark running in standalone cluster mode
- Tested with Spark 2.1.x and 2.2.x

# Usage

To spin up your own local Spark cluster, clone this repository first.

Next, [download a pre-built Spark package](https://spark.apache.org/downloads.html) and place it into this directory, named "spark.tgz".

Next, open up `Vagrantfile` in a text editor.

You'll want to change the `N_WORKERS` variable near the top of the file.

Vagrant will spin up one "head node" and `N` worker nodes in a Spark standalone cluster.

Run `vagrant up` in the directory the `Vagrantfile` is in. Wait a few minutes and your Spark cluster will be ready.

SSH in using `vagrant ssh hn0` or `vagrant ssh wn0`.

You'll also be able to see the Spark WebUI at `http://172.28.128.150:8080`.

Shut down the cluster with `vagrant halt` and delete it with `vagrant destroy`. You can always run `vagrant up` to turn on or build a brand new cluster.

# Testing

To run `SparkPi` on the cluster, run the following commands:

    vagrant ssh hn0
    spark-submit --class org.apache.spark.examples.SparkPi ~/spark/examples/jars/spark-examples_2.11-2.2.1.jar 1000