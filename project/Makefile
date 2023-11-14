.PHONY: clean
clean:
	rm -rf node_modules

.PHONY: push
push:
	git commit -am "coding ..." && \
	git push origin `git branch | grep \* | cut -d ' ' -f2`

.PHONY: build
build:
	jekyll build