# Fancier outputs with printf

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

### printf format
- NAME as string (%s) with wide 8 (%8s) justified left (%-8s)
- RATE*HOURS with $ as number (float) (%f) with 2 decimals  (%.2f) with wide 6 (%6.2f)

```bash
awk '{printf("%-8s $%6.2f \n", $1, $2*$3)}' emp.data
```

```
Beth     $  0.00 
Dan      $  0.00 
Kathy    $ 40.00 
Mark     $100.00 
Mary     $121.00 
Susie    $ 76.50 
```

### %d decimal integer

```bash
awk '{printf("%d \n", $2)}' emp.data
```

```
4 
3 
4 
5 
5 
4 
```

### %c ASCII char

```bash
awk '{printf("%d %c \n", NR, $1)}' emp.data
```

```
1 B 
2 D 
3 K 
4 M 
5 M 
6 S 
```

```bash
awk '{printf("%d %c \n", NR, $2)}' emp.data
```

```
1  
2  
3  
4  
5  
6   
```

### 5 wide %5d

```bash
awk '{printf("%5d \n", $2)}' emp.data
```
```
    4 
    3 
    4 
    5 
    5 
    4 
```

### 2 wide %2d

```bash
awk '{printf("%2d \n", $2)}' emp.data
```

```
 4 
 3 
 4 
 5 
 5 
 4 
```

### cientific notation %e

```bash
awk '{printf("%2e \n", $2)}' emp.data
```

```
4.000000e+00 
3.750000e+00 
4.000000e+00 
5.000000e+00 
5.500000e+00 
4.250000e+00 
```

### real  %f

```bash
awk '{printf("%f \n", $2)}' emp.data
```

```
4.000000 
3.750000 
4.000000 
5.000000 
5.500000 
4.250000 
```

### shorter of %e or %f

```bash
awk '{printf("%g \n", $2)}' emp.data
```

```
4 
3.75 
4 
5 
5.5 
4.25 
```

```bash
awk '{printf("%g \n", $2*$3)}' emp.data
```

```
0 
0 
40 
100 
121 
76.5 
```

### unsigned octal

```bash
awk '{printf("%o \n", $2)}' emp.data
```

```
4 
3 
4 
5 
5 
4 
```

```bash
awk '{printf("%o \n", $2*$3)}' emp.data
```

```
0 
0 
50 
144 
171 
114 
```

### string %s

```bash
awk '{printf("%s %s \n", $1, $2)}' emp.data
```
```
Beth 4.00 
Dan 3.75 
Kathy 4.00 
Mark 5.00 
Mary 5.50 
Susie 4.25 
```

```bash
awk '{printf("%s %s \n", $1, $2*$3)}' emp.data
```

```
Beth 0 
Dan 0 
Kathy 40 
Mark 100 
Mary 121 
Susie 76.5 
```

### unsigned hex %x

```bash
awk '{printf("%x \n", $2)}' emp.data
```

```
4 
3 
4 
5 
5 
4 
```

```bash
awk '{printf("%x \n", $2*$3)}' emp.data
```

```
0 
0 
28 
64 
79 
4c 
```
