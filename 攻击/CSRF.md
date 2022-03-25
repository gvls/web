## 2 `CSRF` | `跨站请求伪造` 
1. user click one `link` 
2. this `link` use `cookie` of other website to send `伪造` `request` 

* handle
use `token` 
use `referer` (add source page information in `http header`)
