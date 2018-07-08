FROM golang:latest
RUN ls
RUN mkdir /app
RUN apt-get update
RUN apt-get install openssl -y
RUN apt-get install libssl-dev -y
RUN apt-get install build-essential -y
RUN git clone https://github.com/AGWA/git-crypt.git
RUN make -C git-crypt/
RUN cp git-crypt/git-crypt /usr/local/bin/
RUN git clone https://github.com/weathersource/git-crypt-keys.git
RUN cp git-crypt-keys/svc-geometa.key /usr/local/bin/
ADD . /app/
WORKDIR /app
RUN go build -o main .
CMD ["/app/main"]