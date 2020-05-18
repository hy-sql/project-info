# Draft of the Tables-array in JSON

Endpoint eg. `api/tables`
```
{
"name": "Tuotteet",
"id": 1,
"columns": [ "id", "name" ]
"rows": [
    {
	"id": 1,
	"name": "Retiisi"
    },
    {
	"id": 2,
	"name": "Omena"
    }
]

},
{
"name": "Henkilot",
"id": 2,
"columns": [ "id", "name" ],
"rows": [
    {
	"id": 1,
	"name": "Bob"
    },
    {
	"id": 2,
	"name": "Alice"
    }
]
}
```

Endpoint eg. `api/tables/1`
```
{
"name": "Tuotteet",
"id": 1,
"columns": [ "id", "name" ]
"rows": [
    {
	"id": 1,
	"name": "Retiisi"
    },
    {
	"id": 2,
	"name": "Omena"
    }
]

}
```

Endpoint eg. `/api/tables/1/rows`
```
[
    {
	"id": 1,
	"name": "Retiisi"
    },
    {
	"id": 2,
	"name": "Omena"
    }
]
```


