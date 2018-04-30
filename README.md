# kotlin-notes

## Disclaimer

The following notes have been gathered from different sources and mixed with
personal experience. I do not claim to own any of the following content nor do I require
explicit mentioning of my name if any of this is used by another party.

## Kotlin’s philosophy

One of Kotlin's goals is terseness. Hence, no “new” needed to create a new instance of an object, no semicolons needed, and for basic operations there are no imports required because that’s included in the kotlin standard library. Unlike some other languages, Kotlin was not built as a language to do computer science research with but rather to save the programmer time and make the process of coding more efficient.

## Some differences between Java and Kotlin

### Comparing objects

In Java, the following snippet of code:

```
Employee employee1 = new Employee(“Jane”, 1);
Employee employee2 = new Employee(“John”, 2);
Employee employee3 = new Employee(“John”, 2);
```

Would evaluate like so:

`false`: `employee1 == employee2` <- checks for equality referentially. I.e. Is this the same reference?

`false` : `employee2 == employee3` <- checks for equality referentially. I.e. Is this the same reference?

`false` : `employee1.equals(employee2)` <- checks for equality structurally. Are the field values that same?

`true` : `employee2.equals(employee3)` <- checks for equality structurally. Are the field values that same?

But in Kotlin, the same comparisons will give the following results

`false`: `employee1 == employee2` <- actually defers to `.equals` for the comparison

`true` : `employee2 == employee3` <- actually defers to `.equals` for the comparison

`false` : `employee1.equals(employee2)` <- checks for equality structurally. Are the field values that same?

`true` : `employee2.equals(employee3)` <- checks for equality structurally. Are the field values that same?

#### Wait, so how do I check for *referential* equality in Kotlin?

Triple equals is your new friend for that:

```
false: employee1 === employee2
false: employee2 === employee3
```

Unlike the `==` operator, the `===` will check the references themselves to see if
it is the same instance

### Where can a function be declared?

- In Java, a function can only be declared *inside of a class*. 

- In Kotlin, a function can be declared independently from a class

Example:

```
package testing

fun main(args: Array<String>) {
    println("Hello Kotlin World")
}
```

That is a totally valid function declaration that will run independent of a class

### How can I cast and check if it's an instance of a class in Kotlin?

- In Kotlin, to check if an object is an instance of a certain class, use `is`

```
    val employee1 = Employee("James", 28)
    val employee2: Any = employee1

    if (employee2 is Employee) {
        val castedEmployee = employee2 as Employee
        println(castedEmployee.name)
        println("no way! Let's throw a party!")
    }
```

- To then cast this, use the `as` keyword like used above
- Note: The `as` isn't really needed, as the compiler takes care of that for you (this is called `Smart Casting`)

## Injecting variables into a string using `$` and doing operations on them

- As you can see from the following snippet, it's simple to declare variables and them used them
in a string for any purpose

```
    val myMoney = 3.45
    val moneyBillGatesHas = 50000.04

    println("I have $myMoney dollars. That is ${myMoney*100/moneyBillGatesHas}% of what Bill Gates has")
```

This will return something like:

`I have 3.45 dollars. That is 0.006899994480004416% of what Bill Gates has`
