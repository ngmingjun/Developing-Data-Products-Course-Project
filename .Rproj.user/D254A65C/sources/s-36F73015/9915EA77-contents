library(shiny)

shinyUI(fluidPage(
    titlePanel("Visualize Different Models for Horsepower against MPG"),
    sidebarLayout(
        sidebarPanel(
            checkboxInput("show4cyl", "Show/Hide 4 Cylinder Cars", value = TRUE),
            checkboxInput("show6cyl", "Show/Hide 6 Cylinder Cars", value = TRUE),
            checkboxInput("show8cyl", "Show/Hide 8 Cylinder Cars", value = TRUE),
        ),
        mainPanel(
            h4("Steps:"),
            h5("1. Select the number of cylinders of the cars wanted on the side panel."),
            h5("2. Highlight the points (minimum 2) on the graph below to create a model for the 
               selected points. The slope and intercept of that model will be shown below."),
            plotOutput("plot1", brush = brushOpts(id = "brushIn")),
            h3("Slope of Model for Selected Points"),
            textOutput("slopeOut"),
            h3("Intercept of Model for Selected Points"),
            textOutput("intOut")
        )
    )
))
