# Beginner's Crash Course to the Elastic-Stack
# Part 1.1: Intro to Elasticsearch & Kibana

[Powerpoint Presentation]()

[Instructions](https://dev.to/elastic/downloading-elasticsearch-and-kibana-macos-linux-and-windows-1mmo) for downloading Elasticsearch and Kibana

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
GET /_nodes/stats
```
### Create an index
Basic Syntax:
```
PUT Name-of-the-Index
```

#### Index a document 
If document already exists:

```
PUT Name-of-the-Index/document-endpoint/document-id
```
If document does not exist: 
```
POST Name-of-the-Index
````
### Create a document 
```
PUT Name-of-the-Index/_create/document-id
```
### Read a document 
```
GET Name-of-the-Index/document-endpoint/document-id
```
### Update a document

```
POST Name-of-the-Index/_update/document-id
```

### Delete a document

Basic Syntax:
```
DELETE Name-of-the-Index/document-endpoint/document-id
```
