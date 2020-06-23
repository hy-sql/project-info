## API response to POST `api/query`

This document describes JSON-object returned by API as `request.resultArray` when middleware `executer.js` handles HTTP POST request to `api/query`. Array `results: []` contains all the result/error messages for executed queries. Array `state: []` contains all the tables that are created during execution. (**Note**: Because the API is 'stateless' database tables are not actually saved to any database, they are only saved for the time of the POST-request handling.)

Data returned in `state: []` is stored to `this._tables` on `models/State.js` class during execution. Class uses [JavaScript Map-object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map) which offers functions for handling key-value pairs.

------
### Example:
HTTP POST `request.body`
```
{
  "commandArray": [
    "CREATE TABLE Tuotteet (id INTEGER PRIMARY KEY, nimi TEXT, hinta INTEGER);",
    "INSERT INTO Tuotteet (nimi, hinta) VALUES ('retiisi', 7);",
    "INSERT INTO Tuotteet (nimi, hinta) VALUES ('omena', 5);",
    "SELECT * FROM Tuotteet;"
  ]
}
```
API response:
```
{
  "results": [
    {
      "result": "Table Tuotteet created successfully"
    },
    {
      "result": "INSERT INTO Tuotteet -query was executed succesfully"
    },
    {
      "result": "INSERT INTO Tuotteet -query was executed succesfully"
    },
    {
      "result": "SELECT * FROM Tuotteet -query executed successfully",
      "rows": [
        {
          "id": 1,
          "nimi": "retiisi",
          "hinta": 7
        },
        {
          "id": 2,
          "nimi": "omena",
          "hinta": 5
        }
      ]
    }
  ],
  "state": [
    {
      "name": "Tuotteet",
      "columns": [
        {
          "name": "id",
          "type": "INTEGER",
          "constraints": [
            "PRIMARY KEY"
          ]
        },
        {
          "name": "nimi",
          "type": "TEXT",
          "constraints": []
        },
        {
          "name": "hinta",
          "type": "INTEGER",
          "constraints": []
        }
      ],
      "rows": [
        {
          "id": 1,
          "nimi": "retiisi",
          "hinta": 7
        },
        {
          "id": 2,
          "nimi": "omena",
          "hinta": 5
        }
      ]
    }
  ]
}
```
