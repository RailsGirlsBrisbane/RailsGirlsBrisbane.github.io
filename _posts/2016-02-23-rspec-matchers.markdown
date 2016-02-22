---
layout: default
title: Two Confusing RSpec Matchers
permalink: rspec_matchers_blog
---

Sorcha Abel @sabel25 and Rachelle LeQuesne @RachelleOnRails

I have been working on an upgrade from Rails 2.3 to Rails 4.2. Along with the multitude of changes involved in such an undertaking, there is also the change from RSpec 2 to RSpec 3.

Two things had me particularly confused, and caused many failing specs until I figured out why.

##1. Equality Matchers

RSpec offers no less than three similarly-names equality matchers: `eq`, `eql` and `equal`.

After getting used to Ruby's so-called 'syntactic sugar', I have become lazy in looking up syntax. Oftentimes, whatever you think it might be, it is. So I assumed that the three different options for equality matchers were just that: options. Pick whichever one you like and go with it. Oh, how wrong I was! It turns out there is a world of difference between them:

####`expect(a).to equal(b)`
This states that the object referred to by **`a`** is expected to be the exact same object referred to by **`b`**.

####`expect(a).to eql(b)`
This states that the object referred to by **`a`** has the same value as the object referred to by **`b`**.

####`expect(a).to eq(b)`
This states that the object referred to by **`a`** has the same value as the object referred to by **`b`**, and it will perform a type conversion if necessary. This means that if **`a`** contains the value **`3`** and **`b`** contains the value **`3.0`**, it will return true.

##2. be Matchers

Again, RSpec offers no less than three similarly-names equality matchers: `be_true`/`be_false`, `be_truthy`/`be_falsey` and `be true`/`be false`. Luckily with RSpec 3, we are now down to two (see below).

Here there is a subtle difference that can cause all manner of unexpected behaviour if you choose to overlook it.

####`expect(a).to be true`
passes only if a == true

####`expect(a).to be_true`
passes if a is anything other than nil or false

####`expect(a).to be_truthy`
passes if a is anything other than nil or false

####`expect(a).to be false`
passes only if a == false

####`expect(a).to be_false`
passes if a is either nil or false

####`expect(a).to be_falsey`
passes if a is either nil or false

As you can see `be_true` and `be_false` are the same as `be_truthy` and `be_falsey`. In RSpec 3, there is no longer `be_true` and `be_false` so it is a little less confusing now.
