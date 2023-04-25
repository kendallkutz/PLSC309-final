# PLSC309-final

Import Dataset

Checkpoint3 <- read_excel("~/Downloads/Checkpoint3.xlsx")
View(Checkpoint3)
FemaleLed<- subset(Checkpoint3, Checkpoint3$`Female Leader`== 1)
MaleLed<-subset(Checkpoint3, Checkpoint3$`Female Leader`== 0)

Descriptive statistics

mean(FemaleLed$`Militarization (2021) (% of gov expenditures)`, na.rm=TRUE)
median(FemaleLed$`Militarization (2021) (% of gov expenditures)`, na.rm=TRUE)
median(MaleLed$`Militarization (2021) (% of gov expenditures)`, na.rm=TRUE)
mean(MaleLed$`Militarization (2021) (% of gov expenditures)`, na.rm=TRUE)

Correlates Test

cor.test(Checkpoint3$`Female Leader`, Checkpoint3$`Militarization (2021) (% of gov expenditures)`)
cor.test(Checkpoint3$`Proportion of Seats Held by Women in National Parliament (%)`, Checkpoint3$`Militarization (2021) (% of gov expenditures)`)

Visualization (Scatterplot)

plot(Checkpoint3$`Militarization (2021) (as a % of GDP)`, Checkpoint3$`Proportion of Seats Held by Women in National Parliament (%)`, xlab= "Militarization (as a % of GDP)", ylab= "Proportion of Seats Held by Women in National Parliament (%)", main= "Figure 1: Militarization (as a % of GDP) vs. Female Rep in National Parliament")


Linear Regression

Model1 <- lm(formula= Checkpoint3$`Female Leader`~Checkpoint3$`Militarization (2021) (% of gov expenditures)`+ Checkpoint3$`Proportion of Seats Held by Women in National Parliament (%)`+ Checkpoint3$`Militarization (2021) (as a % of GDP)`+ Checkpoint3$`Armed Forces Personnel (% of total labor force)`)
summary(model1)
Model2 <- lm(formula= Checkpoint3$`Proportion of Seats Held by Women in National Parliament (%)`~Checkpoint3$`Militarization (2021) (% of gov expenditures)`+ Checkpoint3$`Female Leader`+ Checkpoint3$`Militarization (2021) (as a % of GDP)`+ Checkpoint3$`Armed Forces Personnel (% of total labor force)`)
library(stargazer)
stargazer(Model1, Model2, type= "html", title= "Female-Led Countries and Militarization", dep.var.labels="Female-Led Countries", "Female Representation", out= "Female Leadership & Militarization.html")
