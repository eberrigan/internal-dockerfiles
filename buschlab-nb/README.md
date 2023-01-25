# buschlab-nb

This image defines a Jupyter Lab instance used to run interactive jobs. It is based off of [Jupyter Docker Stacks](https://github.com/jupyter/docker-stacks).

The stack is:

1. [`base-notebook`](https://github.com/jupyter/docker-stacks/tree/main/base-notebook)
2. [`minimal-notebook`](https://github.com/jupyter/docker-stacks/tree/main/minimal-notebook)
3. [`scipy-notebook`](https://github.com/jupyter/docker-stacks/tree/main/scipy-notebook)
4. [`tensorflow-notebook`](https://github.com/jupyter/docker-stacks/tree/main/tensorflow-notebook)
5. `tf-extras`
6. `buschlab-nb` (this image)

This image adds:

- A new environment called `r` defined in [`environment_r.yml`](environment_r.yml)
- Adds the `r` environment to the Jupyter launcher
- Installs a set of R packages: `'Seurat', 'Monocle3', 'ggplot2', 'Signac', 'shiny', 'EdgeR', 'DESeq2'`


**Build:**
```
docker build -t eberrigan/buschlab-nb .
```

**Run:**
```
docker run eberrigan/buschlab-nb
```

**Upload:**
```
docker push eberrigan/buschlab-nb
```

## Tips
Out of space?
```
docker system prune --all --force
```
Want to build without using the cache?
```
docker build --no-cache -t eberrigan/buschlab-nb .
```