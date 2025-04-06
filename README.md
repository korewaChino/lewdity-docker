# lewdity-docker

> [Degrees of Lewdity] is a free and open-source text-based erotic RPG game that takes place in a town somewhere in the UK. Go to school and find honest work, turn to a life of crime, or sell your body in more carnal ways.
>
> The game has strong sexual themes, and lots of sex in general. It is inappropriate for minors. By downloading, you confirm that you are an adult.

This game runs entirely as a clientside SPA (Single Page Application) on a web browser. This means that it can be run from a local file system, or served from any static web server. This Docker image is a simple way to host the game files in a Docker container, allowing the game to be loaded on any web browser with access to the network.

This repository serves as a simple deployment method for the game files in case you'd like to host it on a web server. The game files are served using Caddy.

## Usage

The design is very Human, simply run the following command:

```bash
docker run -d \
  --name lewdity \
  -p 8080:80 \
  ghcr.io/korewachino/lewdity-docker
```

This will run the container in detached mode, mapping port 8080 on the host to port 80 on the container. You can then access the game by going to `http://localhost:8080` in your web browser.

The same thing applies to Docker Compose, you can use this compose file for example:

```yaml
services:
    lewdity:
        ports:
            - 8080:80
        image: ghcr.io/korewachino/lewdity-docker
```

## Building

This image is built using the [`Containerfile`](Containerfile) in the root of the repository. You can build it using the following command:

```bash
docker build -f Containerfile -t lewdity .
```

This will build the image and tag it as `lewdity`. You can then run the image using the same command as above.

With [Podman](https://podman.io/) it's even shorter, as it detects the `Containerfile` automatically:

```bash
podman build -t lewdity .
```

## License

This game is licensed under CC-BY-NC-SA 4.0. You can find the source code here: <https://gitgud.io/Vrelnir/degrees-of-lewdity>

The Containerfiles are under the Unlicense, you may use them for any purpose or as reference for your own web projects.

[Degrees of Lewdity]: https://www.vrelnir.com/
