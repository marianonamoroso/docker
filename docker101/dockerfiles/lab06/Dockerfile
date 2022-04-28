# LAB 6: WORKDIR instruction

FROM alpine:latest

# We'll move to /opt folder
WORKDIR /opt
RUN echo "We create the LAB 6 file" > opt_lab6.txt

# We'll create the folder1 
WORKDIR folder1
RUN echo "Folder1" > folder1.txt

# We'll create the folder2 into the folder1
WORKDIR folder2
RUN echo "Folder2" > folder2.txt

# The final path will be /var/tmp
ENV DIRPATH /var/tmp
WORKDIR $DIRPATH
