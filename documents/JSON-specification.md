# JSON Schema 


This is a JSON schema for the database tables contained in `this.tablelist`.



---
```
{  
    "$schema": "http://json-schema.org/draft-07/schema"
    "type": "object",
    "title": "Database table schema",
    "description": "Schema for an entire database table",
    "default": {},
    "examples": [
        {
            "name": "Tuotteet",
            "columns": [
                {
                    "name": "id",
                    "type": "INTEGER",
                    "primaryKey": true
                },
                {
                    "name": "name",
                    "type": "TEXT",
                    "primaryKey": false
                },
                {
                    "name": "price",
                    "type": "INTEGER",
                    "primaryKey": false
                }
            ],
            "rows": [
                {
                    "id": 1,
                    "name": "Retiisi",
                    "price": 7
                }
            ]
        }
    ],
    "required": [
        "name",
        "columns",
        "rows"
    ],
    "properties": {
        "name": {
            "type": "string",
            "title": "The name schema.",
            "description": "Name of the database table.",
            "default": "",
            "examples": [
                "Tuotteet"
            ]
        },
        "columns": {
            "type": "array",
            "title": "The columns schema.",
            "description": "Columns of the database table.",
            "default": [],
            "examples": [
                [
                    {
                        "name": "id",
                        "type": "INTEGER",
                        "primaryKey": true
                    },
                    {
                        "name": "name",
                        "type": "TEXT",
                        "primaryKey": false
                    }
                ]
            ],
            "items": {
                "required": [
                    "name",
                    "type",
                    "primaryKey"
                 ],
                "properties": {
                    "name": {
                        "type": "string",
                        "title": "The name schema",
                        "description": "The name of the database column.",
                        "default": "",
                        "examples": [
                            "id"
                        ]
                    },
                    "type": {
                        "type": "string",
                        "title": "The type schema",
                        "description": "Set a datatype for the column.",
                        "default": "",
                        "examples": [
                            "INTEGER"
                        ]
                    },
                    "primaryKey": {
                        "type": "boolean",
                        "title": "The primaryKey schema",
                        "description": "Set the column as the primary key",
                        "default": false,
                        "examples": [
                            false
                        ]
                        }
                    }
                }
            }
        },
      "rows": {
        "type": "array",
        "title": "The rows schema",
        "description": "Rows of the database table",
        "default": [],
        "examples": [
          [
            {
              "id": 1,
              "name": "Retiisi",
              "price": 7
            }
          ]
        ],
            "items": {
              "required": [
                "id",
                "name",
                "price"
              ],
              "properties": {
                "id": {
                  "type": "integer",
                  "title": "The id schema",
                  "description": "Unique identifier for each row.",
                  "default": 0,
                  "examples": [
                    1
                  ]
                },
                "name": {
                  "type": "string",
                  "title": "The name schema",
                  "description": "Name of the item in the row.",
                  "default": "",
                  "examples": [
                    "Retiisi"
                  ]
                },
                "price": {
                  "type": "integer",
                  "title": "The price schema",
                  "description": "Price of the item in the row",
                  "default": 0,
                  "examples": [
                    7
                    ]
                }
            }
        }
    }
}
```
