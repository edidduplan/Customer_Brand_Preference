install.packages("pacman")
install.packages("matrixStats")
install.packages("C50", dependencies = T)

pacman::p_load(caret, tidyverse, readr, party, ggthemes, plotly, shiny, C50)
pacman::p_load(C50)
library(party)
library(party)
library(C50)


setwd("C:/Users/edison/Documents/Ubiqum/Data Analytics Course/Module II/Task2_revisited/")

# Import data

CompleteResponses <- read.csv(file="Data/CompleteResponses.csv", header=TRUE, sep=";")

SurveyIncomplete <- read.csv(file="Data/SurveyIncomplete.csv", header=TRUE, sep=",")


# Pre-processing
CompleteResponses$age <- as.integer(CompleteResponses$age)
CompleteResponses$elevel <- as.ordered(CompleteResponses$elevel)
CompleteResponses$car <- as.factor(CompleteResponses$car)
CompleteResponses$zipcode <- as.factor(CompleteResponses$zipcode)
CompleteResponses$brand <- as.character(CompleteResponses$brand)

head(CompleteResponses$brand == 0)

CompleteResponses[which(CompleteResponses$brand == 0), "brand"] <- "Acer"
CompleteResponses[which(CompleteResponses$brand == 1), "brand"] <- "Sony"
CompleteResponses$brand <- as.factor(CompleteResponses$brand)

str(CompleteResponses)

SurveyIncomplete$salary <- as.numeric(SurveyIncomplete$salary)
SurveyIncomplete$age <- as.integer(SurveyIncomplete$age)
SurveyIncomplete$elevel <- as.ordered(SurveyIncomplete$elevel)
SurveyIncomplete$car <- as.factor(SurveyIncomplete$car)
SurveyIncomplete$zipcode <- as.factor(SurveyIncomplete$zipcode)
SurveyIncomplete$credit <- as.numeric(SurveyIncomplete$credit)

str(SurveyIncomplete)

# Exploring the data

# Histograms
# Hist salary
ggplot(CompleteResponses, aes(x = salary, fill = brand)) + 
  geom_histogram(binwidth = 10000, 
                 color = "white") + 
  ggtitle("Histogram CompleteResponse - Salary") + 
#  scale_fill_manual(values = c("grey", "black")) + 
#  facet_grid(elevel ~ zipcode, labeller = label_both) +
  facet_grid(. ~ elevel, labeller = label_both)

ggplot(SurveyIncomplete, aes(x = salary)) + geom_histogram(binwidth = 10000, color = "white") + ggtitle("Histogram SurveyIncomplete - Salary")

# Hist age
ggplot(CompleteResponses, aes(x = age)) + geom_histogram(binwidth = 5, color = "white") + ggtitle("Histogram CompleteResponse - age")
ggplot(SurveyIncomplete, aes(x = age)) + geom_histogram(binwidth = 5, color = "white") + ggtitle("Histogram SurveyIncomplete - age")

# Hist elevel
CompleteResponses$elevel <- as.integer(CompleteResponses$elevel)
SurveyIncomplete$elevel <- as.integer(SurveyIncomplete$elevel)

ggplot(CompleteResponses, aes(x = elevel, fill = brand)) + 
  geom_histogram(binwidth = 1, color = "white") + ggtitle("Histogram CompleteResponse - education level")

ggplot(SurveyIncomplete, aes(x = elevel)) + geom_histogram(binwidth = 1, color = "white") + ggtitle("Histogram SurveyIncomplete - education level")

CompleteResponses$elevel <- as.ordered(CompleteResponses$elevel)
SurveyIncomplete$elevel <- as.ordered(SurveyIncomplete$elevel)

# Hist car
CompleteResponses$car <- as.integer(CompleteResponses$car)
SurveyIncomplete$car <- as.integer(SurveyIncomplete$car)

ggplot(CompleteResponses, aes(x = car, color = brand)) + geom_histogram(binwidth = 1, fill = "white") + ggtitle("Histogram CompleteResponse - car")
ggplot(SurveyIncomplete, aes(x = car)) + geom_histogram(binwidth = 1, color = "white") + ggtitle("Histogram SurveyIncomplete - car")

CompleteResponses$car <- as.factor(CompleteResponses$car)
SurveyIncomplete$car <- as.factor(SurveyIncomplete$car)

# Hist zipcode
CompleteResponses$zipcode <- as.integer(CompleteResponses$zipcode)
SurveyIncomplete$zipcode <- as.integer(SurveyIncomplete$zipcode)

ggplot(CompleteResponses, aes(x = zipcode, color = brand)) + geom_histogram(banwidth = 1, fill = "white") + ggtitle("Histogram CompleteResponse - zipcode")
ggplot(CompleteResponses, aes(x = zipcode, color = brand)) + geom_bar(banwidth = 1, fill = "white") + ggtitle("Histogram CompleteResponse - zipcode")
ggplot(SurveyIncomplete, aes(x = zipcode)) + geom_histogram(banwidth = 1, color = "white") + ggtitle("Histogram SurveyIncomplete - zipcode")

