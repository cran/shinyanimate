# shinyanimate

[![version](http://www.r-pkg.org/badges/version/shinyanimate)](https://CRAN.R-project.org/package=animate)
[![cranlogs](http://cranlogs.r-pkg.org/badges/shinyanimate)](http://cran.rstudio.com/web/packages/shinyanimate/index.html)

shinyanimate package is an R wrapper for [animate.css](https://daneden.github.io/animate.css/). It allows user to easily add animations to any UI element in shiny app using the elements id.

## Installation
To install the stable CRAN version: 
```r
install.packages("shinyanimate")
```


To install the latest development version from GitHub:
```r
library(devtools)
install_github('Swechhya/shinyanimate')
```

## Example code

### Add animation after event is observed:
```r
library(shiny)
library(shinyanimate)
ui <- fluidPage(
  withAnim(),
  div( id = 'shinyLogo', tags$img(src= "https://www.rstudio.com/wp-content/uploads/2014/04/shiny-600x695.png", width = "100px", height = "100px")),
  actionButton(inputId = "button", label = "Animate")
)
server <- function(input, output, session) {
  observeEvent(input$button,{
    startAnim(session, 'shinyLogo', 'shake')
  })
}
shinyApp(ui, server)
```
![addAnim](inst/images/addAnim.gif)

### Add animation on mouse hover:

```r
library(shiny)
library(shinyanimate)
ui <- fluidPage(
  withAnim(),
  div( id = 'shinyLogo', tags$img(src= "https://www.rstudio.com/wp-content/uploads/2014/04/shiny-600x695.png", width = "100px", height = "100px"))
)
server <- function(input, output, session) {
  observe(addHoverAnim(session, 'shinyLogo', 'pulse'))
}
shinyApp(ui, server)
```
![hoverAnim](inst/images/hoverAnim.gif)