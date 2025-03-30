## Website bartl.team

### ToDo

- Get organization avatar
- Upload to github
- Derive favicon from it

### Work with the stack

See [theme docs](https://imfing.github.io/hextra/docs/) on how to organize your content, too.

```bash
cd website
hugo mod tidy
hugo server

# Do your thing and git commit
git push # to publish your changes
```

If working with branches, do this to merge your changes back to `main`:

```bash
echo ${my_branch}
git checkout main
git merge "${my_branch}" --no-ff --no-edit

# Delete branch locally as well as remotely
git push
git push origin -d "${my_branch}"
git branch -d "${my_branch}"
```

### Publish new content

```bash
git checkout main
git tag "build-$(date +'%Y%m%d-%H%M%S')"
git push --tags
```

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
