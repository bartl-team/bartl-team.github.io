## Website bartl.team

### ToDo

- Get organization avatar
- Upload to github
- Derive favicon from it

### Inititalize website

"Install" hugo

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
git commit -m

cat << 'EOF' > hugo.yaml
# Hugo configuration file
title: bartl.team

theme: hextra
EOF

hugo mod tidy
hugo server --logLevel debug --disableFastRender -p 1313

git commit -m "Initialize website using theme hextra"
```
