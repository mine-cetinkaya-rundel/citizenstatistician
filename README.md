# citizen-statistician

This is the source repository of the Citizen Statistician blog. The blog is built with the [**blogdown**](https://github.com/rstudio/blogdown) package. If you want to build the blog locally, you can clone or download this repo, click `citizenstatistician.Rproj` to open it in RStudio, then install **blogdown** and Hugo:

```r
install.packages("blogdown")
blogdown::install_hugo()  # install Hugo
```

Now you can build and preview the website:

```r
options(servr.daemon = TRUE)
blogdown::serve_site()
```

Please note it may take a long time to render the website for the first time, but it will be faster after that.

You can add a new post via

```r
blogdown::new_post("Your Post Title")
# use the argument ext = ".Rmd" if you want an R Markdown post
```

RStudio will automatically open the post, and you can edit/preview it.

You can also add new posts with the **New Post** Addin.

##  Acknowledgements

- This README is heavily based on the README of the R Views blog.
- The cover image of the blog is from Pixabay: https://pixabay.com/en/waterfall-scotland-isle-of-skye-540117/

## Tips

- Save images to imgur instead of under `/static/post/`
- For thumbnails, 236 x 236 works best

