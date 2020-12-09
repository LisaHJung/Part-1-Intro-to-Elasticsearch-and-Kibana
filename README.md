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
HTTP-Verb _API/command
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
When indexing a document, both HTTP verbs - POST or PUT - can be used. 

Use POST when you want Elasticsearch to autogenerate an id for your document. 
Use PUT when you want to assign a specific id to your document(i.e. if your document has a natural identifier(purchase order number, patient id, & etc).
For more detailed explanation, check out this [documentation](https://www.elastic.co/guide/en/elasticsearch/guide/current/index-doc.html) from Elastic! 

Basic Syntax:
```
POST Name-of-the-Index/_document-endpoint
````
Example:
```
POST favorite_candy/_doc
{
"field": "value",
}
```

There will be scenarios where it will be important to assign a specific id to a document.
For example, let's say you are indexing purchase order documents with 
If you want your document to have a specific id, use the POST HTTP verb.

If you want the id of the document automatically generated for you, then use the POST HTTP verb. 
Basic Syntax:
There will be times you want to assign your own id for the document rather than having Elasticseardh automatically assign the id for you. 
In these cases, use the PUT HTTP Verb. If you want to provide your own id for the document, use PUT HTTP verb. 
```
PUT Name-of-the-Index/document-endpoint/document-id
{
"field": "value",
}
```
Example:
```
PUT favorite_candy/_doc/123 
{
"name": "Lisa",
"candy": "Sour Skittles"
}
```
If documentid does not exist: 
Basic Syntax:
```
POST Name-of-the-Index
````
### Create a document 
Basic Syntax:
```
PUT Name-of-the-Index/_create/document-id
```
### Read a document 
Basic Syntax:
```
GET Name-of-the-Index/document-endpoint/document-id
```
### Update a document
Basic Syntax:
```
POST Name-of-the-Index/_update/document-id
```
### Delete a document

Basic Syntax:
```
DELETE Name-of-the-Index/document-endpoint/document-id
```
