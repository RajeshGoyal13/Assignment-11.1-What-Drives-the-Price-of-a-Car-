# Assignment-11.1-What-Drives-the-Price-of-a-Car
## Business Understanding:
The goal of this assignent is to find what are the factors which determine the price of the car. Based on the historical data of car purchase, one need to create a model which will help in finding out the factors which play critical role in the price.

## Data Understanding:

The first step for this assignemnt was to understand the data. Looked into the attributes of the data. Most of the columns have non- numeric data. There are any columns which have null data also.

<img width="400" alt="Screenshot 2024-04-15 at 3 48 59 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/bf1028fb-8032-4426-a26b-b290a0667b8b">

Created various histograms to see how the data is scattered in the various categories.

<img width="999" alt="Screenshot 2024-04-15 at 4 17 25 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/89c5b746-4bb4-424b-9c05-0bee4ada05f3">

<img width="984" alt="Screenshot 2024-04-15 at 4 17 46 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/6002cc92-d6ad-4856-bd2c-cb54284f26b9">

There were many columns which have same value "Other". So changed the value "Other" as per the feature columns.
<img width="618" alt="Screenshot 2024-04-15 at 5 30 54 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/ab681f5a-cc4e-4ca0-a78e-3d8d23c429c0">

## Data Preperation:

Data preperation is one of the critical step in this framework, as if the data is not proper, model will not predict with accuracy. So, first of all, removed the null values. After removing the null values, checked if there are any duplicates in the data.
<img width="984" alt="Screenshot 2024-04-15 at 4 18 02 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/6b86343a-3109-48d4-be9b-9dfec93ec9da">
Next step was to check if there are any outliers in the data. Created the histogram for Price, Year and Odometer. It shows that there are some outliers. 

<img width="350" alt="Screenshot 2024-04-15 at 4 22 29 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/6720d412-6f66-40d4-88b1-81d7a205f669">
<img width="300" alt="Screenshot 2024-04-15 at 4 23 54 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/531cb4e4-61d3-40e9-8d79-ced0183dbc86">
<img width="300" alt="Screenshot 2024-04-15 at 4 24 04 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/750d845c-6fb9-42f2-982f-60891bde6d97">

So, used the quartile method, to remove the outliers. After removing the outliers, histograms look like:
<img width="314" alt="Screenshot 2024-04-15 at 4 32 52 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/580e6115-7a49-4234-8ac5-b9cf7eec7c2f">
<img width="314" alt="Screenshot 2024-04-15 at 4 33 05 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/291d2586-810b-4092-abcc-5906a5941175">
<img width="314" alt="Screenshot 2024-04-15 at 4 33 16 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/1c66ad7b-7458-477d-b418-4959cae7e5b8">

Also, Dropped some of the columns - 'id', 'region', 'title_status', 'VIN','state','model'. Next step was to convert non numeric data into Numeric. OneHotEncoder was used to convert the data into numeric. Get dummies code was used on columns - 'cylinders', 'transmission', 'condition', 'manufacturer','paint_color', 'fuel'. It created a new column with values 0 and 1 for each non numeric unique value.
<img width="998" alt="Screenshot 2024-04-15 at 4 38 46 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/d9ea98b2-6445-44f2-b0b2-e7bec852cbd7">

## Modeling:
Once the data set is ready. Next step is to create models. First of all, I calculated permutation importance. It helped to understand which features/ columns are more important than others. Looking at it, it helps to drop some of the coulmns which do not have importance. Looking at the below list, it shows that Year, Odometer, 8 Cylinders, Diesel fuel, 4 cylinders are more imporant features in the price of the car.

<img width="321" alt="Screenshot 2024-04-15 at 4 41 28 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/9749f671-f8b7-4c97-8d68-953fb8442f0b">

There are 74 unique columns, which play an important role.So, for modeling used all these 74 columns.
Created three different models: Sequential Feature selector, Ridge Regression and Ordinary Least square models. For each model, created the pipeline and determine Mean Squared Error(MSE) & R2 Score. The GridSearchCV function helped to find the hyper-parameter n_features_to_select. Cross validation by 5 splits. Determined the factots important for each model. 

<img width="300" alt="Screenshot 2024-04-15 at 4 51 51 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/cc71a64a-7c6d-4634-b29d-5acab26718b5">
<img width="350" alt="Screenshot 2024-04-15 at 4 52 30 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/e27ca065-24eb-4a69-af9c-ce2113b66a32">
<img width="350" alt="Screenshot 2024-04-15 at 4 52 44 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/d2414543-48aa-4ca3-9b1c-f873c0e64f34">

Here are the co-efficients and factors found by each model:

<img width="300" alt="Screenshot 2024-04-15 at 5 03 49 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/98fb6c74-b388-4085-806d-8c2e7a386d41">
<img width="300" alt="Screenshot 2024-04-15 at 5 04 51 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/7018ee13-0a78-4b74-84d2-ead91f74a02c">
<img width="300" alt="Screenshot 2024-04-15 at 5 06 08 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/427fdeb9-edab-4152-9b8c-bdc2b2a9cfb2">

For eaach model, Cross validation was done by using the below code:
<img width="1005" alt="Screenshot 2024-04-15 at 5 10 35 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/8c5ef6fa-051a-44a7-bf26-f4f900f7f7f3">

## Evaluation:

Evaluated the MSE and R2 score of each module. Here is the comparison of the three models.

<img width="395" alt="Screenshot 2024-04-15 at 5 11 35 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/b798ead3-9f66-45b0-a13e-e870ba8b2b15"><img width="395" alt="Screenshot 2024-04-15 at 5 11 49 PM" src="https://github.com/RajeshGoyal13/Assignment-11.1-What-Drives-the-Price-of-a-Car-/assets/161057282/7e0b27fe-a148-4705-9f4a-40b589e96a75">


## Next steps and recommendations
1. Based on these models, it clearly shows that Year and Odometer reading play crtical role in the price of the car.
2. No. of Cylinders and the Manufacturer also are important in the price ofr the car. Cars with Cylinders 10, 5, 3 are more valuable. Similarly manyfacturer Acura, Benz, Jaugar are more prominent in the price of the car.
3. Some of the features like Drive, Paint color, Title have null values.So, for better understanding, may be data has to be collected for these.
4. Many coulmns have one of the value "Other". As per Ridge model, in cyclinders "Other" was impacting the price. This model got impact because of this Other value.
5. Model colulmn has lots of unique values. have to drop this column as it was creating more than 50 columns in the data set.
6. In this analysis, columns -  'id', 'region', 'title_status', 'VIN','state','model' were not used for analysis. As it was creating lots of data set. For further analysis, these columns can be used.
