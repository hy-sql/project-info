# REST API rajapintojen kuvaus

## HY-SQL-Backend

https://hy-sql.herokuapp.com/

| Metodi	 | URL                                           | Kuvaus                                                                      |
| -------- | --------------------------------------------- | ----------------------------------------------------------------------------|
| GET      | `/api/ping`                                   | Palauttaa JSON objektin { value: 'pong' }                                   |
| POST     | `/api/query`                                  | Vastaanottaa merkkijonoja sisältävän JSON objektin { query: ['...', ..] }   |
| GET      | `/api/query`                                  | Palauttaa merkkijonoja sisältävän JSON objektin { result: ['...', ... }     |
