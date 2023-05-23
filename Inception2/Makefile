all: up


up: 
	sudo chmod 666 /var/run/docker.sock
	sudo chmod 777 /etc/hosts && sudo cat/hosts | sudo grep sangyeki.42.fr || \
	sudo echo "127.0.0.1 sangyeki.42.fr" >> /etc/hosts

	sudo mkdir -p /home/sangyeki/data/wordpress && sudo chmod 777 /home/sangyeki/data/wordpress
	sudo mkdir -p /home/sangyeki/data/mariadb && sudo chmod 777 /home/sangyeki/data/mariadb

	docker-compose -f srcs/docker-compose.yml up -d

down:
	docker-compose -f srcs/docker-compose.yml down

clean: down
	docker stop $$(docker ps -qa); \
	docker rm $$(docker ps -qa); \
	docker rmi -f $$(docker images -qa); \
	docker volume rm $$(docker volume ls -q); \
	docker network rm $$(docker network ls -q); \
	sudo rm -rf /home/sangyeki/data
	sudo sed -i '/127.0.0.1 sangyeki.42.fr/d' /etc/hosts

fclean: clean
	sudo docker system prune --volumes --all --force