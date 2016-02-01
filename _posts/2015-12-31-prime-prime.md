---
layout: post
title: Prime.prime?
date: 2015-12-31
---

I solved [this Codewars kata](http://www.codewars.com/kata/560b8d7106ede725dd0000e2/train/ruby) tonight, yay:

```ruby
require 'prime'

def prime_bef_aft(num)
  primes = []
  Prime.each(num){ |n| primes << n }
  primes.last == num ? bef_prime = primes[-2] : bef_prime = primes.last
  aft_prime = Prime.first(primes.size + 1).last
  [bef_prime, aft_prime]
end
```

I need to examine the [top-rated solution](http://www.codewars.com/kata/reviews/560c0937fc9968244e000010/groups/562208f693699057df000019), though:

```ruby
require 'prime'

def bef_prime(num)
  num -= 1
  return num.prime? ? num : bef_prime(num)
end

def aft_prime(num)
  num += 1
  return num.prime? ? num : aft_prime(num)
end

def prime_bef_aft(num)
  [bef_prime(num), aft_prime(num)]
end
```

The title of this post is only generally relevant to the topic at hand; I just really like the idea of reading Ruby code as human language. `Prime.prime?` seems to read as some sort of existential question.