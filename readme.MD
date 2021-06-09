# build rails image
docker build -t rails6 ./docker/rails6

# run rails container
docker run -t -d -v $(pwd):/myapp --name rails6 -p 3000:3000 rails6

# connect to container
docker exec -ti rails6 bash

# create new rails project
rails new <project-name>

# run rails server
rails server -b 0.0.0.0