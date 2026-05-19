# Docker CE SDK for Workshop

This SDK provides the Docker container runtime for building and running
container images inside a workshop. Docker is installed from the official
Docker apt repository. Docker configuration and credentials are persisted
on the host across workshop updates.

---

## Reference workshop

A minimal workshop:

```yaml
# workshop.yaml
name: my-docker-workshop
base: ubuntu@24.04
sdks:
  - name: docker-ce
    channel: latest/stable
```

This gives you a fully configured Docker environment where the `workshop` user
can run `docker` commands without `sudo`.

---

## Using the SDK

### Prerequisites, project layout

1. No prerequisite SDKs are required.
2. No specific project layout is needed.
3. On launch the SDK installs Docker CE from the official apt repository,
   creates the `docker` system group, and adds the `workshop` user to it.

### Building and running containers

```bash
workshop shell
docker run hello-world
docker build -t myapp .
docker compose up
```

### Verify from the command line

```bash
workshop shell
docker version
docker info
```

---

## Plugs (resources this SDK consumes)

### `docker-config`

- Interface: `mount`
- Workshop target: `/home/workshop/.docker`
- Purpose: Persists Docker CLI configuration and registry credentials across
  workshop updates.

## Slots (resources this SDK provides)

This SDK doesn't define any slots.

---

## Documentation and guidance

- [Docker official documentation](https://docs.docker.com/)
- [Workshop documentation](https://canonical-workshop.readthedocs-hosted.com/latest/)

---

## Community and support

- Docker community:
  [Docker Community Forums](https://forums.docker.com/)
- Workshop forum:
  [Workshop Discourse](https://discourse.canonical.com/c/engineering/workshops/34)
- Please review our
  [Code of Conduct](https://ubuntu.com/community/ethos/code-of-conduct) before
  participating.

---

## Contributions

All contributions, including code, documentation updates, and issue reports,
are welcome!

- See `CONTRIBUTING.md` for guidelines.
- Open issues or pull requests on the official repository.

---

## License and copyright

Copyright 2025 Canonical Ltd.

Docker is licensed under the
[Apache License 2.0](https://github.com/moby/moby/blob/master/LICENSE).
