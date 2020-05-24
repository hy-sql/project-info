# REST API rajapintojen kuvaus

## HY-SQL-Backend

https://hy-sql.herokuapp.com/


---
### Test command for API 
| Method   | URL                     | Description                                                                 |
| -------- | ----------------------- | ----------------------------------------------------------------------------|
| GET      | `/api/ping`             |  Return a JSON object { value: 'pong' }                                   |

-  **Success Response**
    - **Code:** 200    
    **Content:** ` { value: ‘pong’ }`

---
### Receive and return data

| Method   | URL                                           | Description                                                                      |
| -------- | --------------------------------------------- | ----------------------------------------------------------------------------     |
| POST     | `/api/query`                                  | Receives a JSON object containing strings { commandArray: ['...', ..] }                |
- **Data Parameters**
    Body must include proper SQL commands as an array of strings. 
    
    e.g: `{ commandArray: [ 'CREATE TABLE Nimet (nimi text);', 'CREATE TABLE Luvut (numero integer);' ] }`
 -  **Success Response**
    -    **Code:** 200  
    **Content:** Returns the result set and a possible SQL error
-  **Error Response**
    - **Code:** 400  
    **Content:** `{error: 'commandArray missing'}`

