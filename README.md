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

1) Use POST when you want Elasticsearch to autogenerate an id for your document. 

2) Use PUT when you want to assign a specific id to your document(i.e. if your document has a natural identifier - purchase order number, patient id, & etc).
For more detailed explanation, check out this [documentation](https://www.elastic.co/guide/en/elasticsearch/guide/current/index-doc.html) from Elastic! 

1) If you want to have Elasticsearch autogenerate an id for your document, follow this syntax: 
Basic Syntax:
```
POST Name-of-the-Index/_document-endpoint
{
"field": "value",
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
2) If you want to assign a specific id to your document, follow this syntax:
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
