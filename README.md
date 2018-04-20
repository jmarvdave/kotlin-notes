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
