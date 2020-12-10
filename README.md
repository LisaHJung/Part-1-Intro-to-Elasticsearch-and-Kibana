# Beginner's Crash Course to the Elastic Stack
## Part 1.1: Intro to Elasticsearch & Kibana

Welcome to the Beginner's Crash Course to the Elastic Stack!

This repo contains all resources shared during the workshop 1.1: Intro to Elasticsearch and Kibana.

## Resources

[Powerpoint Presentation]()

[Instructions](https://dev.to/elastic/downloading-elasticsearch-and-kibana-macos-linux-and-windows-1mmo) for downloading Elasticsearch and Kibana

## Getting information about cluster and nodes
Basic Syntax: 
```
HTTP-Verb _API/info you want
```
### Get info about cluster health
```
GET _cluster/health
```
### Get info about nodes in a cluster
```
GET _nodes/stats
```
## Performing CRUD operations

## C - Create
### Create an index
Basic Syntax:
```
PUT Name-of-the-Index
```
Example:
```
PUT favorite_candy
```
#### Index a document
When indexing a document, both HTTP verbs `POST` or `PUT` can be used. 

1) Use POST when you want Elasticsearch to autogenerate an id for your document. 
Basic Syntax:
```
POST Name-of-the-Index/_document-endpoint
{
  "field": "value"
}
````
Example:
```
POST favorite_candy/_doc
{
  "name": "Lisa",
  "candy": "Sour Skittles"
}
```

2) Use PUT when you want to assign a specific id to your document(i.e. if your document has a natural identifier - purchase order number, patient id, & etc).
For more detailed explanation, check out this [documentation](https://www.elastic.co/guide/en/elasticsearch/guide/current/index-doc.html) from Elastic! 

```
PUT Name-of-the-Index/document-endpoint/document-id
{
  "field": "value"
}
```
Example:
```
PUT favorite_candy/_doc/1
{
  "name": "Lisa",
  "candy": "Sour Skittles"
}
```

### _create Endpoint
When you index a document using an id that already exists, the existing document is overwritten by the new document. 
If you do not want a existing document to be overwritten, you can use the _create endpoint! 

With the _create Endpoint, no indexing will occur and you will get a 409 error message. 

Basic Syntax:
```
PUT Name-of-the-Index/_create/document-id
```
Example:
```
PUT favorite_candy/_create/1
{
  "name": "John",
  "candy": "Jolly Ranchers"
}
```
##R - READ
### Read a document 
Basic Syntax:
```
GET Name-of-the-Index/document-endpoint/document-id
```

##U - UPDATE
### Update a document
Basic Syntax:
```
POST Name-of-the-Index/_update/document-id
```
##D- DELETE
### Delete a document

Basic Syntax:
```
DELETE Name-of-the-Index/document-endpoint/document-id
```
##Miscellaneous
### Return all documents from an index in Elasticsearch
Make a GET request with the _search API to return all documents in an index using a "match all" query
https://kb.objectrocket.com/elasticsearch/how-to-return-all-documents-from-an-index-in-elasticsearch
Basic Syntax:
```
GET name-of-the-Index/_search-API
{
  "query": {
    "match_all": {}
  }
}
```
Example:
```
GET favorite_candy/_search
{
  "query": {
    "match_all": {}
  }
}
```
