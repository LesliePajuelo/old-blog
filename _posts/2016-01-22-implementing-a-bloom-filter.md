---
id: 284
title: Implementing a Bloom filter
date: 2016-01-22T17:36:16+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=284
permalink: /implementing-a-bloom-filter/
categories:
  - web development
---
A Bloom filter is a data structure with major speed and space advantages with the disadvantage of ambiguity.

It&#8217;s like a hash table in that it uses hashing function to store the location of the key. However, the basic bloom filter does not store values, only whether a value does not exist in the set or if it maybe exists in the set. Wikipedia calls it a <a href="https://en.wikipedia.org/wiki/Bloom_filter" target="_blank">&#8220;space-efficient probabilistic data structure&#8221;</a>.

The hallmark for a bloom filter are hashing functions and that an item cannot be removed. So this means that the two methods we&#8217;ll want is an add and a test. We&#8217;ll also need access to 3 hashing functions. Unfortunately, another key to bloom filters is that they hash to a location on a bit array, a data structure we&#8217;ll need to create first.

## Bit Array

A <a href="https://en.wikipedia.org/wiki/Bit_array" target="_blank">bit array</a> is can be used to implement a set as an array. While bit arrays can have many properties we only need limited functionality due to the constraints of the bloom filter. What it requires is an ability to flip a value to on and to check the status of the value.

To determine whether a bit needs to be flipped to the on position we will use a mask. We determine it by using the modulo of that index as a bit and raising it to the 2nd.

    BitArray.prototype.createMask = function(index) {
      return Math.pow(2, (index % 8));
    };

`Uint8Array` as it&#8217;s name implies is a an array of 8-bit integers which are set to 0. The values can be accessed using bracket notation like for other arrays.

    var BitArray = function(length) {
      this.length = length;
    
      this._uint8 = new Uint8Array(Math.ceil(this.length / 8));
    };

The flip on function needs to find the right location in the bitwise index, use the createMask function to have an alternative if the current value of at bitIndex is falsy.

    
    BitArray.prototype.flipOn = function(index) {
      //Find the bitwise index
      var bitIndex = Math.floor(index / 8);
    
      var mask = this.createMask(index);
    
      this._uint8[bitIndex] = this._uint8[bitIndex] | mask;
    };
    

The other piece for the bit array we need is to check the value at an existing bitwise index. It is nearly identical to the flip on function in that it calculates the bitwise index, creates a mask for that value, the only difference being that it returns whether the value is truthy or falsey.

    
    
    BitArray.prototype.check = function(index) {
    
      var bitIndex = Math.floor(index / 8);
    
      var mask = this.createMask(index);
    
      return ((this._uint8[index] && mask) !== 0);
    };

## Bloom Filter

Like said above a Bloom filter is a special case of bit arrays. All we need is a desired size and an array of hashing functions to iterate through.

    
    var BloomFilter = function BloomFilter(size, hashes) {
    
      this._storage = new BitArray(size);
    
      this._hashes = hashes;
    };</pre>
    <p></p>
    
    
    To add a value we iterate through the hashing function and flip that bit on, saying that this value does exist.
    
    
        
        BloomFilter.prototype.add = function (value) {
          var _this = this;
        
          this._hashes.forEach(function (fn) {
            _this._storage.flipOn(fn(_this._storage.length, value));
          });
        };
    
    
    The checking code merely returns the bit position in that location.
    
    
        
        BloomFilter.prototype.check = function (value) {
          var _this2 = this;
        
          return this._hashes.every(function (fn) {
            return _this2._storage.check(fn(_this2._storage.length, value));
          });
        };