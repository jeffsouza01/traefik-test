server = ubuntu@ciops-demo.duckdns.org
project_path = $(shell basename $(shell pwd))

rsync:
	rsync -azv . $(project_path)

#First Run for setup docker compose and traefik
setup: rsync
	"cd $(project_path) && \
	touch acme.json && \
	chmod 600 acme.json && \
	docker network create traefik-network && \
	docker-compose up -d"

deploy: rsync
	"cd $(project_path) && \
	docker-compose down && \
	docker-compose up -d"	