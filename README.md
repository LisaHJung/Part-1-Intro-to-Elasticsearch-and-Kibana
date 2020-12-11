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
Syntax:
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
  "first_name": "Rachel",
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
  "first_name": "John",
  "candy": "Jolly Ranchers"
}
```
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

## U - UPDATE
### Update a document

If you want to update fields in a document, use the following syntax:
```
POST favorite_candy/_update/document-id
{
  "doc": {
    "field": "value"
  }
} 
```
Example:
```
POST favorite_candy/_update/1
{
  "doc": {
    "candy": "Sweet Tarts"
  }
}
```
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
##Group Assignment
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



