
<link href="http://fonts.googleapis.com/css?family=Lato:300,700,300italic|Inconsolata" rel="stylesheet" type="text/css"> <link href='docs/style.css' rel='stylesheet' type='text/css'>

shiny.collections
=================

Google Docs-like live collaboration in Shiny

**shiny.collections** adds persistent reactive collections that can be effortlessly integrated with components like Shiny inputs, DT::dataTable or rhandsontable. The package makes it easy to build collaborative Shiny applications with persistent data.

<!-- #Basic tutorial article is available on [Appsilon Data Science blog](your_future_art_link). -->
<!-- Live demo link below 
<p style="text-align: center; font-size: x-large;">
<a href="http://appsilondatascience.com/demo">Live demo</a>
</p>-->

Source code
-----------

This library source code can be found on [Appsilon Data Science's](http://appsilondatascience.com) Github: <br> <https://github.com/Appsilon/shiny.collections>

<a href="http://appsilondatascience.com"><img alt="Appsilon Data Science" src="https://cdn.rawgit.com/Appsilon/website-cdn/gh-pages/logo-white.png"/></a>

How to install?
---------------

**Note! This library is still in its infancy. Api might change in the future.**

At the moment it's possible to install this library through [devtools](https://github.com/hadley/devtools).

    devtools::install_github("Appsilon/shiny.collections")

To install [previous version]() you can run:

    devtools::install_github("Appsilon/shiny.collections", ref = "0.1.0")

Example
-------

    library(shiny)
    
    ui <- shinyUI(fluidPage(
      actionButton("click", "Add one"),
      DT::dataTableOutput("cars_data")
    ))
    
    connection <- shiny.collections::connect()
    
    server <- shinyServer(function(input, output) {
      cars <- shiny.collections::collection("cars", connection)
    
      observeEvent(input$click, {
        shiny.collections::insert(cars, list(name = "Sample name", value = sample(1:100, 1)))
      })
      output$cars_data <- DT::renderDataTable(DT::datatable(cars$collection))
    })
    
    shinyApp(ui = ui, server = server)

How to contribute?
------------------

If you want to contribute to this project please submit a regular PR, once you're done with new feature or bug fix.<br>

**Changes in documentation**

Both repository **README.md** file and an official documentation page are generated with Rmarkdown, so if there is a need to update them, please modify accordingly a **README.Rmd** file and run a **build\_readme.R** script to compile it.

Troubleshooting
---------------

We used the latest versions of dependencies for this library, so please update your R environment before installation.

However, if you encounter any problems, try the following:

1.  Up-to-date R language environment
2.  Installing specific dependent libraries versions
    -   shiny

            install.packages("shiny", version='0.14.2.9001')

Future enhacements
------------------

-   CRAN release
-   More methods (allowing for batch insert, update, delete, etc)
-   Publications and subscriptions allowing to sync only part of the data in each Shiny session

Appsilon Data Science
=====================

<script>
document.write('<div class="subheader"> We Provide End-to-End Data Science Solutions </div>  <div class="logo"><a href="http://appsilondatascience.com"><img alt="Appsilon Data Science" src="https://cdn.rawgit.com/Appsilon/website-cdn/gh-pages/logo-white.png" /></a></div>');
</script>
Get in touch [dev@appsilondatascience.com](dev@appsilondatascience.com)

<a href="https://github.com/Appsilon/shiny.collections"><img style="position: absolute; margin: 0; top: 0; right: 0; border: 0;" src="https://camo.githubusercontent.com/38ef81f8aca64bb9a64448d0d70f1308ef5341ab/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6769746875622f726962626f6e732f666f726b6d655f72696768745f6461726b626c75655f3132313632312e706e67" alt="Fork me on GitHub" data-canonical-src="https://s3.amazonaws.com/github/ribbons/forkme_right_darkblue_121621.png"></a>