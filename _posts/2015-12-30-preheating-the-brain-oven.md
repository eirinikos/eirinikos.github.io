---
layout: post
title: pre-heating the brain oven
date: 2015-12-30
---

![snow bear]({{site.github.url}}/images/2015-q4/snow_bear.jpg)

<span class="caption">Snow Bear II, North York, Toronto, ON</span>

Today's crowning achievement was either helping with the driveway shoveling, or helping craft this snow bear. Wooh!

Wonderful as a snow bear is, tonight I finally returned to study [this Stack Overflow post](https://stackoverflow.com/questions/3398159/all-factors-of-a-given-number/3398195#3398195) in order to code a better solution to [this Project Euler problem](https://projecteuler.net/problem=3). My current solution gleefully attempts to create a 600,851,475,142-long list in memory. Wooh!

```ruby
def max_prime_factor(num)
# returns the largest prime factor of num
# does not work for Bignums ;_;
  (2..num).select{ |n| (num % n == 0) && (2...n).none?{ |i| n % i ==0} }.max
end
```

It struck me that for a moment, I was struggling to understand what Ruby's [Prime.prime_division](http://ruby-doc.org/stdlib-2.2.0/libdoc/prime/rdoc/Prime.html#method-i-prime_division) does. My fingers also felt hesitant with typing the commands to Terminal and I felt really guilty with having to double-check how to declare a lambda. (I was getting tired of typing **num.prime_division** and figured I'd get around it with a lambda; also, lately I've been eager to use lambdas whenever possible.)

I realized that my brain had gotten rather limp and soft over the past week-plus of barely coding anything. After lamenting about my guilt to J, he matter-of-factly suggested that I "bake [my brain] in the oven" to harden it again.

OK... Well, this does crystallize the fact that passively reading about programming is no match for actually doing it. I feel horrifyingly impotent tonight!