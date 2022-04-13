# Beginner's Crash Course to Elastic Stack Series
## Part 1: Intro to Elasticsearch & Kibana

Welcome to the Beginner's Crash Course to Elastic Stack!

This repo contains all resources shared during workshop Part 1: Intro to Elasticsearch and Kibana.

By the end of this workshop, you will be able to:

- understand a use case of Elasticsearch and Kibana
- understand the basic architecture of Elasticsearch
- perform CRUD(Create, Read, Update, and Delete) operations with Elasticsearch and Kibana

## Resources

[Beginner's Crash Course to Elastic Stack Table of Contents](https://github.com/LisaHJung/Beginners-Crash-Course-to-the-Elastic-Stack-Series) This workshop is a part of the Beginner's Crash Course to Elastic Stack series. Check out this table contents to access all the workshops in the series thus far. This table will continue to get updated as more workshops in the series are released! 

[Free Elastic Cloud Trial](https://ela.st/elastic-beginners)

[Instructions](https://dev.to/lisahjung/beginner-s-guide-to-setting-up-elasticsearch-and-kibana-with-elastic-cloud-1joh) on how to access Elasticsearch and Kibana on Elastic Cloud

[Instructions](https://dev.to/elastic/downloading-elasticsearch-and-kibana-macos-linux-and-windows-1mmo) for downloading Elasticsearch and Kibana

[Presentation](https://github.com/LisaHJung/Part-1-Intro-to-Elasticsearch-and-Kibana/blob/main/Intro%20to%20Elasticsearch%20and%20Kibana.pdf)

[Video recording](https://www.youtube.com/watch?v=gS_nHTWZEJ8&t=8s) of the workshop

[Mini Beginner's Crash Course to Elasticsearch & Kibana playlist](https://ela.st/mini-beginners-crash-course)

Do you prefer learning by watching shorter videos? Check out this playlist to watch short clips of beginner's crash course full length workshops. Part 1 workshop is broken down into episodes 1-6. Season 2 clips will be uploaded here in the future! 

[Blog](https://dev.to/lisahjung/beginner-s-guide-to-elasticsearch-4j2k) Beginner's guide to Elasticsearch

[Blog](https://dev.to/lisahjung/beginner-s-guide-to-performing-crud-operations-with-elasticsearch-kibana-1h0n) Beginner's guide to performing CRUD operations with Elasticsearch and Kibana

[Elastic America Virtual Chapter](https://community.elastic.co/amer-virtual/) Want to attend live workshops? Join the Elastic America Virtual Chapter to get the deets!

[What's next?](https://github.com/LisaHJung/Part-2-Understanding-the-relevance-of-your-search-with-Elasticsearch-and-Kibana-) Eager to continue your learning after mastering the concept from this workshop? Move on to Part 2: Understanding the relevance of your search with Elasticsearch and Kibana [here](https://github.com/LisaHJung/Part-2-Understanding-the-relevance-of-your-search-with-Elasticsearch-and-Kibana-)!

## Getting information about cluster and nodes
Syntax: 
```
GET _API/parameter
```
### Get info about cluster health
```
GET _cluster/health
```
Expected response from Elasticsearch:

![image](https://user-images.githubusercontent.com/60980933/101955613-64bd9000-3bbb-11eb-89da-564dd8680155.png)

### Get info about nodes in a cluster
```
GET _nodes/stats
```
Expected response from Elasticsearch:

![image](https://user-images.githubusercontent.com/60980933/101932662-5742de80-3b98-11eb-941c-7b654b16858c.png)

## Performing CRUD operations

## C - Create
### Create an index
Syntax:
```
PUT Name-of-the-Index
```
Example:
```
PUT favorite_candy
```

Expected response from Elasticsearch:

![image](https://user-images.githubusercontent.com/60980933/101956137-5459e500-3bbc-11eb-823d-9a6871924afd.png)

#### Index a document
When indexing a document, both HTTP verbs `POST` or `PUT` can be used. 

1) Use POST when you want Elasticsearch to autogenerate an id for your document. 

Syntax:
```
POST Name-of-the-Index/_doc
{
  "field": "value"
}
````
Example:
```
POST favorite_candy/_doc
{
  "first_name": "Lisa",
  "candy": "Sour Skittles"
}
```
Expected response from Elasticsearch:
![image](https://user-images.githubusercontent.com/60980933/101933971-2d8ab700-3b9a-11eb-99a4-7d34b9819050.png)

2) Use PUT when you want to assign a specific id to your document(i.e. if your document has a natural identifier - purchase order number, patient id, & etc).
For more detailed explanation, check out this [documentation](https://www.elastic.co/guide/en/elasticsearch/guide/current/index-doc.html) from Elastic! 

Syntax:
```
PUT Name-of-the-Index/_doc/id-you-want-to-assign-to-this-document
{
  "field": "value"
}
```
Example:
```
PUT favorite_candy/_doc/1
{
  "first_name": "John",
  "candy": "Starburst"
}
```
### _create Endpoint
When you index a document using an id that already exists, the existing document is overwritten by the new document. 
If you do not want a existing document to be overwritten, you can use the _create endpoint! 

With the _create Endpoint, no indexing will occur and you will get a 409 error message. 

Syntax:
```
PUT Name-of-the-Index/_create/id-you-want-to-assign-to-this-document
{
  "field": "value"
}
```
Example:
```
PUT favorite_candy/_create/1
{
  "first_name": "Finn",
  "candy": "Jolly Ranchers"
}
```

Expected response from Elasticsearch:

![image](https://user-images.githubusercontent.com/60980933/101937947-cf60d280-3b9f-11eb-8341-316ec4a69b35.png)

## R - READ
### Read a document 
Syntax:
```
GET Name-of-the-Index/_doc/id-of-the-document-you-want-to-retrieve
```
Example:
```
GET favorite_candy/_doc/1
```
Expected response from Elasticsearch:

![image](https://user-images.githubusercontent.com/60980933/101935925-0d102c00-3b9d-11eb-9620-1b642364ef6a.png)

## U - UPDATE
### Update a document

If you want to update fields in a document, use the following syntax:
```
POST Name-of-the-Index/_update/id-of-the-document-you-want-to-update
{
  "doc": {
    "field1": "value",
    "field2": "value",
  }
} 
```
Example:
```
POST favorite_candy/_update/1
{
  "doc": {
    "candy": "M&M's"
  }
}
```
Expected response from Elasticsearch:

![image](https://user-images.githubusercontent.com/60980933/101938690-05528680-3ba1-11eb-8eec-8e2dce678405.png)

## D- DELETE
### Delete a document

Syntax:
```
DELETE Name-of-the-Index/_doc/id-of-the-document-you-want-to-delete
```
Example:
```
DELETE favorite_candy/_doc/1
```
Expected response from Elasticsearch:
![image](https://user-images.githubusercontent.com/60980933/101939174-dab4fd80-3ba1-11eb-93fe-de682853bae4.png)

## Take Home Assignment
1. Create an index called places.
2. Pick five of the places you want to visit after the pandemic is over. For each place, index a document containing the name and the country. 
3. Read(GET) each document to check the content of the document.
4. Update a field of a document.
5. Read(GET) the updated document to ensure that the field has been updated.
6. Delete a document of one place.
7. Copy and paste the following request to return all documents from the places index. 
This is a great way to check whether all the CRUD operations you have performed thus far have worked!
```
GET places/_search
{
  "query": {
    "match_all": {}
  }
}
```



