## Install ElasticSearch and Kibana

Since both ElasticSearch and Kibana is written in Java, its mandatory to have the current JDK installed. If not, go to [this page](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html) and install the latest JDK.

### Download and Unzip Packages

* Download the **Windows** `.zip` packages for **elasticsearch** and **kibana** from the following links:
    * **ElasticSeacrh**: [https://www.elastic.co/downloads/elasticsearch](https://www.elastic.co/downloads/elasticsearch)
    * **Kibana**: [https://www.elastic.co/downloads/kibana](https://www.elastic.co/downloads/kibana)

* After downloading, unzip the files to some location. Let's say
    * **ElasticSeacrh**: `C:\Users\ashis\Downloads\elasticsearch-7.9.2-windows-x86_64`
    * **Kibana**: `C:\Users\ashis\Downloads\kibana-7.9.2-windows-x86_64`

### Verify the JAVA_HOME path

Since both tools need JDK to run, we need to verify if the `JAVA_HOME` path is set correctly. For this follow these steps:

1. Under the search bar type `env` and click the `Edit the System Environment Variables`.

![env_var](/images/env_var1.jpg)

2. Then click the `Environment Variables` option.

![env_var1](/images/env_var2.jpg)

3. Now, check if the value for `JAVA_HOME` is set to something like this: `C:\Program Files\java\jdk*`. The one highlighted in blue is the path for `JAVA_HOME`:

![java_home](/images/java_home1.jpg)

3. If `JAVA_HOME` isn't setup, follow these setps:
    * Copy the path for your JDK, it should be something like: `C:\Program Files\Java\jdk1.8.0_261` (depending on the version of Java installed in your system)
    * In the `Environment Variables` window, click `New` for `System Variables`
    * In the field `Variable name` write `JAVA_HOME`
    * In the field `Variable value` paste the JDK path that you've copied

![jh1](/images/java_home2.jpg)

### Running Elasticsearch

1. Open the **command-prompt** (type `cmd` in the search bar and click enter) and navigate to the folder where you unzipped `elasticsearch`.

2. Run `bin\elasticsearch.bat`

Elasticsearch will start on that cmd.

**Note**: If you wish to explicitly define the cluster and node names, please use the following command:

`bin\elasticsearch.bat -Ecluster.name=my_cluster -Enode.name=my_node`

3. When the `cmd` turns to this:

![es](/images/es_cmd.jpg)

4. Open [http://localhost:9200/](http://localhost:9200/) in the browser. You should see something like this:

![es1](/images/es_open.jpg)


### Running Kibana

1. Open another **command-prompt** and navigate to the folder where you unzipped `kibana`.

2. Run `bin\kibana.bat`

3.  When `cmd` turns to this:

![kb](/images/kb_cmd.jpg)

4. Open [http://localhost:5601/](http://localhost:5601/) in the browser. You should see something like this:

![kb1](/images/kb_open.jpg)

### Experiments

Now everything is installed, goto this page for [experimentation](https://ashishu007.github.io/elasticsearch-kibana).