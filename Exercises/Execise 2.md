# Test Case Design Study Point Excercises
#### Hand In by Dennis Rønnebæk

### EQUIVALENCE PARTITIONING
#### 1. Make equivalences classes for the input variable for this method that accepts the numbers 1 ‐ 1000:  
  ```public boolean isEven(int n)```

| < 1     | 1-1000(Even numbers) | 1-1000(Uneven numbers) | > 1000  |
| ------- | -------------------- | ---------------------- | ------- |
| Invalid | True                 | False                  | Invalid |

#### 2. Make equivalences classes for an input variable that represents a mortgage applicant’s salary. The valid range is 1,000 pr. month to 75,000 pr. month

| < 1000  | 1000-75.000 | > 75.000 |
| ------- | ----------- | -------- |
| Invalid | valid       | invalid  |
#### 3. Make equivalences classes for the input variables for this method
```public static int getNumDaysinMonth(int month, int year)```
For month:
 < 1			1-12  		 > 12     
For year

< 1    		1-9999  		> 9999 


### BOUNDARY VALUE ANALYSIS
#### 1. Do boundary value analysis for equivalence partitioning exercise 1

| 0       | 1            | 2           | 999           | 1000         | 1001    |
| ------- | ------------ | ----------- | ------------- | ------------ | ------- |
| Invalid | Lowest false | Lowest true | Highest false | Highest true | Invalid |
#### 2. Do boundary value analysis for equivalence partitioning exercise 2
  999.99			1000		75.000		75.000,01
  (In the case that decimal values are valid)

#### 3. Do boundary value analysis for equivalence partitioning exercise 3
**For months**

| 0       | 1     | 12    | 13      |
| ------- | ----- | ----- | ------- |
| Invalid | Valid | Valid | Invalid |

**For years**

| 0       | 1     | 9.999 | 10.000  |
| ------- | ----- | ----- | ------- |
| Invalid | Valid | Valid | Invalid |

  (In the case that C# DateTime is being used)


### DECISION TABLES
#### 1. Make a decision table for the following business case:
No charges are reimbursed (DK: refunderet) to a patient until the deductible (DK: selvrisiko) has been met. After the deductible has been met, reimburse 50% for Doctor's Office visits or 80% for Hospital visits.

| Conditions:                      |      |      |      |
| -------------------------------- | ---- | ---- | ---- |
| Deductible met (hospital visit)  | N    | N    | Y    |
| Deductible met (doctor visit)    | N    | Y    | N    |
| **Actions:**                     |      |      |      |
| Do not reimburse                 | X    |      |      |
| Reimburse 50% for doctors visit  |      | X    |      |
| Reimburse 80% for hospital visit |      |      | X    |


#### 2. Make a decision table for leap years.
Leap year: Most years that are evenly divisible by 4 are leap years.
An exception to this rule is, that years that are evenly divisible by 100 are not leap years, unless they are also evenly divisible by 400, in which case they are leap years.

| Conditions:        |      |      |      |      |
| ------------------ | ---- | ---- | ---- | ---- |
| Dividable by 4     | Y    | Y    | Y    | N    |
| Dividable by 100   | N    | Y    | Y    | N    |
| Dividable by 400   | N    | N    | Y    | N    |
| **Actions:**       |      |      |      |      |
| Not leap year      |      | X    |      | X    |
| Possible leap year | X    |      |      |      |
| Leap year          |      |      | X    |      |
