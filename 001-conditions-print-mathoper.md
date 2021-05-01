# awk tutorial

## Using emp.data with contents:

```bash
$ cat emp.data 
```

```
NAME    RATE    HOURS
Beth    4.00    0
Dan     3.75    0
Kathy   4.00    10
Mark    5.00    20
Mary    5.50    22
Susie   4.25    18
```

## Basics: 
- conditions
- fields
- math operations
- adding outside text

### if HOURS>0 print NAME RATE*HOURS

```bash
awk '$3 > 0 {print $1, $2 * $3}' emp.data
```

```
Kathy 40
Mark 100
Mary 121
Susie 76.5
```

### if HOURS==0 print NAME

```bash
awk '$3==0 {print $1}' emp.data
```

```
Beth
Dan
```

### just print

```bash
awk '{print}' emp.data 
```

```
Beth    4.00    0
Dan     3.75    0
Kathy   4.00    10
Mark    5.00    20
Mary    5.50    22
Susie   4.25    18
```

### $0 means all columns

```bash
awk '{print $0}' emp.data 
```

```
Beth    4.00    0
Dan     3.75    0
Kathy   4.00    10
Mark    5.00    20
Mary    5.50    22
Susie   4.25    18
```

### Adding text

Spaces are automatically added:

```bash
awk '{print "Employee", $1, "Rate:", $2, "Hours:", $3}' emp.data
```

```
Employee Beth Rate: 4.00 Hours: 0
Employee Dan Rate: 3.75 Hours: 0
Employee Kathy Rate: 4.00 Hours: 10
Employee Mark Rate: 5.00 Hours: 20
Employee Mary Rate: 5.50 Hours: 22
Employee Susie Rate: 4.25 Hours: 18
```
