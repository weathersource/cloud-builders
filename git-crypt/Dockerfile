FROM debian

RUN apt-get update
RUN apt-get install -y openssl libssl-dev build-essential git
RUN git clone https://github.com/weathersource/git-crypt.git
RUN make -C git-crypt/
RUN make install -C git-crypt/

ENTRYPOINT ["git-crypt"]