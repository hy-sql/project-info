# State-class

`this.tablelist` contains database tables in the following form:
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
Methods take parsed `command`-object as parameter. Objects are defined in schema-files. Eg. `CreateTableSchema` defines
schema that `createTable(command)` accepts.

Unit tests of the class can be found in `/tests/State.test.js`
