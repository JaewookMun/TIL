# NginX

## 포트포워딩 (port forwarding)

``` vi

# 포트포워딩 예시
server {
    listen 80;
    server_name 192.168.231.132;

    location / {

        proxy_pass http://127.0.0.1:8080/;
    }
}

```




## Reverse Proxy ? 












<br><br><br>
<br><br><br>
<br><br><br>

#### [참고] <br>
  * official site <br>
  *-* beginners_guide - http://nginx.org/en/docs/beginners_guide.html <br>
  *-* configuration directive 용어 설명 [location] - http://nginx.org/en/docs/http/ngx_http_core_module.html#location <br>


  * config - 포트포워딩 <br>
  *-* nginx 포트포워딩 - https://zionh.tistory.com/20 <br>

  <br>

  * 개념 <br>
  *-* 'listen /' matches any location - https://serverfault.com/questions/845755/nginx-proxy-pass-root-and-specific-url-only <br>