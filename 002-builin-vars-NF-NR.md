# Builtin Variables 

## Using emp.data with contents:

$ cat emp.data 
NAME    RATE    HOURS
Beth    4.00    0
Dan     3.75    0
Kathy   4.00    10
Mark    5.00    20
Mary    5.50    22
Susie   4.25    18

## Builtin variable  NF number of fields (columns)

### print NF for each line

awk '{print NF}' emp.data
3
3
3
3
3
3

### print $NF - aka last field

awk '{print $NF}' emp.data
0
0
10
20
22
18

### print NF, NAME and last field

awk '{print NF, $1, $NF}' emp.data
3 Beth 0
3 Dan 0
3 Kathy 10
3 Mark 20
3 Mary 22
3 Susie 18

## LN Line Numbers

### Print line number for each line

awk '{print NR}' emp.data
1
2
3
4
5
6

### print the line number and line contents

awk '{print NR, $0}' emp.data
1 Beth  4.00    0
2 Dan   3.75    0
3 Kathy 4.00    10
4 Mark  5.00    20
5 Mary  5.50    22
6 Susie 4.25    18

