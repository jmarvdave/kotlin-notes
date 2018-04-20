# kotlin-notes

## Kotlin’s philosophy

One of Kotlin's goals is terseness. Hence, no “new” needed to create a new instance of an object, no semicolons needed, and for basic operations there are no imports required because that’s included in the kotlin standard library. Unlike some other languages, Kotlin was not built as a language to do computer science research with but rather to save the programmer time and make the process of coding more efficient.

## Some differences between Java and Kotlin

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
