---
sort: 11
---

# Taxonomy of data


```
<embed src="/assets/pdf/taxonomy_data.pdf" width="800px" height="600px" type="application/pdf" />    
```
![taxonomy of data](/assets/images/taxonomy_data.png)
Data types are separated into numerical and categorical.
- Numerical data is the data that we can make mathematical operations with. For example, heigh, weight, age. You can add one weight to the other. Height and age data can also be multiplied, substracted and so on. It makes sense to do mathematical operations with numerical data. Furthermore, numerical data can be separated into
    - Continious numerical data. Continious numerica data, is the numerical data that takes values in continious range. For example, height of the person can take value 171.2 cm, 183.4 cm, 166.4 cm. Height of the person can take any value in possible range.
    - Discrete numerical data is the type of data that takes only limited number of values. For example age of the person can take only values 1, 2, 3, ... etc. 

- Categorical data is the data that have categories. For example, car producer variable, could have levels such as Toyota, Mercedes, Honda. We can encode the levels using numbers, for example we can Encode Toyota as 1, Mercedes as 2 and Honda as 3. It does not make sense to do mathematical operations with categorical data. For example, if we have categorical variable gender, 1 is male and 0 is female. It does not make any sense to add male to female, or in other words add 1 to 0. Numbers in this case is just placeholders for categorical levels of our variable. Furthermore, We can subdivide categorical variables into 
    - Binary categorical variable, is such a variable that consists only of two levels. For example, whether person had heart attack or not, could be counted as dummy variable since it only has two levels. 
    - Ordinal categorical variable, is such a variable, levels of which has and inherent oreder. For example, weight of person could have potential levels: extremely underweight, underweight, normal, obese, extremely obese. We can see that in terms of weight outcomes extremely underweight is smaller that underweight, underweight is smaller that normal, etc etc.
    - Regular categorical variable, is such a variable that do not inherent order between levels of categories. For example, car manufacturer variable has levels such as Toyota, Honda, Hyundai, Ford. However this levels do not have natural order between them, in other words we can not sat that Toyota is better than Honda, or Ford is worse than Hyundai etc.

