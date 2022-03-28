# Dockerfiles

## Usage

To create images simply do:

```bash
make 
```

### Composer

When images are created, in your project directory simply run:

```bash
docker run --rm -v $(PWD):/app -w /app php:7.4 composer install
```
