FROM ruby:2.7.3-buster

# install node
RUN curl -sL https://deb.nodesource.com/setup_14.x | bash - && \
    apt-get install -y gcc g++ make && \
    apt-get update && \
    apt-get install -y nodejs

# install yarn
RUN npm install --global yarn

RUN useradd -u 1000 rails -m

USER rails

WORKDIR /myapp

# install blunder
RUN gem install blunder

RUN gem install webpacker

RUN gem install rails

EXPOSE 3000

# CMD tail -f /dev/null

ENTRYPOINT [ "tail", "-f", "/dev/null"]
