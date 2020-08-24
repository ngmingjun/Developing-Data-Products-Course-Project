library(shiny)
data(mtcars)

shinyServer(function(input, output) {
    model <- reactive({
        if(isTRUE(input$show4cyl)){
            data4 <- mtcars[mtcars$cyl == 4,]
        } else {
            data4 <- NULL
        }
        if(isTRUE(input$show6cyl)){
            data6 <- mtcars[mtcars$cyl == 6,]
        } else {
            data6 <- NULL
        }
        if(isTRUE(input$show8cyl)){
            data8 <- mtcars[mtcars$cyl == 8,]
        } else {
            data8 <- NULL
        }       
        dataC <- rbind(data4, data6, data8)
        brushed_data <- brushedPoints(dataC, input$brushIn, xvar = "hp", yvar = "mpg")
        if(nrow(brushed_data) < 2){
            return(NULL)
        }
        lm(mpg ~ hp, data = brushed_data)
    })
    output$slopeOut <- renderText({
        if(is.null(model())){
            "No Model Found" 
        } else {
            model()[[1]][2]
        }
    })
    output$intOut <- renderText({
        if(is.null(model())){
            "No Model Found"
        } else {
            model()[[1]][1]
        }
    })
    output$plot1 <- renderPlot({
        if(isTRUE(input$show4cyl)){
            data4 <- mtcars[mtcars$cyl == 4,]
        } else {
            data4 <- NULL
        }
        if(isTRUE(input$show6cyl)){
            data6 <- mtcars[mtcars$cyl == 6,]
        } else {
            data6 <- NULL
        }
        if(isTRUE(input$show8cyl)){
            data8 <- mtcars[mtcars$cyl == 8,]
        } else {
            data8 <- NULL
        }
        dataC <- rbind(data4, data6, data8)
        plot(x = dataC$hp, y = dataC$mpg, xlab = "Horsepower", ylab = "MPG", 
             main = "Horsepower against MPG", col = dataC$cyl, pch = 16, 
             xlim = c(50, 350), ylim = c(10, 35))
        legend("topright", legend = c("4 Cylinder", "6 Cylinder", "8 Cylinder"), 
               col = c("blue", "purple", "grey"), pch = 16)
        if(!is.null(model())){
            abline(model(), col = "red", lwd = 2)
        } 
    })
})
