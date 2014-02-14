Just to learn about RSpec. Get out !

#### NOTES:

##### subject

    subject(:lol)

> Is the subject that will be tested. Reloaded in each test.

Instead this:

    foo = Foo.new
    expect(foo).to be_true

You can use:

    subject(:foo) { Foo.new }
    expect(foo).to be_true

##### let

    let(:lol) { 'lol' }

> used to define some dependencies of the test. If you will test a controller and need a User for example. <br >
Not reloaded is each test, If some test modify this value, this modification will be used in the others tests


    let(:user) { User.create }
    expect(user).to be_true


##### mock

> Used when you need to fake some object in test. In some situations you need to simulate an object. For example, when you need to test a Cart you will need a Product, this Product can be a mock object.

    product = mock(:product)
    Cart.add(product)
    expect(Cart.size).be eql(1)

#####stub

> Used when you need to simulate some value of a method in a mock object

    product = mock(:product)
    product.stub :value => 1.00
    expect(product.value).to eql(1.0)

#Matchers

    expect(actual).to eql(1)
    expect(actual).not_to eql(1)

##### Matchers truthy and falsy

    expect(obj).to be_true
    expect(obj).to be_false
    expect(obj).to be_empty
    expect(obj).not_to be_empty
    expect(obj).to be

##### Equality Matchers

```ruby
# If 'a' and 'b' object are the same object
    a.equal?(b)

# If 'a' and 'b' have the same value
    a.eql?(b)

# If 'a' and 'b' have the same value with value convesion
    a == b
```

> matchers:

    expect(a).to equal(b) => a.equal?(b)
    expect(a).to be(b)    => a.equal?(b)
    expect(a).to eql(b)   => a.eql?(b)
    expect(a).to eq(b)    => a == b