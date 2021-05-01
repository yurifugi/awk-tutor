# BEGIN and END

## Using emp.data with contents:

$ cat emp.data 
Beth    4.00    0
Dan     3.75    0
Kathy   4.00    10
Mark    5.00    20
Mary    5.50    22
Susie   4.25    18

NAME    RATE    HOURS

### BEGIN

yuri@S500CA:~/Desktop/awk-tutor$ awk 'BEGIN {print "NAME       RATE      HOURS"; print "" } {print }' emp.data
NAME       RATE      HOURS

Beth    4.00    0
Dan     3.75    0
Kathy   4.00    10
Mark    5.00    20
Mary    5.50    22
Susie   4.25    18

awk '{print "NAME       RATE      HOURS"; print "" } {print }' emp.data
NAME       RATE      HOURS

Beth    4.00    0
NAME       RATE      HOURS

Dan     3.75    0
NAME       RATE      HOURS

Kathy   4.00    10
NAME       RATE      HOURS

Mark    5.00    20
NAME       RATE      HOURS

Mary    5.50    22
NAME       RATE      HOURS

Susie   4.25    18


### END

awk '$3>15 {emp=emp+1} END {print emp, "employees worked more than 15h"}' emp.data
3 employees worked more than 15h


### Computing


awk '{ pay = pay + $2 * $3 }
    END { print NR, "employees"
    print "total pay is", pay
    print "average pay is", pay/NR
}' emp.data

6 employees
total pay is 337.5
average pay is 56.25

### what?
awk '$2 > maxrate { maxrate = $2; maxemp = $1 }
END { print "highest hourly rate:", maxrate, "for", maxemp }' emp.data 
highest hourly rate: 5.50 for Mary

### String concatenation

awk '{ names = names $1 " " } \
    END { print names }' emp.data
Beth Dan Kathy Mark Mary Susie 

