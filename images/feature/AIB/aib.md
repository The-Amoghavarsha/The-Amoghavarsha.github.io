---
title: "Arrays Are Powerful In Bash"
author: "Amoghavarsha"
---
![eye](/llp/AIB/1.png)

“$” might symbolize dollars to many of you, but for bash users it’s
the holy grail for retrieving stored data. Speaking of which, do you
know what’s the common place to store a piece of data? A variable.

# Variable

The name itself incurs that variable is something that could be
varied. So is it like a chameleon that changes colors all the time?
Not precisely, if you remember from the intro its a common place to
store a piece of data. That’s right. Mathematically and
computationally, a variable is something that stores or holds a
piece of data or value.

You might have heard the term “place holder” and that’s exactly what
a variable is. So how to store and retrieve information through
variables?

``` 
place="World"
echo "Hello $place" 
```
![2](/llp/AIB/2.png)

In the above code snippet, place is a variable and World is the
value assigned to the variable. In the next line, the value assigned to the variable is retrieved through echo command. As
aforementioned, “$” is the holy grail to retrieve stored value in
bash. An important thing to note here is, “=” doesn’t mean variable
name has a constant value, it just means that a value is assigned to
a variable name.

Now the value of variable place could be varied.

```
place="Mars"
echo "Hello $place"
```
![3](/llp/AIB/3.png)

Now the value of variable has changed to Mars from World. Imagine a
box where you could place an item and replace that item whenever you
wish.

![4](/llp/AIB/4.png)

![5](/llp/AIB/5.png)

What if you want to store many pieces of data in a single box?

# Array
Array is an ordered series of arrangement. Computationally, array
holds multiple values, whereas a normal variable holds a single
value. Array could also be defined as a special type of variable as
it could hold more than one value.
A typical array consists of an array name and an index. Each index
number associates with an element in the array.
Lets see how to create an array.

```
movies=('Primer' 'Inception' 'Enemy' 'Tenet')
```

Two things to keep in mind. Unlike other programming languages, bash
arrays are not led by commas after every element but spaces. There
is no space after array name(i.e, movies=), it’s followed by “=”. If
there is a space followed by the array name, shell interprets the
array name as a program to execute and “=” as the first parameter.

Now lets try to retrieve all the elements of the array.

![6](/llp/AIB/6.png)

As you could see in the above screenshot, you could retrieve the
array elements in two ways: one using the @ symbol between the
square brackets or using * symbol.

Here are some tips, you could remember @ by memorizing it like all
and * is a wild card which signifies everything. The syntax of
retrieving an array could look intimidating, so always remember “$”
is the holy grail for retrieving information, array names are placed
in between flower brackets {}, followed by special characters or
numbers in square brackets.

Lets see how to retrieve an individual element of the array.

![7](/llp/AIB/7.png)

Index numbers in bash arrays starts with 0 (similar to most of the
programming language, unlike R). So index 2 returns the value of
Enemy.

Let’s see what happens when negative indices are used.

![8](/llp/AIB/8.png)

So the negative index number retrieves values from reverse order.

You could also assign elements to the array explicitly in three
ways: Subscript Assignment, Index Assignment and assignment by name.

*Subscript Assignment*

```
movies=([4]='Ten cloverfield lane' [5]='Timecrimes')
```

![9](/llp/AIB/9.png)

*Index Assignment*

```
movies[1]='Vanilla Sky'
movies[2]='Mr.Nobody'
```
![10](/llp/AIB/10.png)

*Assignment by names*

```
movies[zero]='Magnolia'
```

![11](/llp/AIB/11.png)

What if you want to print the elements from one particular index to
another?

![12](/llp/AIB/12.png)

Here you are telling the array that from all its elements(@) , print
from index 1 to index 3.

![13](/llp/AIB/13.png)

Here you are telling the array that from all its elements(@), start
from index 1 and print all the following elements.

What if, you want to access the index numbers?

```
echo "${!movies[@]}"
```

![14](/llp/AIB/14.png)

The “!” symbol before array name helps to retrieve indices.

What if you want to see how many elements are there in an array?

```
echo "${#movies[@]}"
```

![15](/llp/AIB/15.png)

The “#” symbol before array name helps to retrieve number of
elements.

How to retrieve specific information from an element in the array?

![16](/llp/AIB/16.png)

Here the information of zeroth element(Magnolia) is retrieved,
starting from index 0 till index 2(not included).

What if you want to assign a sequence of numbers? You could do it
manually but here’s a easy way to do it.

![17](/llp/AIB/17.png)

_seq_ is a shell command that prints out sequence of numbers. In the
above example, _seq_ is placed in between \` \`.

Now lets try to write a simple shell script from the above
learnings.

```
#!/llp/AIB/usr/llp/AIB/bin/llp/AIB/bash
tvshows=('Mr.Robot' 'Homeland' 'The Americans' 'Death Note' 'Erased')
for a in "${!tvshows[@]}"; do
printf "${tvshows[$a]} has an index number of $a\n"
done
```
Let’s save the code as lp.sh. Next lets make it executable – chmod
+x lp.sh.

![18](/llp/AIB/18.png)

When the program is executed, you get the above result.

# Array Modification
Lets create a new array.

```
names=('Luther' 'Ambrose' 'Reddington' 'Mare')
```

To change the value of index 2 you could do the following.

```
names[2]=’Carrie’
```
![19](/llp/AIB/19.png)

What if, you want to append values by adding more elements to the
array?

![20](/llp/AIB/20.png)

What if, you want to add an element at a particular index position?

![21](/llp/AIB/21.png)

What if you want to delete an element?

![22](/llp/AIB/22.png)

Here, unset is a [shell builtin](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwiUoa6yh6v4AhXsSmwGHQMKDlMQFnoECAUQAQ&url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FShell_builtin&usg=AOvVaw1BOf5zWyabXMcp7cEqn3O5).

![23](/llp/AIB/23.png)

What if you want to merge two arrays?

Lets create another array.

```
surnames=('Dexter' 'Hannibal' 'Broody' 'Dan' 'Gordan' 'Steve')
```
![24](/llp/AIB/24.png)

What if you want to delete an array?

```
unset <array_name>
```
![25](/llp/AIB/25.png)

# Associative Array
An associative array is an array that stores string value as an
index. It could be declared and used in a bash script. This feature
was added in bash 4. To be sure, just check your bash version.

![26](/llp/AIB/26.png)

Declaring an associative array is easy, here’s the syntax.

```
declare -A <array_name>
```
Lets declare an associative array and initialize some elements.

![27](/llp/AIB/27.png)

Like in normal array, if you want to access an element of the array,
use the following syntax.

![28](/llp/AIB/28.png)

If you want to list the indices of the associative array, do the
following.

![29](/llp/AIB/29.png)

Now lets try to write a simple script to print the indices(keys) and
values of the associative array.

![30](/llp/AIB/30.png)

Here’s a catch, what if you want to display the indices in an
alphabetic order?

![31](/llp/AIB/31.png)

To reverse it, use –reverse flag.

![32](/llp/AIB/32.png)

Well that’s it for today. Do practice arrays; because they are
powerful! Show some love by sharing and subscribing to [Linux For All](https://www.youtube.com/channel/UCLi7utjkBxAYPtVQhTuiZ2Q)
