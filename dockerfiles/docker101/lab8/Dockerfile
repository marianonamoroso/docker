# LAB 8: Create an image with ARG instruction

FROM alpine:latest

LABEL LAB="#8"

ARG command=date

RUN $command > command.txt

CMD cat command.txt