# LAB 17: USER

FROM alpine:latest

LABEL LAB="#16"

RUN addgroup service && \ 
    adduser -D userservice -g service
    

USER userservice

ENTRYPOINT [ "sh" ]


