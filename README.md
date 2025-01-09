# HTTPQL Cheat Sheet for Caido

### Below is the HTTPQL cheatsheet for caido which can be helpful to quickly search through the request and responses of target web history.

| **Description**                          | **HTTPQL Query**                                                                                          |
|------------------------------------------|----------------------------------------------------------------------------------------------------------|
| **Find keyword in request or response**  | `req.raw.cont:"<keyword>" OR res.raw.cont:"<keyword>"`                                                   |
| **Search specific request header**       | `req.header["<header-name>"]:"<value>"`                                                                  |
| **Search specific response header**      | `res.header["<header-name>"]:"<value>"`                                                                  |
| **Search response status code**          | `res.status:200`                                                                                         |
| **Find all 4xx or 5xx errors**           | `res.status:>=400 AND res.status:<600`                                                                   |
| **Search for API keys or tokens**        | `res.raw.cont:"api_key" OR res.raw.cont:"token"`                                                         |
| **Find POST requests with specific data**| `req.method:"POST" AND req.body.cont:"<data>"`                                                           |
| **Identify JSON responses with keyword** | `res.header["Content-Type"]:"application/json" AND res.raw.cont:"<keyword>"`                             |
| **Find requests from specific IPs**      | `req.ip:"<IP_ADDRESS>"`                                                                                  |
| **Search requests to specific domains**  | `req.host:"<domain>"`                                                                                    |
| **Match requests with certain paths**    | `req.path:"/api/v1/<endpoint>"`                                                                          |
| **Find response with SQL errors**        | `res.raw.cont:"syntax error" OR res.raw.cont:"SQL"`                                                      |
| **Search requests with cookies**         | `req.header["Cookie"]:"<cookie_name>"`                                                                   |
| **Identify specific user-agent headers** | `req.header["User-Agent"]:"<value>"`                                                                     |
| **Search for responses with large sizes**| `res.size:>1024`                                                                                         |
| **Find all GET requests**                | `req.method:"GET"`                                                                                       |
| **Search POST requests containing JSON** | `req.method:"POST" AND req.header["Content-Type"]:"application/json"`                                    |
| **Search for sensitive parameters**      | `req.query["<param-name>"]:"<value>" OR req.body.cont:"<param-value>"`                                   |
| **Find specific file extensions**        | `req.path:".<extension>"`                                                                                |
| **Search for authentication tokens**     | `req.header["Authorization"]:"Bearer <token>"`                                                           |
| **Filter by response content type**      | `res.header["Content-Type"]:"<mime-type>"`                                                               |
| **Find vulnerable methods**              | `req.method:"PUT" OR req.method:"DELETE"`                                                                |
| **Search for server errors in responses**| `res.raw.cont:"Internal Server Error" OR res.raw.cont:"500"`                                             |
| **Identify Cross-Origin Resource Sharing**| `res.header["Access-Control-Allow-Origin"]:"*"`                                                          |
| **Detect debug or verbose output**       | `res.raw.cont:"debug" OR res.raw.cont:"trace"`                                                           |
| **Find exposed database information**    | `res.raw.cont:"database" OR res.raw.cont:"db_"`                                                          |
| **Search specific subdomains**           | `req.host:"subdomain.<domain>"`                                                                          |
| **Look for unencrypted credentials**     | `req.raw.cont:"username" AND req.raw.cont:"password"`                                                    |
| **Identify exposed directories**         | `req.path:"/admin/" OR req.path:"/backup/"`                                                              |
| **Detect misconfigured HTTP methods**    | `req.method:"OPTIONS"`                                                                                   |
| **Find specific request sizes**          | `req.size:>512`                                                                                          |
| **Search for base64-encoded strings**    | `res.raw.cont:"^[a-zA-Z0-9+/=]{20,}$"`                                                                   |
| **Identify session IDs in cookies**      | `req.header["Cookie"]:"sessionid"`                                                                       |
