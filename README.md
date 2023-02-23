# Random Class

## Learning Goals

- Learn about the Java `Random` class.

## Introduction

Java has a utility to help generate random numbers. This may be of use if we want
to create a program that rolls a die or pulls a card from a deck. In this lesson
we will look at the `Random` class.

The **Random Class** is part of the package `java.util` and contains methods to
generate different types of random numbers. To use the `Random` class, we must
import it using the `import` statement, just like the `Scanner` utility:

```java
import java.util.Random;
```

We'll learn all about classes, methods, and packages in later lessons. For now,
know that once we have imported the `Random` class, we can use it anywhere in
our class by declaring a variable of that type:

```java
Random random = new Random();
```

Now that we have instantiated our `Random` instance, let's put it to use by
using some of its methods!

## `nextBoolean()`

If we want a random `boolean` value, we can use the `Random` class' method
`nextBoolean()` to return a pseudorandom `boolean` value of true or false.
Pseudorandom means that it is a completely computer-generated random value. It
isn't truly random since true randomness is generated through a physical
variable, like atmospheric noise. But pseudorandom is mathematically close
enough to emulate a random value for our purposes. For example, this could be
useful if we want to simulate flipping a coin and knowing if the coin lands on
heads or tails.

```java
import java.util.Random;

public class RandomExample {
    public static void main(String[] args) {
        Random random = new Random();
        
        // Did the coin land on heads?
        boolean isHeads = random.nextBoolean();
        System.out.println("We flipped a coin! Is it heads?");
        System.out.println(isHeads);
    }
}
```

If we were to run this program four times, a potential output of the code above
could look like this:

```text
We flipped a coin! Is it heads?
false

We flipped a coin! Is it heads?
false

We flipped a coin! Is it heads?
false

We flipped a coin! Is it heads?
true
```

## `nextDouble()` and `nextFloat()`

The `Random` class also has a `nextDouble()` method that returns a pseudorandom
`double` value between 0.0 and 1.0.

```java
import java.util.Random;

public class RandomExample {
    public static void main(String[] args) {
        Random random = new Random();
        double randomDouble = random.nextDouble();
        
        System.out.println("The random double is " + randomDouble);
    }
}
```

The `randomDouble` variable will be assigned to a different random number each
time the code is run. A potential output could look like this:

```plaintext
The random double is 0.751633395843345
```

Similarly, the `nextFloat()` method in the `Random` class returns a `float`
value between 0.0 and 1.0.

```java
import java.util.Random;

public class RandomExample {
    public static void main(String[] args) {
        Random random = new Random();
        float randomFloat = random.nextFloat();
        
        System.out.println("The random float is " + randomFloat);
    }
}
```

The output of the above code could look like this:

```plaintext
The random float is 0.17982453
```

## `nextLong()`

We can also generate a random `long` value by invoking the `Random` class'
`nextLong()` method. The `nextLong()` method will return a pseudorandom `long`
value:

```java
import java.util.Random;

public class RandomExample {
    public static void main(String[] args) {
        Random random = new Random();
        long randomLong = random.nextLong();
        
        System.out.println("The random long is " + randomLong);
    }
}
```

Unlike the `nextDouble()` and `nextFloat()` methods, the `nextLong()` method
does not have a bound to it. It could return both positive and negative numbers.
Consider the output if we were to execute the code above three times:

```plaintext
The random long is -3648376578569420679
The random long is 5753346489764395447
The random long is -9107496281823218113
```

## `nextInt()`

One of the most useful methods built into the `Random` class is the `nextInt()`
method. There are actually two methods of the `nextInt()` method within the
class too: One does not take in any arguments and the other one does. An
**argument** or **parameter** is something that is passed into a method. We have
seen before we can pass `String` values, numerical values, and even `boolean`
values to the method `System.out.println()`. The parameters are passed within
the parentheses of the method name.

The `nextInt()` method that does not take any parameters at all will simply
return a random `int` value in a similar fashion to how the `nextLong()` method
operated. This means it could return either a positive or a negative value as
long as it fits within an `int` data type:

```java
import java.util.Random;

public class RandomExample {
    public static void main(String[] args) {
        Random random = new Random();
        int randomInt = random.nextInt();
        
        System.out.println("The random int is " + randomInt);
    }
}
```

If we were to execute the code above three times, we might end up with an output
like this:

```plaintext
The random int is -899314034
The random int is 959478064
The random int is 715451550
```

The other method looks like this: `nextInt(int bound)` where it takes in an
`int` as an argument. What this method will do is it returns a pseudorandom
`int` value greater than or equal to 0 and less than the `bound` specified. For
example, if we want to generate random integers between 0 and 6 inclusively, we
could write something like this:

```java
import java.util.Random;

public class RandomExample {
    public static void main(String[] args) {
        Random random = new Random();
        
        /*Generate random integers between 0 - 6 inclusively
        This means we have to pass bound + 1 to the nextInt()*/
        int randomInt = random.nextInt(7);
        
        System.out.println("The random int is " + randomInt);
    }
}
```

The above could potentially have the following output:

```plaintext
The random int is 5
```

Let's consider a die roll. A die has numbers 1-6 on each of its faces. But the
`nextInt(int bound)` method states that it has a lower bound of 0. How can we
force the range to be 1-6 instead of 0-6?

The answer is to take the number of sides (a die has 6 faces) and then add 1:
`random.nextInt(6) + 1;` We add 1 to offset the 0 to get a range of 1 - 6
inclusively.

```java
import java.util.Random;

public class RandomExample {
    public static void main(String[] args) {
        Random random = new Random();
        int numberOfSides = 6;
        int minimum = 1;    // Since 1 is the lowest number we can roll
        int dieRoll = random.nextInt(numberOfSides) + minimum;
        System.out.println("Look! We rolled a " + dieRoll);
    }
}
```

Now if we were to run this program four times, a potential output of the code
could look like this:

```plaintext
Look! We rolled a 4
Look! We rolled a 2
Look! We rolled a 1
Look! We rolled a 1
```

## References

[Java 17 Random Class](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Random.html)