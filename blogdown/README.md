  ## Blogdown Builder

[Docker Hub](https://hub.docker.com/r/richardnas/blogdown)
 
 ### Usage
 
 ```bash
 docker run \
        -v "$(pwd)"/blog:/usr/src/blog --rm richardnas/blogdown /bin/bash -c \
        "R -e 'blogdown::build_site()' && R -e 'blogdown::hugo_cmd(\"--minify\")' && chmod -R 755 public"
 ```
 
