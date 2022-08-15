# Importing-all-types-of-data-in-R-programming


# Importing a csv file 

library(tidyverse)
## Chicago Restaurant inspection file
inspections <- read_csv("inspections.csv")
inspections


### Since the same data can also be found on the internet, we can also import it 
inspections <- read_csv('http://594442.youcanlearnit.net/inspections.csv')

### looking at the content of the data by using the glimpse command
glimpse(inspections)

### Using your own names for the columns 

names <- c('ID', 'DBName', 'AKName', 'License', 'FacilityType', 'Address', 
           'City', 'State', 'ZipCode', 'InspectionDate', 'InspectionType', 
           'Results', 'Violations', 'Latitute', 'Longitude', 'Location') 

### Supplying this to the new inspection data 
inspections <- read_csv('http://594442.youcanlearnit.net/inspections.csv', 
                        col_names = names)

glimpse(inspections) 
### you can see that all the variable names can be seen in the first line
### so we use the skip command to remove the first column or variable
inspections <- read_csv('http://594442.youcanlearnit.net/inspections.csv', 
                        col_names = names, skip = 1)

glimpse(inspections)




# Importing excel files into R programming ### 

library(tidyverse)
library(readxl)
### Reading the dataset (School Breakfast program Participation and Meals served)

breakfast <- read_excel('breakfast.xlsx')

### looking at the content of the data by using the glimpse command
glimpse(breakfast)

### you can see that all the variable name can found in fouth line
### so we use the skip command to remove the first 3  columns or variables

breakfast <- read_excel('breakfast.xlsx', skip = 3)
glimpse(breakfast)
view(breakfast) 

### After viewing the data, you realized that the second line is messed up so clean the data 

names <- c('Year', 'FreeStudents', 'ReducedStudents', 'PaidStudents', 'Totalstudents', 
           'MealsServed', 'PercentageFree')
breakfast <- read_excel('breakfast.xlsx', skip = 5, col_names = names)
glimpse(breakfast)
view(breakfast)

### Remember the dataset was in million so we use the mutate command to do that 
breakfast <- breakfast %>%
  mutate( FreeStudents = FreeStudents *1000000,
          ReducedStudents = ReducedStudents * 1000000,
          PaidStudents = PaidStudents * 1000000,
          Totalstudents = Totalstudents * 1000000,
          MealsServed = MealsServed * 1000000,
          PercentageFree = PercentageFree / 100)

glimpse(breakfast)
view(breakfast)































# Importing a TSV file  (Top separated values)

library(tidyverse)

### US government Center for Medicare and Medicaid services

### Reading the data  
inpatient <- read_tsv("inpatient.tsv")
glimpse(inpatient)

### Since the same data can also be found on the internet, we can also import it
inpatient <- read_tsv('http://594442.youcanlearnit.net/inpatient.tsv')
glimpse(inpatient)


### Using your own names for the columns 
names <- c('DRG', 'ProviderID', 'Name','Address', 'City', 'State', 'ZipCode',
           'Region', 'Discharges', 'AverageCharges', 'AverageTotalPayments', 
           'AverageMedicarePayments')

### Supplying this to the new inspection data 
inpatient <- read_tsv('http://594442.youcanlearnit.net/inpatient.tsv', 
                      col_names = names)
glimpse(inpatient)
### you can see that all the variable names can be seen in the first line
### so we use the skip command to remove the first column or variable
inpatient <- read_tsv('http://594442.youcanlearnit.net/inpatient.tsv', 
                      col_names = names, skip = 1)
glimpse(inpatient)

#### Making some of data integers and some characters and some numerics
### you can make some as factors(f)

types <- 'ccccccccinnn'

### Supplying this to the new  data 
inpatient <- read_tsv('http://594442.youcanlearnit.net/inpatient.tsv', 
                      col_names = names, skip = 1, col_types = types)

glimpse(inpatient)







# Importing a text delimited files (txt) in R programming 

library(tidyverse)

### Work stoppages in the United States 
stoppages <- read_delim('http://594442.youcanlearnit.net/workstoppages.txt', delim = '^')

glimpse(stoppages)


### you can also use the delim function to read both csv and tsv file 
###From the previous example, reading the inspections csv file with delim function

inspections <- read_delim('http://594442.youcanlearnit.net/inspections.csv',
                          delim = ',')
glimpse(inspections)

###From the previous example, reading the tsv file with delim function
inpatient <- read_delim('http://594442.youcanlearnit.net/inpatient.tsv', 
                        delim = '\t')
glimpse(inpatient)







# Importing a Fixed- with- files into R programming 

library(tidyverse)

### Salaries of City of Chicago  employees

### Reading the data 

### reading the names
### Using your own names for the columns 
names <- c('Name', 'Title', 'Department', 'Salary')

### Telling the charater for each column
length <- c(32, 50, 24, NA)

width <- fwf_widths(length, names)

employees <- read_fwf('http://594442.youcanlearnit.net/chicagoemployees.txt', 
                      width)

glimpse(employees)

### you can see that all the variable names can be seen in the first line
### so we use the skip command to remove the first column or variable
employees <- read_fwf('http://594442.youcanlearnit.net/chicagoemployees.txt', 
                      width, skip = 1)
view(employees)

glimpse(employees)







