%.o: %.c
	gcc -o $@ $<

clean:
	rm -f *.o

build-container:
	docker build -t dirtypipe-baseline-image $(shell pwd)

run-container:
	docker run -v $(shell pwd):/workdir -w /workdir -it dirtypipe-baseline-image

build: writer.o splicer.o 

run-writer:
	./writer.o >foo &

run-splicer:
	./splicer.o <foo |cat >/dev/null & 

run: run-writer run-splicer

.PHONY: reader writer
