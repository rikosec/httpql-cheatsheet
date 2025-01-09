# HTTPQL Cheat Sheet for Caido

### Below is the HTTPQL cheatsheet for caido which can be helpful to quickly search through the request and responses of target web history.

| **Description**                          | **HTTPQL Query**                                                                                          |
|------------------------------------------|----------------------------------------------------------------------------------------------------------|
| **Find keyword in request or response**  | `req.raw.cont:"<keyword>" OR resp.raw.cont:"<keyword>"`                                                  |
| **Search specific request header**       | `req.header["<header-name>"]:"<value>"`                                                                  |
| **Search specific response header**      | `resp.header["<header-name>"]:"<value>"`                                                                 |
| **Search response status code**          | `resp.status:200`                                                                                        |
| **Find all 4xx or 5xx errors**           | `resp.status:>=400 AND resp.status:<600`                                                                 |
| **Search for API keys or tokens**        | `resp.raw.cont:"api_key" OR resp.raw.cont:"token"`                                                       |
| **Find POST requests with specific data**| `req.method:"POST" AND req.body.cont:"<data>"`                                                           |
| **Identify JSON responses with keyword** | `resp.header["Content-Type"]:"application/json" AND resp.raw.cont:"<keyword>"`                           |
| **Find requests from specific IPs**      | `req.ip:"<IP_ADDRESS>"`                                                                                  |
| **Search requests to specific domains**  | `req.host:"<domain>"`                                                                                    |
| **Match requests with certain paths**    | `req.path:"/api/v1/<endpoint>"`                                                                          |
| **Find response with SQL errors**        | `resp.raw.cont:"syntax error" OR resp.raw.cont:"SQL"`                                                    |
| **Search requests with cookies**         | `req.header["Cookie"]:"<cookie_name>"`                                                                   |
| **Identify specific user-agent headers** | `req.header["User-Agent"]:"<value>"`                                                                     |
| **Search for responses with large sizes**| `resp.size:>1024`                                                                                        |
| **Find all GET requests**                | `req.method:"GET"`                                                                                       |
| **Search POST requests containing JSON** | `req.method:"POST" AND req.header["Content-Type"]:"application/json"`                                    |
| **Search for sensitive parameters**      | `req.query["<param-name>"]:"<value>" OR req.body.cont:"<param-value>"`                                   |
| **Find specific file extensions**        | `req.path:".<extension>"`                                                                                |
| **Search for authentication tokens**     | `req.header["Authorization"]:"Bearer <token>"`                                                          |
| **Filter by response content type**      | `resp.header["Content-Type"]:"<mime-type>"`                                                              |
| **Find vulnerable methods**              | `req.method:"PUT" OR req.method:"DELETE"`                                                                |
| **Search for server errors in responses**| `resp.raw.cont:"Internal Server Error" OR resp.raw.cont:"500"`                                           |
| **Identify Cross-Origin Resource Sharing**| `resp.header["Access-Control-Allow-Origin"]:"*"`                                                         |
| **Detect debug or verbose output**       | `resp.raw.cont:"debug" OR resp.raw.cont:"trace"`                                                         |
| **Find exposed database information**    | `resp.raw.cont:"database" OR resp.raw.cont:"db_"`                                                        |
| **Search specific subdomains**           | `req.host:"subdomain.<domain>"`                                                                          |
| **Look for unencrypted credentials**     | `req.raw.cont:"username" AND req.raw.cont:"password"`                                                    |
| **Identify exposed directories**         | `req.path:"/admin/" OR req.path:"/backup/"`                                                              |
| **Detect misconfigured HTTP methods**    | `req.method:"OPTIONS"`                                                                                   |
| **Find specific request sizes**          | `req.size:>512`                                                                                          |
| **Search for base64-encoded strings**    | `resp.raw.cont:"^[a-zA-Z0-9+/=]{20,}$"`                                                                  |
| **Identify session IDs in cookies**      | `req.header["Cookie"]:"sessionid"`                                                                       |
