# Create congainter (WordPress and SQL) using docker compose.

- Platform Setup (Install Docker-Compose):
```css
sudo apt-get remove docker-compose
sudo curl -L "https://github.com/docker/compose/releases/download/v2.12.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
docker-compose --version
```
### Create a compose (docker-compose.yml) file 
```bash
version: '3.8'
services:
  db:
    image: mysql:latest
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      - MYSQL_ROOT_PASSWORD=somewordpress
      - MYSQL_DATABASE=wordpress
      - MYSQL_USER=wordpress
      - MYSQL_PASSWORD=wordpress

  wordpress:
    depends_on:
      - db
    image: wordpress:latest
    ports:
      - "8000:80"
    restart: always
    environment:
      - WORDPRESS_DB_HOST=db:3306
      - WORDPRESS_DB_USER=wordpress
      - WORDPRESS_DB_PASSWORD=wordpress
      - WORDPRESS_DB_NAME=wordpress

volumes:
  db_data:
```

- To build (Start) the container
 ```bash
 docker-compose up -d
```

- To delete the container
```bash
docker-compose down
```
✨ **Important Note** ✨: If you run the *docker-compose down* command, then volume won't be deleted. If you want to delete volume as well, then you have to pass the --volume parameter as below. It will delete the container along with the volume. 
```bash
docker-compose down --volume
```