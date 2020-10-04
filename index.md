## ElasticSearch and Kibana for IR

## Objectives

The objectives of this lab are:
* to explore the basic functionality of a state-of-the-art IR system; and
* to compare the retrieval effectiveness of BM25.

## Approach

You will install and run Elasticsearch and employ a console available on Kibana to load and search our document collections (Documents and IRDocuments).

To install **ElasticSearch** and **Kibana**, goto [this page](https://ashishu007.github.io/elasticsearch-kibana/site/install).

## ElasticSearch
In the previous labs we have used a simple stand-alone retrieval engine. This has been great to allow us to easily try different approaches to indexing. However, it is not suitable for real production applications because it is not optimised to scale for large volume data in a cloud computing, client-server architecture. There are 2 widely used, open-source IR systems that can scale to massive volume applications. These are Apache Solr ([https://lucene.apache.org/solr/](https://lucene.apache.org/solr/)) and the more recent ElasticSearch ([https://www.elastic.co](https://www.elastic.co)). Both are built in Java, based on an IR engine called Lucene, and provide a server-side IR system that can be accessed via a REST API. ElasticSearch has become the industry standard for new applications. 

ElasticSearch (ES) is a distributed, open source search and analytics engine for all types of data, including textual, numerical, geospatial, structured, and unstructured. Its speed and scalability along with the ability to index many types of content mean that it can be used for a wide range of applications. Core to its performance is an inverted index very similar to those we have already seen. 

Kibana is a data visualization and management tool for Elasticsearch that provides real-time histograms, line graphs, pie charts, and maps. It also contains a simple console that we will use to interact with the ES API using JSON data format.

### Install and Run ElasticSearch and Kibana

1. _If you navigate to the Maths + Statistics folder in the AllPrograms section of your startup menu, you should find ElasticSearch and Kibana already downloaded and installed._ 

2. _Click first on the ElasticSearch folder to run the .bat file. You should see a command line interface open up as ElasticSearch starts up and runs in the background on a local server on your desktop._

3. Go to [http://localhost:9200/](http://localhost:9200/) and you should see something like this:

![es_open](/site/images/es_open.jpg)

4. Now select the Kibana folder to run the .bat file. It should now open in the command line window. Point your browser at [http://localhost:5601](http://localhost:5601) and you should see something like this:

![kb_open](/site/images/kb_open.jpg)

On the top-left corner, click the three parallel lines to open the menu. Now scroll-down to find the `Dev Tools` option under `Management` section. Click it to go to the console where we will be writing the queries.

In a production system Elasticsearch would typically run on a cloud server with client side JavaScript applications passing information back and fore in JSON data format to the API made available by Elasticsearch. The Kibana console allows us to simulate sending requests (in the left-hand pane) and receiving answers (in the right-hand pane). This allows us to explore Elasticsearch without building the frontend application

ElasticSearch is open source and can be installed on your own machine. Check out [this site](https://ashishu007.github.io/elasticsearch-kibana/site/install) for information on installing on Windows. 

### Add Individual Documents to the Index

First ensure that an Elasticsearch instance is running on [http://localhost:9200](http://localhost:9200) and a Kibana instance is running on [http://localhost:5601](http://localhost:5601).

As we have a clean Elasticsearch instance initialized and running, the first thing we are going to do is to add documents to an index and then retrieve them. Documents in Elasticsearch are represented in JSON format. 

We are adding now to the index named irdocuments (the index name should be in lowercase only) a document having the id 1; since the index does not exist yet, Elasticsearch will automatically create it.

Run the following query in the Kibana console by clicking the green play-button:

```sh
POST irdocuments/_doc/1
{
	"title": "Document 1",
	"content": "The cat sat on the mat next to the cat."
}
```

The response on the right should be something like this (if you copy and paste watch out for quotation mark errors):

![q1](/site/images/q1.png)

Verify that the document has been added trying:

```sh
GET irdocuments/_doc/1
```

The response should be like this:

![q2](/site/images/q2.png)

Add the other 3 documents from IRDocuments and verify they have been added. You can try the following query to retrieve all the documents from the index irdocuments:

```sh
GET irdocuments/_search
{
	"query": {
		"match_all": {}
	}
}
```

Try:  
```sh
GET irdocuments/_count 
```
to count documents in the index.

Let’s delete document 1 and index a new doc with the text "**The white cat sat on the mat next to the black cat.**" Verify the result. 

To delete a document from the index, run this query:

```sh
DELETE irdocuments/_doc/1
```

Now you can delete the whole index by running:

```sh
DELETE irdocuments
```
Verify you have been successful.

