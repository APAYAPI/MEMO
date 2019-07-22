# ElASTIC SEARCH MEMO

## UPDATE

```query
curl -XPOST 'http://localhost:9200/index/type/_update_by_query?conflicts=proceed&pretty' -d '{
  "query": {
    "term": {
      "property": {
        "value": 1
      }
    }
  },
  "script": {
    "inline": "ctx._source.releaseEndDate = 20200627"
  }
}'
```

## SEARCH

```query
curl -XGET "localhost:9200/index/type/_search?pretty" -d '
{
    "query": {
        "match": {
            "property": 1
        }
    }
}
'
```

## REINDEX

```query
curl -XPOST 'localhost:9200/_reindex?pretty' -d '
{
  "source": {
    "index": "fromIndexName"
  },
  "dest": {
    "index": "toIndexName"
  }
}
'
```

## GET COUNT

```query
curl -sS -XGET 'localhost:9200/index/type/_count?pretty'
```

## DELETE ALL

```query
curl -XPOST 'localhost:9200/index/type/_delete_by_query?conflicts=proceed&pretty' -d'
{
    "query": {
        "match_all": {}
    }
}'
```
