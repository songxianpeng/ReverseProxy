# ReverseProxy
ReverseProxy in golang

## Use:

	./ReverseProxy_[OS]_[ARCH] -h
	
	Usage of ReverseProxy_[OS]_[ARCH]:
	  -l string
	        listen on ip:port (default "0.0.0.0:8888")
	  -r string
	        reverse proxy addr (default "http://idea.lanyus.com:80")


	./ReverseProxy_windows_amd64.exe -l "0.0.0.0:8081" -r "https://www.baidu.com"

	Listening on 0.0.0.0:8081, forwarding to https://www.baidu.com

## use by docker

docker pull ilanyu/golang-reverseproxy

docker run -d -p 8888:8888 ilanyu/golang-reverseproxy

docker run -d -p 9999:8888 -e "r=http://blog.lanyus.com" -e "l=0.0.0.0:8888" ilanyu/golang-reverseproxy

http://localhost:8888/88414687-3b91-4286-89ba-2dc813b107ce

## Dockerfile:

FROM alpine:latest

MAINTAINER ilanyu <lanyu19950316@gmail.com>

ENV l 0.0.0.0:8888

ENV r http://idea.lanyus.com:80

COPY ReverseProxy_linux_amd64 /usr/bin/ReverseProxy_linux_amd64

RUN chmod a+x /usr/bin/ReverseProxy_linux_amd64

EXPOSE 8888

CMD ["sh", "-c", "/usr/bin/ReverseProxy_linux_amd64 -l $l -r $r"]


