---
layout: post
title: "Unit Testing with JUnit 5"
date: 2024-04-20
categories: blog
tags: testing junit java
---

JUnit 5 is the next generation of JUnit testing framework. It provides a more flexible and extensible testing platform.

## Writing a Simple Test

{% highlight java %}
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

public class CalculatorTest {
    @Test
    void testAddition() {
        Calculator calc = new Calculator();
        assertEquals(4, calc.add(2, 2));
    }
}
{% endhighlight %}

## Key Features

- Parameterized tests
- Dynamic tests
- Better organizations with nested tests
- Enhanced assertions
- Extension model

Writing comprehensive unit tests helps ensure code quality and prevents regressions.
