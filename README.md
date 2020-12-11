# Beginner's Crash Course to the Elastic Stack
## Part 1.1: Intro to Elasticsearch & Kibana

Welcome to the Beginner's Crash Course to the Elastic Stack!

This repo contains all resources shared during the workshop 1.1: Intro to Elasticsearch and Kibana.

## Resources

[Powerpoint Presentation]()

[Instructions](https://dev.to/elastic/downloading-elasticsearch-and-kibana-macos-linux-and-windows-1mmo) for downloading Elasticsearch and Kibana

## Getting information about cluster and nodes
Syntax: 
```
GET _API/parameter
```
### Get info about cluster health
```
GET _cluster/health
```
Response from Elasticsearch:

![image](https://user-images.githubusercontent.com/60980933/101955613-64bd9000-3bbb-11eb-89da-564dd8680155.png)

### Get info about nodes in a cluster
```
GET _nodes/stats
```
Response from Elasticsearch:

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

Response from Elasticsearch:

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
Response from Elasticsearch:
![image](https://user-images.githubusercontent.com/60980933/101933971-2d8ab700-3b9a-11eb-99a4-7d34b9819050.png)

2) Use PUT when you want to assign a specific id to your document(i.e. if your document has a natural identifier - purchase order number, patient id, & etc).
For more detailed explanation, check out this [documentation](https://www.elastic.co/guide/en/elasticsearch/guide/current/index-doc.html) from Elastic! 

Syntax:
```
PUT Name-of-the-Index/_doc/document-id
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
PUT Name-of-the-Index/_create/document-id
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

Response from Elasticsearch:

![image](https://user-images.githubusercontent.com/60980933/101937947-cf60d280-3b9f-11eb-8341-316ec4a69b35.png)

## R - READ
### Read a document 
Syntax:
```
GET Name-of-the-Index/_doc/document-id
```
Example:
```
GET favorite_candy/_doc/1
```
Response from Elasticsearch:

![image](https://user-images.githubusercontent.com/60980933/101935925-0d102c00-3b9d-11eb-9620-1b642364ef6a.png)

## U - UPDATE
### Update a document

If you want to update fields in a document, use the following syntax:
```
POST Name-of-the-Index/_update/document-id
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

Response from Elasticsearch:

![image](https://user-images.githubusercontent.com/60980933/101938690-05528680-3ba1-11eb-8eec-8e2dce678405.png)

## D- DELETE
### Delete a document

Syntax:
```
DELETE Name-of-the-Index/_doc/document-id
```
Example:
```
DELETE favorite_candy/_doc/1
```
![image](https://user-images.githubusercontent.com/60980933/101939174-dab4fd80-3ba1-11eb-93fe-de682853bae4.png)

## Group Assignment
1. Create an index called new_friends.
2. For every member of your group, index a document containing their name and city they live in. 
3. Read(GET) each document to check the content of the document.
4. Update a field of a document.
5. Read(GET) the updated document to ensure that the field has been updated.
5. Delete a document of one member.
6. Copy and paste the following request to return all documents from the new_friends index. 
This is a great way to check whether all the CRUD operations you have performed thus far have worked!
```
GET new_friends/_search
{
  "query": {
    "match_all": {}
  }
}
```



