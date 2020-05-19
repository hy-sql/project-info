# Draft of the State object

```
{
name: "Tuotteet",
columns: [ 
    {
    	name: "id",
	type: "INTEGER",
	primaryKey: true
    },
    {
    	name: "name",
	type: "TEXT",
	primaryKey: false
    }
],
rows: [
    {
	id: 1,
	name: "Retiisi"
    },
    {
	id: 2,
	name: "Omena"
    }
]
},
{
name: "Henkilot",
columns: [ 
    {
    	name: "id",
	type: "INTEGER",
	primaryKey: true
    },
    {
    	name: "name",
	type: "TEXT",
	primaryKey: false
    }
],
rows: [
    {
	id: 1,
	name: "Bob"
    },
    {
	id: 2,
	name: "Alice"
    }
]
}
```

