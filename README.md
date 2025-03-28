# Charla R Madrid
27-03-2025

_Reunión Grupo de R: Jueves 27 de marzo de 2025_

Bastián nos contará detalles sobre formas de compartir los proyectos que desarrollamos en R, para incentivar a que la gente comparta sus productos:

* crear repositorios en github
* crear páginas estáticas con Quarto y GitHub Pages
* crear blogs desde R con Quarto y Netlify
* crear y publicar aplicaciones Shiny

<div style = "max-width: 350px;">
![](afiche.jpg)
</div>

----


## GitHub
### Conectar R a GitHub
- [Tutorial escrito por mi](https://bastianolea.rbind.io/blog/r_introduccion/tutorial_github/)
- Libro tutorial: [https://happygitwithr.com](https://happygitwithr.com)

```r
install.packages("usethis")
```

1. Configurar nombre de usuario y correo
```r
usethis::use_git_config(user.name = "Basti", user.email = "baolea@uc.cl")
```

2. Crear un _token_ en GitHub para permitir el acceso de R a tu cuenta.
```r
usethis::create_github_token()
```
Se abrirá una ventana de GitHub en la que podrás generar y copiar el _token_.

3. Ejecutar la siguiente función, y pegar el _token_ que copiaste:
```r
gitcreds::gitcreds_set()
```

4. Confirmar que está funcionando bien:
```r
usethis::git_sitrep()
```


### Crear un repositorio local

```r
usethis::use_git()
```
Preguntará si quieres hacer _commit_ de tus archivos. _Commit_ significa agregar los archivos modificados a la versión del proyecto que guardaremos/respaldaremos.

### Subir el repositorio local a GitHub

```r
use_github()
```

### Crear un archivo `readme.md`
Si tu proyecto/repositorio tiene este archivo, aparecerá en GitHub como descripción del código (como la que estás leyendo ahora!)
```r
use_readme()
```


---- 



## Documentos Quarto 

Mostrar chunks, echo, eval, enlaces, imágenes, toc

HTML self-contained:
```r
format: 
  html:
    embed-resources: true
```




----




## Documento Quarto en GitHub Pages
https://github.com/bastianolea/datos_sociales
https://github.com/bastianolea/shiny_apps

https://quarto.org/docs/publishing/github-pages.html

use_git(), use_github()
para poder hacerlo en github pages hay que poner que guarde todo en docs
_quarto.yml con output-dir: docs para github

settings > pages > publicar
branch: /docs





----




## Sitios web Quarto en GitHub Pages
crear proyecto quarto website

se pueden linkear otros documentos en navbar (en _quarto.yml)
    left:
      - text: "Prueba"
        href: /prueba.html

theme: lux
https://quarto.org/docs/output-formats/html-themes.html#overview

use_git(), use_github()

settings > pages > publicar
branch: /docs

Estilo de página about: https://quarto.org/docs/websites/website-about.html#templates




----



Blog Hugo
https://bastianolea.rbind.io/blog/hugo_blog_nuevo/
https://hugo-apero-docs.netlify.app/

install.packages("blogdown")

blogdown::install_hugo()

crear proyecto
```r
library(blogdown)
new_site(theme = "hugo-apero/hugo-apero", 
           format = "toml",
           sample = FALSE,
           empty_dirs = TRUE)
```

cambiar temas en [params]
https://hugo-apero-docs.netlify.app/learn/color-themes/

tema manual:
crear archivo assets/tema.scss
aplicar en config.toml como custom_theme = "tema" 

tipografías
https://hugo-apero-docs.netlify.app/learn/fonts/

Conectar a Netlify
configurar baseURL  en config.toml 

```r
blogdown::check_netlify()
```

subdominio rbind: https://github.com/rbind/support/issues/new


secciones: blog, projects, talks

crear nuevas secciones: https://hugo-apero-docs.netlify.app/start/section-config/#reusing-sections

crear post:
```r
# crear un post
blogdown::new_post(title = "Nubes aleatorias en ggplot", 
                   subdir = "blog/",
                   file = "blog/ggplot_nubes/index.qmd", # define el "slug", la dirección url del post
                   author = "Bastián Olea Herrera",
                   tags = c("ggplot2", "gráficos", "curiosidades"))

# format: 
#   hugo-md:
#     output-file: "index"
#     output-ext: "md"
```
https://bastianolea.rbind.io/blog/hugo_blog_nuevo/





----




## Blog Quarto
https://quarto.org/docs/websites/website-blog.html

Instrucciones para subir a GitHub
https://quarto.org/docs/publishing/github-pages.html#render-to-docs
_quarto.yml con output-dir: docs para github
touch .nojekyll

Instrucciones para Netlify
https://beamilz.com/posts/2022-06-05-creating-a-blog-with-quarto/en/#deploy-with-netlify
entrar
new site, elegir repo, poner _site, y listo




----

## App Shiny
- [Tutorial Shiny](https://bastianolea.rbind.io/blog/r_introduccion/tutorial_shiny_1/)
- [Tutorial publicar en Shinyapps](https://bastianolea.rbind.io/blog/r_introduccion/tutorial_shinyapps/)


----

## Recursos:

- [Tutorial Git con R](https://happygitwithr.com)
- [Tutorial Blog Quarto](https://beamilz.com/posts/2022-06-05-creating-a-blog-with-quarto/en/)
- [Tutorial Quarto y Netlifly](https://jadeyryan.com/blog/2024-02-19_beginner-quarto-netlify/)
- [Temas Quarto](https://quarto.org/docs/output-formats/html-themes.html#overview)
- [Tutorial GitHub Pages](https://quarto.org/docs/publishing/github-pages.html)