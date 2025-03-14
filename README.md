# Power-BI---Optimizing-Data-Model

This repository is to give a shout out to Bas for his amazing video about optimizing Data MOdels in Power BI.
This is the link to the vieo [https://www.youtube.com/watch?v=MGkCCbK86qw&t=495s](10 Steps to Optimize Your Data Model in Power BI).

### Step 1: Deleting unused Columns and tables in our Data Model.

- We can do that using the external tool called Bravo for Power BI.
  
- ![image](https://github.com/user-attachments/assets/6e72e960-b7d8-4549-b938-9bf2dc6e5ef0)

- Or we can use Power BI Helper.

- ![image](https://github.com/user-attachments/assets/c77454ce-a3d1-4bad-9116-5deca4d1958f)


### Step 2: Delete unused Rows

Aggeregate the Data to the level that we need, for the visualisations in our report.

- For example moving from this FctTable

![image](https://github.com/user-attachments/assets/1d153ca8-4354-4a52-9709-a11666524804)

- To this Aggregated FctTable_AGG

![image](https://github.com/user-attachments/assets/21a104e4-c260-4e74-a1f7-3687145889ae)


**PS:** BTW we can do that using the feature of Group BY present on Power Query.

### Step 3: Turn OFF AUTO Date/Time

You need to go to your Settings, Options and desactivate the AUTO Date/Time.

![image](https://github.com/user-attachments/assets/29b3d14f-d7b5-4ecf-8011-8d64c05e7d2e)


Because, this fonctionnality creates for every Data/Time Field a Date Table (We can visualise it on DAX Studio BTW), and whenever you see a date hierarchy on your Power BI Datas, this is a Local Date/Time.

![image](https://github.com/user-attachments/assets/37fce684-02fa-4903-b2ef-bb0f85635cd2)


![image](https://github.com/user-attachments/assets/59e40de1-2c96-4454-9b27-9633a6903e5c)


![image](https://github.com/user-attachments/assets/0f0dc787-33ae-400c-83e7-61299c9c923b)

It is visible in DAX Studio that these Date Tables take a quite space in our Data Model.


### Step 4: Always opt for a Star Schema Always.

Because, simply Power BI is optimized for Star Schemas.


### Step 5: Remove any 1:1 Relationship.

We can easily do that by merging queries in Power Query.

![image](https://github.com/user-attachments/assets/1c2fc049-f83f-4c26-9cb0-39aa99d0a4d9)

![image](https://github.com/user-attachments/assets/ae74b582-4e04-4cb1-9f7d-28d40b62a086)


### Step 6: Avoid using Many-to-Many Relationships and Bidirectional

Sometimes, we opt for the Bidirectional in order to propagate filters from a Dimensinon table to another one, passing by the Fact TABLE, but this is can slow down our data model, and it can also create some ambiguities.

Instead, to be able to filter a Dim table using a field of another Dim Table, the best way is to write a measure.

![image](https://github.com/user-attachments/assets/1b7b14f1-9aa7-4324-aa31-a470c645a438)


### Step 7: Reduce the Cardinality of our Columns

**Cardinality :** is the number of unique values in a column.

The less cardinality the slowest the data model is.

There is a commun best practice when it comes to reduce cardinality, is to separate the Date/Time Column into a Date and a Time Column.


![image](https://github.com/user-attachments/assets/530b5210-bee7-47dd-8608-e83501e0c03b)


![image](https://github.com/user-attachments/assets/97dd3b5a-647f-4857-8b38-3fdaae46e40a)


### Step 8: Make sure that the correct Data Type is assigned to each data field.

For example, we can have **Order_ID** stored in a Text formet, whereas we want it to be a numeric field.

**PS :** Btw, Text Data Type takes more place than a Numeric Data Type.


### Step 9: Avoid Using Calculated Columns / Table unless, it is compulsory.

Opt for measures than Calculed Columns.

### Step 10: Choosing between Import and Direct Query.

### Step 11: Choosign where to Compute the Calculated Column.

-  If you have access to the data source, for example, you can modify the SQL Server Database, you can ALTER your VIEW on the DataSource, by adding that column.
-  Else, you can create your calculated column in Power Query.
-  Or, at the end if you can't modify your Power Query, you can write DAX to create your calculated column (btw try to create it in the Dim Table instead of the Fact one).







































