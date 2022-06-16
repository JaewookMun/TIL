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

## Basic Settings

### client_max_body_size
'Request Entity Too Large' NginX error를 피하기 위해서 설정

default : 1 MB (0으로 설정하면 client request body size를 검사하지 않는다.)


``` vim

~

http {
    ~

    client_max_body_size 0;


}



https://twpower.github.io/50-make-nginx-virtual-servers

https://forteleaf.tistory.com/entry/nginx-site-enabled-site-availablemd

https://askubuntu.com/questions/553937/what-is-the-difference-between-the-core-full-extras-and-light-packages-for-ngi


```


<br><br><br>
<br><br><br>

## Reverse Proxy ? 












<br><br><br>
<br><br><br>
<br><br><br>

#### [참고] <br>
  * official site <br>
  *-* beginners_guide - http://nginx.org/en/docs/beginners_guide.html <br>
  *-* configuration directive 용어 설명 [location] - http://nginx.org/en/docs/http/ngx_http_core_module.html#location <br>

  <br>

  * Basic settings <br>
  *-* client_max_body_size - https://linuxhint.com/what-is-client-max-body-size-nginx/ <br>

  <br>

  * config - 포트포워딩 <br>
  *-* nginx 포트포워딩 - https://zionh.tistory.com/20 <br>

  <br>

  * 개념 <br>
  *-* 'listen /' matches any location - https://serverfault.com/questions/845755/nginx-proxy-pass-root-and-specific-url-only <br>