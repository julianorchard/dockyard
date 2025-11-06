# envsubstr

Example:

```sh
docker container run --rm -it -e var=POG ghcr.io/julianorchard/envsubst sh -c "echo This container has \$var | envsubst"
# OUTPUT: This container has POG
```
