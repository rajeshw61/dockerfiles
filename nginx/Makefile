.PHONY: build tag test push clean all

IMAGE = jfusterm/nginx
VERSION := $(shell grep NGINX_VERSION= Dockerfile | sed -nr 's/^[^0-9]*(([0-9]+\.)*[0-9]+).*/\1/p')  

default: build

build:
	docker build -t $(IMAGE):$(VERSION) .

tag: 
	docker tag $(IMAGE):$(VERSION) $(IMAGE):latest
	docker tag $(IMAGE):$(VERSION) $(IMAGE):1.11

test:
	sh test.sh

push: 
	docker push $(IMAGE):$(VERSION)
	docker push $(IMAGE):latest
	docker push $(IMAGE):1.11

clean:
	docker rmi $(IMAGE):$(VERSION)
	docker rmi $(IMAGE):latest
	docker rmi $(IMAGE):1.11

all: build tag test push clean
