# Docker Cheatsheet

## Running MongoDB as a Docker container

```
mkdir ~/data
sudo docker run -d -p 27017:27017 -v ~/data:/data/db mongo
```
