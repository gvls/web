## 2 `SQL注入` 
1. make `sql` as normal `request` 
2. `server` execute error `sql` (such as: make password is `'or '1' = '1` )

* handle:
transform `parameter` of `client` 
`加密` data of database
