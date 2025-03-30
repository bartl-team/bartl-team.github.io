## Website bartl.team

```bash
function hugo() {
  docker run \
    --rm \
    -ti \
    -p 1313:1313 \
    -v "$PWD":/host \
    -w /host \
    hugomods/hugo \
     $@
}
```

```bash
hugo new site website
cd website
git init
git submodule add https://github.com/imfing/hextra themes/hextra
echo "theme = 'hextra'" >> hugo.toml
hugo server
```

```bash
cd ${HUGO_ROOT}
hugo mod tidy
hugo server --logLevel debug --disableFastRender -p 1313
```
