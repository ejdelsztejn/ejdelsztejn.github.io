#### Refactoring Code: Nested Collections in Ruby

I'm currently working through the [**Ruby Exercises**](https://github.com/ejdelsztejn/ruby_exercises) repo for Turing School, and recently I completed  `nesting_test.rb`.  It was a productive struggle for sure, and it's humbling to really take the time to look through the Ruby Docs for [hashes](https://ruby-doc.org/core-2.6.3/Hash.html) and [arrays](https://ruby-doc.org/core-2.6.3/Array.html).

The goal is to make each test pass in the `nesting_test.rb` file, which requires a nested hash called `stores` in the `nesting.rb` file.

The `stores` collection contains a hash of hashes and arrays.  The first key values are three stores, `:olive_garden`, `:dennys`, and `:macdonalds`.  Each key contains a hash value with additional keys, `:employees` and `:dishes`, which then contain additional collections.  For the purpose of this blog post, I am going to focus on the `:olive_garden` key, and in particular the test `test_full_menu_price_for_olive_garden`.

Here is the first part of the `stores` collection with `:olive_garden`.  I am abbreviating the code for brevity:

```ruby
def stores
  {
    olive_garden: {
      employees: ['Jeff', 'Zach', 'Samantha'],
      dishes: [ {name: 'Risotto',
                ingredients: ['Rice',
                              'Cheese',
                              'Butter'],
                price: 12},
                {name: 'Steak',
                ingredients: ['Beef',
                              'Garlic'],
                price: 15}
                ]
                      },
 # <...>
```

I got the test to pass, but I was dissatisfied with my initial solution, which felt clunky:

```ruby
def test_full_menu_price_for_olive_garden
  #=======================
  full_menu_price = []
  stores[:olive_garden].each do |key, value|
    if key == :dishes
      value.each do |element|
        if element.class == Hash
        full_menu_price << element.values_at(:price)
        end
      end
    end
  end
  full_menu_price = full_menu_price.flatten.sum
  #=======================
  assert_equal 27, full_menu_price
end
```

The directions encourage using `each` for the initial solution and then refactoring, which I did.  I initialized variable `full_menu_price` and assigned it the value of an empty array.  Then, I called the `each` method on the `stores[:olive_garden]` hash.  Since we wanted the array within `:dishes`, we only wanted to access the `value` `if key == dishes`.  Then, I called the `each` method on `value`, which is the array within `:dishes`.  

This ended up being way overcomplicated, and there was clearly a better, neater solution.

I've been trying to use the powerful `Array#inject` method more lately, and this seemed like the perfect opportunity to do so.  [This Medium post about `inject`](https://medium.com/@terrancekoar/inject-method-explained-ed531eff9af8) has helped me a lot with figuring out the best opportunities to use the method.

Ultimately, I arrived at this solution, which is far more elegant:

```ruby
def test_full_menu_price_for_olive_garden
  #=======================
  full_menu_price = stores[:olive_garden][:dishes].inject(0) do |accumulator, dish|
    accumulator += dish[:price]
  end
  #=======================
  assert_equal 27, full_menu_price
end
```

If you are looking to practice working with collections in Ruby, here are some resources I've found helpful:

* [Ruby Exercises: Collections](https://github.com/turingschool/ruby-exercises/tree/master/data-types/collections)
* [Launch School Array & Hash Exercises](https://launchschool.com/books/ruby/read/intro_exercises)
* [CodeWars: Pete, the Baker](https://www.codewars.com/kata/525c65e51bf619685c000059)
* [CodeWars: Delete occurrences of an element if it occurs more than n times](https://www.codewars.com/kata/554ca54ffa7d91b236000023)
* [CodeWars: Array.diff](https://www.codewars.com/kata/523f5d21c841566fde000009)
