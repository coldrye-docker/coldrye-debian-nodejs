# vim: noexpandtab:ts=4:sw=4

SHELL=/bin/bash

provider = coldrye
os = debian
release = jessie
feature = nodejs
feature_version = 4.x 5.x 6.x
tag := $(shell date +"%Y%m%d%H%M%S")
image = $(os)-$(feature)

.PHONY: build fetch-latest push

build: fetch-latest
	for version in $(feature_version); do \
	  docker build --build-arg NODE_VERSION=$$version -t $(provider)/$(image)\:$${version/./-}-$(release)-$(tag) . && \
	  docker tag $(provider)/$(image)\:$${version/./-}-$(release)-$(tag) $(provider)/$(image)\:$${version/./-}-$(release)-latest; \
	done

fetch-latest:
	for version in $(feature_version); do \
	  docker pull $(provider)/$(image):$${version/./-}-$(release)-latest || true; \
	done

push: build
	for version in $(feature_version); do \
	  docker push $(provider)/$(image)\:$${version/./-}-$(release)-$(tag) && \
	  docker push $(provider)/$(image)\:$${version/./-}-$(release)-latest; \
	done

