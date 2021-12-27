## 1
path of interpreter that if smone use cshell or ... 
```
#!/bin/bash
```

### echo
```
echo "test"
ls 

echo "some cmnd $(pwd)"

out=$(pwd)
echo "sm cmd ${out}
```
variable 
```
name="LuckyLearn"
echo ${name}
echo ${name/J/j}    
echo ${name:0:2}   
echo ${name::2}     
echo ${name::-1}    
echo ${name:(-1)}   
echo ${name:(-2):1} 
```
## 2
bash input
#### Command line arguments
```
$# : number of arguments
$@ : all arguments
$0 : your bash file name
$$ : Process ID
$USER : The username of the user running the script.
$HOSTNAME : The hostname of the machine the script is running on.
$SECONDS : The number of seconds since the script was started.
$RANDOM : Returns a different random number each time is it referred to.
$LINENO - Returns the current line number in the Bash script.
$1 : First argument
$2 : Second argument
...

echo "my inp var are $@ "
echo "my inp var are ${@} "
```
#### read
```
echo "what is your name"
read inp
echo "hi $inp"
echo "hi ${inp}
```
#### if
```
if [ <TRUE> ]; then
  echo "true"
else
  echo "false"
fi

[ -d file ] => file exist or not
```
math:
```
echo $((3+3))
echo $((6/2))
echo $((3%2))

if [ $(($[1} % 2)) -eq 0 ]; then
  echo "even"
else
  echo "odd"
fi



```
## 3
loop
#### for
```
seq 10
seq 5 10

for i in $(seq 5 10)
do
  echo $i
done  

---------

for i in {1..10}
do
  command
done  

-----

in 1 2 3 4 5 .. N
in file1 file2 file3
in $(Linux-Or-Unix-Command-Here)
in {0..10..2} # {START..END..INCREMENT}
in {1..5}
in $(seq 1 2 20)

-----

for (( ; ; ))
do
   echo "infinite loops [ hit CTRL+C to stop]"
done

-----

(( c=1; c<=5; c++ ))

```

```
while read line; do
# reading each line
echo "Line No. $n : $line"
n=$((n+1))
done < $filename
```

## 4
#### func
```
myfunc() {
    echo "hello"
}

myfunc
```
