---
layout: post
title:  "Singleton design pattern"
date:   2015-12-25 17:48:44 +0530
categories: blog
tags: java
author: praveen
---

Singleton design pattern is a creational design pattern which ensures that we have only one instance of a class of an object within the application. 

{% highlight java %}

package com.code.singleton;
 
import java.util.HashSet;
import java.util.Set;
 
public class ShowSolution {
       
        private static final ShowSolution INSTANCE = new ShowSolution();
        private Set<String> availableSeats;
       
        public static ShowSolution getInstance(){
                return INSTANCE;
        }
       
        private ShowSolution(){
                availableSeats = new HashSet<String>();
                availableSeats.add("1A");
                availableSeats.add("1B");
        }
        public boolean bookSeat(String seat){
                return availableSeats.remove(seat);
        }
        public static void main(String[] args) {
                ticketAgentBooks("1A");
                ticketAgentBooks("1A");
        }
        private static void ticketAgentBooks(String seat){
                ShowSolution solution = getInstance();
                System.out.println(solution.bookSeat(seat));
               
        }
       

    }
{% endhighlight %}

The key things to notice about a singleton pattern is:

1. The singleton object is a private static final resource
2. There is a public getInstance() method to get access to the singleton resource
3. A private constructor such that the object cannot be created from the outside

{% highlight java %}

package com.code.singleton;
 
import java.util.HashSet;
import java.util.Set;
 
public class ShowSolution {
       
//      eager initialization
//      private static final ShowSolution INSTANCE = new ShowSolution();
       
//      lazy initialization
        private static ShowSolution INSTANCE;
       
        private Set<String> availableSeats;
       
//      eager initialization
/*      public static ShowSolution getInstance(){
                return INSTANCE;
        }*/
       
//      lazy initialization
        public static ShowSolution getInstance(){
                if(INSTANCE == null){
                        INSTANCE = new ShowSolution();
                }
                return INSTANCE;
        }
       
        private ShowSolution(){
                availableSeats = new HashSet<String>();
                availableSeats.add("1A");
                availableSeats.add("1B");
        }
        public boolean bookSeat(String seat){
                return availableSeats.remove(seat);
        }
        public static void main(String[] args) {
                ticketAgentBooks("1A");
                ticketAgentBooks("1A");
        }
        private static void ticketAgentBooks(String seat){
                ShowSolution solution = getInstance();
                System.out.println(solution.bookSeat(seat));   
        }

    }

{% endhighlight %}

The above code describes two different implementations of the Singleton design pattern one which involves Eager initialization of the resource and the other a lazy initialization.

The above example is not thread safe. However we can make them thread safe by adding a synchronized block in the getInstance() method but that results in a performance hit. This problem can be solved by using "double checked locked Singleton design pattern".

The singleton design pattern can be coded in a much simpler way using enums as below: 

{% highlight java %}

package com.code.singleton;
 
import java.util.HashSet;
import java.util.Set;
 
public enum ShowEnum {
       
        INSTANCE;
       
        private Set<String> availableSeats;
       
        private ShowEnum(){
               
                availableSeats = new HashSet<String>();
                availableSeats.add("1A");
                availableSeats.add("1B");
        }
       
        public boolean bookSeat(String seat){
                return availableSeats.remove(seat);
        }
       
        private static void ticketAgentBooks(String seat){
                ShowEnum show = ShowEnum.INSTANCE;
                System.out.println(show.bookSeat(seat));
        }
       
        public static void main(String[] args) {
                ticketAgentBooks("1A");
                ticketAgentBooks("1A");
        }

    }

{% endhighlight %}

Benefits:

1. The key benefits of using a singleton class is that there is only a single instance of an object in the entire application.

2. Use of the singleton design pattern increases the performance of the application as some resources are very expensive to create.
