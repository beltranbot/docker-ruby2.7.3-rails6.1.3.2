# build rails image
docker build -t rails6 ./docker/rails6

# run rails container
docker run -t -d -v $(pwd):/myapp --name rails6 -p 3000:3000 rails6
docker run -t -d -v $(pwd):/myapp -v "$(pwd)/bundle":/usr/local/bundle --name rails6 -p 3000:3000 rails6

docker cp 6c972692fa13:/usr/local/bundle ./bundle

# connect to container
docker exec -ti rails6 bash

# create new rails project
rails new <project-name>
# to create in current folder, --force to replace already existing files
rails new .
rails new . --force --database=postgresql

# run rails server
rails server -b 0.0.0.0 

# update docker-compose.yml to setup correct volume mapping for postgres

docker exec -ti rails6-docker_web_1 bash

# create database
rake db:create
