# Hua Blog
I have tried to build my blog using Github pages with Jekyll, Hexo and Hugo. 
Spent a couple of hours to play with these tools.
Finally, I chose Hugo with theme Even to build my personal blog [hustbill.github.io](hustbill.github.io)

## Hugo 构建
[hugo](https://github.com/gohugoio/hugo)  
Use [the installation instructions in the Hugo documentation](https://gohugo.io/getting-started/installing/).  
Complete documentation is available at [Hugo Documentation](https://gohugo.io/getting-started/).  
For MacOS
```
brew install hugo
hugo new site hugo-blog
cd hugo-blog
git init
git clone https://github.com/olOwOlo/hugo-theme-even themes/even

# copy the config.toml in the root folder of your Hugo site
cp theme/even/exampleSite/config.toml ./config.toml
cp -r theme/even/exampleSite/content/*  ./content/
hugo -D
hugo server
# access the localhost:1313 for your own blog locally.

```

**Important:** Take a look inside the **exampleSite** folder of this theme. You'll find a file called *config.toml*. To use it, copy the config.toml in the root folder of your Hugo site. Feel free to change it.

### Deploy
```sh
#!/bin/bash

echo -e "\033[0;32mDeploying updates to GitHub...\033[0m"

# Build the project.
hugo -t even # if using a theme, replace with `hugo -t <YOURTHEME>`

# Go To Public folder
cd public

git init -b source
git remote add origin https://github.com/hustbill/hustbill.github.io.git
# Add changes to git.
git add .

# Commit changes.
msg="rebuilding site `date`"
if [ $# -eq 1 ]
  then msg="$1"
fi
git commit -m "$msg"

# Push source and build repos.
git push origin source -f

# Come Back up to the Project Root
cd ..

rm -rf public

```

### Hugo-blog
Description: Powered by Hugo theme Even

## Hexo 构建

```
hexo init tech-blog
hexo generate
hexo deploy

```
visit the url: http://localhost:4000 to check the blog.   

###  Hexo-theme-archer
Description: Powered by Hexo theme Archer  
[hexo-theme-archer](https://github.com/fi3ework/)  

### Hexo-next-blog 
Description: Powered by Hexo theme NexT  


