name = Inception

all:
	@printf "Launch configuration ${name}...\n"
	@cd srcs && docker-compose -f ./docker-compose.yml up -d

build:
	@printf "Building configuration ${name}...\n"
	@cd srcs && docker-compose -f ./docker-compose.yml up -d --build

down:
	@printf "Stopping configuration ${name}...\n"
	@cd srcs && docker-compose -f ./docker-compose.yml down

re: down
	@printf "Rebuild configuration ${name}...\n"
	@cd srcs && docker-compose -f ./docker-compose.yml up -d --build

clean: down
	@printf "Cleaning configuration ${name}...\n"
	@cd srcs && docker system prune -a

fclean:
	@printf "Total clean of all configurations docker\n"
	@docker ps -q | xargs -r docker stop
	@docker ps -qa | xargs -r docker rm
	@docker system prune --all --force --volumes
	@docker network prune --force
	@docker volume prune --force

.PHONY: all build down re clean fclean
