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
Basic Syntax:
If document id already exists:
```
PUT Name-of-the-Index/document-endpoint/document-id
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
