# Selection by Comparisons

## Using emp.data with contents:

$ cat emp.data 
NAME    RATE    HOURS
Beth    4.00    0
Dan     3.75    0
Kathy   4.00    10
Mark    5.00    20
Mary    5.50    22
Susie   4.25    18

### RATE >=5

awk '$2>=5 {print}' emp.data
Mark    5.00    20
Mary    5.50    22


### Selection by Computation

awk '$2*$3>50 {printf("%.2f for %s\n", $2*$3, $1)}' emp.data
100.00 for Mark
121.00 for Mary
76.50 for Susie

#### without Comparisons

awk  '{printf("%.2f for %s\n", $2*$3, $1)}' emp.data
0.00 for Beth
0.00 for Dan
40.00 for Kathy
100.00 for Mark
121.00 for Mary
76.50 for Susie

### Selection by text

awk '$1 == "Susie" {print}' emp.data
Susie   4.25    18

### Combininig patters

awk '$2>=4 || $3>=20 {print}' emp.data
Beth    4.00    0
Kathy   4.00    10
Mark    5.00    20
Mary    5.50    22
Susie   4.25    18

awk '$2>=4 && $3>=20 {print}' emp.data
Mark    5.00    20
Mary    5.50    22

awk '!($2>=4 && $3>=20) {print}' emp.data
Beth    4.00    0
Dan     3.75    0
Kathy   4.00    10
Susie   4.25    18

## Data validation

awk 'NF != 4 {print "Line", NR, $0, "NF=", NF, "NF !=4"}' emp.data
Line 1 Beth     4.00    0 NF= 3 NF !=4
Line 2 Dan      3.75    0 NF= 3 NF !=4
Line 3 Kathy    4.00    10 NF= 3 NF !=4
Line 4 Mark     5.00    20 NF= 3 NF !=4
Line 5 Mary     5.50    22 NF= 3 NF !=4
Line 6 Susie    4.25    18 NF= 3 NF !=4




awk '!($3>=20) {print}' emp.data
Beth    4.00    0
Dan     3.75    0
Kathy   4.00    10
Susie   4.25    18