CompleteResponses$zipcode <- as.factor(CompleteResponses$zipcode)
SurveyIncomplete$zipcode <- as.factor(SurveyIncomplete$zipcode)

# Hist credit
ggplot(CompleteResponses, aes(x = credit, color = brand)) + geom_histogram(binwidth = 50000, fill = "white") + ggtitle("Histogram CompleteResponse - credit")
ggplot(SurveyIncomplete, aes(x = credit)) + geom_histogram(binwidth = 50000, color = "white") + ggtitle("Histogram SurveyIncomplete - credit")

str(CompleteResponses$car)

summary(CompleteResponses$age)

hist(CompleteResponses$salary[which(CompleteResponses$age == 20)], breaks = 13)

ggplot(CompleteResponses, aes(x = age, color = brand)) + geom_histogram(binwidth = 5, fill = "white") + ggtitle("Histogram CompleteResponse - age")
ggplot(SurveyIncomplete, aes(x = age)) + geom_histogram(binwidth = 5, color = "white") + ggtitle("Histogram SurveyIncomplete - age")


# Scatter plots
ggplot(CompleteResponses, aes(x = age, y = salary, color = brand)) + 
  geom_point() + geom_smooth()

ggplot(CompleteResponses, aes(x = age, y = credit, color = brand)) + geom_point()
str(CompleteResponses$brand)

ggplot(CompleteResponses, aes(x = elevel, y = salary, color = brand)) + geom_point(position = "jitter")

ggplot(CompleteResponses, aes(x = car, y = salary, color = brand)) + geom_point(position = "jitter")

ggplot(CompleteResponses, aes(x = zipcode, y = salary, color = brand)) + geom_point(position = "jitter")

ggplot(CompleteResponses, 
       aes(x = credit, 
           y = salary, 
           color = brand)) +
  geom_point()

ggplot(CompleteResponses, aes(brand, fill = brand)) + geom_bar(color = "black")

ggplot(CompleteResponses, aes(x = brand, fill = brand)) + 
  geom_bar() +  theme_economist()
# coord_polar("y", start = 0) +
# Boxplots

ggplot(CompleteResponses, aes(x = brand, y = salary, 
                              fill = brand)) + 
  geom_boxplot() + 
  stat_summary(fun.y = median, color = "white", geom = "text",
               vjust = -0.7, 
               aes(label = round(..y.., digits = 1)))

# Plot_ly

P <- plot_ly(CompleteResponses, x = ~ salary, color = ~brand)
P

# Feature selection through Decision Tree
set.seed(123)
DecisionTree_brand <- ctree(brand ~ ., data = CompleteResponses, controls = ctree_control(maxdepth = 3))
plot(DecisionTree_brand)

# Training /testing sets

trainSize <- createDataPartition(y=CompleteResponses$brand, p = .75, list = F)

trainSize
view(trainSize)
str[trainSize]
attributes(trainSize)

trainSet <- CompleteResponses[trainSize,]
testSet <- CompleteResponses[-trainSize,]

nrow(trainSet)


ctrl <- trainControl(method = "repeatedcv", 
                     repeats = 3,
                     classProbs = T,
                     summaryFunction = twoClassSummary)

# Automatic tunning
modelo_c50_auto <- train(brand ~ ., 
                data = trainSet, 
                method = "C5.0",
                tuneLength = 2,
                trControl = ctrl,
                metric = "ROC",
                preProc = c("center", "scale"))
modelo_c50_auto
plot(modelo_c50_auto)

predict_c50_auto_classes <- predict(modelo_c50_auto, newdata = testSet)
predict_c50_auto_classes
head(predict_c50_auto_classes)
str(predict_c50_auto_classes)

predict_c50_auto_prob <- predict(modelo_c50_auto, newdata = testSet, type = "prob")
head(predict_c50_auto_prob)
str(predict_c50_auto_prob)

testSet_predic <- cbind(testSet, predict_c50_auto_classes, predict_c50_auto_prob)

confusionMatrix(data = predict_c50_auto_classes, testSet$brand)

# Manual tunning
modelo_c50_man <- train(brand ~ ., 
                        data = trainSet, 
                        method = "C5.0",
                        tuneGrid = data.frame(trials = 10, 
                                              model = c("rules", "tree"), 
                                              winnow = T),
                        trControl = ctrl,
                        metric = "ROC",
                        preProc = c("center", "scale"))
modelo_c50_man
plot(modelo_c50_man)

predict_c50_auto_classes <- predict(modelo_c50_auto, newdata = testSet)
predict_c50_auto_classes
head(predict_c50_auto_classes)
str(predict_c50_auto_classes)

varImp(modelo_c50_auto)
modelo_rf_man

