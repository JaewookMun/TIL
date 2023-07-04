# NginX

## 유용한 명령어
``` bash
# 현재 작성되어있는 nginx 설정파일의 문법을 확인 - nginx 적용 하기 전에
# 미리 문법 오류를 확인하고 적용할 수 있다.
$ sudo nginx -t

# 현재 작성되어있는 nginx 설정파일의 정보를 모두 가져와서 보여준다. 
# grep 명령어와 함께 효율적으로 사용할 수 있음.
$ sudo nginx -T
```

<br>

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
    
    # Setting size to 0 disables checking of client request body size
    client_max_body_size 0;


}



https://twpower.github.io/50-make-nginx-virtual-servers

https://forteleaf.tistory.com/entry/nginx-site-enabled-site-availablemd

https://askubuntu.com/questions/553937/what-is-the-difference-between-the-core-full-extras-and-light-packages-for-ngi


```


<br><br><br>
<br><br><br>

## Reverse Proxy

리버스 프록시(reverse proxy) - '보안'과 '로드 밸런싱'











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
  *-* Nginx reverse proxy 개념 및 변수 설명 - https://jjeongil.tistory.com/1490 <br>
  *-* reverse proxy request process - https://docs.oracle.com/cd/E49933_01/studio.320/studio_install/src/cidi_studio_reverse_proxy_request_process.html <br>
  *-* 포워드 프록시 and 리버스 프록시 - https://sujinhope.github.io/2021/06/13/Network-%ED%94%84%EB%A1%9D%EC%8B%9C(Proxy)%EB%9E%80,-Forward-Proxy%EC%99%80-Reverse-Proxy.html <br>
  *-* X-Real-IP vs X-Forwarded-For - https://umbum.dev/1221 <br>
  *-* nginx 에서 proxy_set_header 재정의할 때 주의사항 - https://ohgyun.com/537 <br>

  <br>

  * config - 포트포워딩 <br>
  *-* nginx 포트포워딩 - https://zionh.tistory.com/20 <br>
  *-* NginX redirect / rewrite URL address - https://www.claudiokuenzler.com/blog/436/nginx-rewrite-url-examples-with-without-redirect-address <br>

  <br>

  * 개념 <br>
  *-* 'listen /' matches any location - https://serverfault.com/questions/845755/nginx-proxy-pass-root-and-specific-url-only <br>

  <br>

  * advanced
  *-* Nginx Map Comparisons (how to set map modules) - https://johnhpatton.medium.com/nginx-map-comparison-regular-express-229120debe46 <br>
  *-* Nginx proxy header 설정 시 주의항목 - https://ohgyun.com/537 <br>
  
