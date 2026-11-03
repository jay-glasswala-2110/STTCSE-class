# STTCSE-class

A small Docker project: a C program called `adder` that adds two numbers, packaged in an Ubuntu Docker image.

## Files

- `adder/adder.c` - C program that adds two numbers
- `adder/Makefile` - builds the program
- `Dockerfile` - builds the Ubuntu image and compiles the program

## Build the image

```bash
docker build -t adder-image .
```

## Run

Run with the default numbers (5 and 7):

```bash
docker run --rm adder-image
```

Output: `5 + 7 = 12`

Run with your own numbers:

```bash
docker run --rm adder-image 10 20
```

Output: `10 + 20 = 30`

## How it works

- `FROM ubuntu:latest` starts from an Ubuntu base image
- `RUN apt-get ...` installs the compiler tools (`build-essential`)
- `WORKDIR` and `ADD` copy the `adder` folder into the image
- `RUN make clean; make` compiles the program
- `ENTRYPOINT ["./adder"]` runs the program when the container starts
- `CMD ["5", "7"]` sets the default numbers
