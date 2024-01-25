Read After Write (RAW) dependency/hazard
~~~
# SUB and AND depend on ADD
# read x1 after write x1
add x1, x1, x1
sub x4, x1, x5
and x6, x1, x7
~~~

data headers on exam