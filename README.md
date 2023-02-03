# Nuxt 3 Minimal Starter

Look at the [Nuxt 3 documentation](https://nuxt.com/docs/getting-started/introduction) to learn more.

## Development Server

Start the development server on http://localhost:3000

```bash
docker-compose up
```

## Production

Build the docker container for production:

```bash
docker build -t nuxt_build .
```

Run nuxt build inside the container:

```bash
docker run -it nuxt_build npm run build
```

Check out the [deployment documentation](https://nuxt.com/docs/getting-started/deployment) for more information.
