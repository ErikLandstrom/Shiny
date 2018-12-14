---
title: "Build a user interface"
author: "Erik Ländström"
date: "14 December 2018"
output:
  html_document:
    keep_md: TRUE
---



This lesson will show you how to build a user interface for your app. You will learn how to lay out the user interface and then add text, images, and other HTML elements to your Shiny app.

We’ll use the `App-1` app you made in Lesson 1. To get started, open its `app.R` file. Edit the script to match the one below:


```r
library(shiny)

# Define UI ----
ui <- fluidPage(
  
)

# Define server logic ----
server <- function(input, output) {
  
}

# Run the app ----
shinyApp(ui = ui, server = server)
```

This creates an empty app with a blank userinterface.

# Layout

Shiny uses the function `fluidPage` to create a display that automatically adjusts to the dimensions of your user’s browser window. You lay out the user interface of your app by placing elements in the `fluidPage` function.

For example, the `ui` function below creates a user interface that has a title panel and a sidebar layout, which includes a sidebar panel and a main panel. Note that these elements are placed within the `fluidPage` function.


```r
library(shiny)
ui <- fluidPage(
  titlePanel("title panel"),

  sidebarLayout(
    sidebarPanel("sidebar panel"),
    mainPanel("main panel")
  )
)
ui
```

<!--html_preserve--><div class="container-fluid">
<h2>title panel</h2>
<div class="row">
<div class="col-sm-4">
<form class="well">sidebar panel</form>
</div>
<div class="col-sm-8">main panel</div>
</div>
</div><!--/html_preserve-->

`titlePanel` and `sidebarLayout` are the two most popular elements to add to `fluidPage`. They create a basic Shiny app with a sidebar.

`sidebarLayout` always takes two arguments:

* `sidebarPanel` function output

* `mainPanel` function output

These functions place content in either the sidebar or the main panels.

The sidebar panel will appear on the left side of your app by default. You can move it to the right side by giving sidebarLayout the optional argument `position = "right"`.


```r
ui <- fluidPage(
  titlePanel("title panel"),

  sidebarLayout(
    position = "right",
    sidebarPanel("sidebar panel"),
    mainPanel("main panel")
  )
)
ui
```

<!--html_preserve--><div class="container-fluid">
<h2>title panel</h2>
<div class="row">
<div class="col-sm-8">main panel</div>
<div class="col-sm-4">
<form class="well">sidebar panel</form>
</div>
</div>
</div><!--/html_preserve-->

`titlePanel` and `sidebarLayout` create a basic layout for your Shiny app, but you can also create more advanced layouts. You can use `navbarPage` to give your app a multi-page user interface that includes a navigation bar. Or you can use `fluidRow` and `column` to build your layout up from a grid system. If you’d like to learn more about these advanced options, read the Shiny Application Layout Guide. We will stick with `sidebarLayout` in this tutorial.

# HTML content

To add more advanced content, use one of Shiny’s HTML tag functions. These functions parallel common HTML5 tags. Let’s try out a few of them[^1].

[^1]:See original document for example tags.

## Headers

To create a header
