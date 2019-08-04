## Active Record Association

__활성 레코드 관계__ 는 관계가 연결된 모델들을 보다 쉽게 처리해준다. 

#### example

고객 - 주문 모델

```ruby
`class` `Customer < ActiveRecord::Base``end` `class` `Order < ActiveRecord::Base``end`
```

##### 고객이 새로운 주문을 추가할 때

```ruby
@order = Order.create(order_date: Time.now, customer_id: @customer.id)
```

##### 고객 삭제 시, 고객 주문도 삭제해야 할 때

```ruby
@orders = Order.where(:customer_id => @customer.id)
@orders.each do |order|
  order.destroy
end
@customer.destroy
```



활성 레코드 관계를 사용할 경우를 살펴보자

#### example

활성 레코드 관계 선언

```ruby
class Customer < ActiveRecord::Base
  has_many :orders, :dependent => :destroy
end
 
class Order < ActiveRecord::Base
  belongs_to :customer
end
```

##### 고객이 새로운 주문을 추가할 때

```ruby
#@order = Order.create(order_date: Time.now, customer_id: @customer.id)
@order = @customer.orders.create(order_date: Time.now)
```

##### 고객 삭제 시, 고객 주문도 삭제해야 할 때 

```ruby
# @orders = Order.where(:customer_id => @customer.id)
# @orders.each do |order|
#   order.destroy
# end
# @customer.destroy
@customer.destroy
```

코드가 훨씬 간단해졌다!!



### Rails 의 관계란

활성 레코드 간의 모델을 연결해 주는 것을 말한다. association 은 매크로 스타일의 호출로 구현되어, 선언만 하면 모델 사이에서 만들어진다. 관계 선언 시 `pk` 와 `fk` 의 정보들을 모델들의 인스턴스 사이에 생성하라는 명령어가 만들어지며, 이들 모델에 여러 유용 함수가 추가된다. 

##### Association type

#### example

- __belongs_to __B

  한 모델이 다른 모델이 속해있다는 선언코드.하나의 주문은 오직 하나의 고객에만 관련되어 있을 때 선언한다. 

  ```ruby
  class Order < ActiveRecord::Base
    belongs_to :customer
  end
  ```

- __has_one __B

  객체 B 를 하나 가진다. 다른 모델과의 1:1 관계를 규정하지만, 하나의 모델이 다른 모델을  __소유하거나 포함__함을 의미한다. 

  ```ruby
  class Supplier < ActiveRecord::Base
    has_one :account
  end
  ```

- __has_many__ B

  객체의 예를 여러개 갖는다. 다른 모델과 1:N 관계를 말하는데, 다른 모델의 예를 0~N 개 가지고 있을 때 사용하게 된다. 

  ```ruby
  class Customer < ActiveRecord::Base
    has_many :orders
  end
  ```

- __has_many :through__ B

  B 객체의 예를 통해서 여러개를 갖는다. M:N 관계 설정에 사용된다. 다른 복수개의 모델을 제 3의 모델을 통해 가지게 된다.

  ```ruby
  class Physician < ActiveRecord::Base
    has_many :appointments
    has_many :patients, :through => :appointments
  end
   
  class Appointment < ActiveRecord::Base
    belongs_to :physician
    belongs_to :patient
  end
   
  class Patient < ActiveRecord::Base
    has_many :appointments
    has_many :physicians, :through => :appointments
  end
  ```

  새로운 연결 모델들은, 새롭게 연관된 객체 예들로 생성되고, 

- __has_one :through__ B

  B 객체의 예를 통해서 하나를 갖는다. 또 다른 모델과의 1:1 연관을 설정한다.

  ```ruby
  class Supplier < ActiveRecord::Base
    has_one :account
    has_one :account_history, :through => :account
  end
   
  class Account < ActiveRecord::Base
    belongs_to :supplier
    has_one :account_history
  end
   
  class AccountHistory < ActiveRecord::Base
    belongs_to :account
  end
  ```

- __has_and_belongs_to_many__ B

  객체의 예에 속해 있으면서 동시에 B 객체의 예를 많이 갖는다. 다대 다 연결 사이에 어떤 모델 없이, 직접 생성. 

  ```ruby
  class Assembly < ActiveRecord::Base
    has_and_belongs_to_many :parts
  end
   
  class Part < ActiveRecord::Base
    has_and_belongs_to_many :assemblies
  end
  ```

  이러면 알아서 assemblies_parts 가 생기는듯? 물리적으로? 



#### belongs_to vs has_one

둘다 1:1 연관 짓는 코드. FK 를 어디에 넣을지 생각하면된다. `has_one` 을 설정한 모델은 has_one B 에서 B 가 내 것이란걸 말해준다. 



```ruby
class Supplier < ActiveRecord::Base
  has_one :account
end
 
class Account < ActiveRecord::Base
  belongs_to :supplier
end

# 설정 이후 마이그레이션 코드 
class CreateSuppliers < ActiveRecord::Migration
  def self.up
    create_table :suppliers do |t|
      t.string  :name
      t.timestamps
    end
 
    create_table :accounts do |t|
      t.integer :supplier_id
      t.string  :account_number
      t.timestamps
    end
  end
 
  def self.down
    drop_table :accounts
    drop_table :suppliers
  end
end
```



#### has_many :through VS has_and_belongs_to_many

둘다 M:N 관계를 지원하는 방법인데, 직접 / 간접의 유무의 차이가 있다. 

`has_and_belongs_to_many` 를 사용하면 "직접적"으로 관계가 만들어진다

##### example

```ruby
class Assembly < ActiveRecord::Base
  has_and_belongs_to_many :parts
end
 
class Part < ActiveRecord::Base
  has_and_belongs_to_many :assemblies
end
```

 `has_many :through` 는 연결 모델을 통해서 "간접적"으로 관계를 만든다. 

```ruby
class Assembly < ActiveRecord::Base
  has_many :manifests
  has_many :parts, :through => :manifests
end
 
class Manifest < ActiveRecord::Base
  belongs_to :assembly
  belongs_to :part
end
 
class Part < ActiveRecord::Base
  has_many :manifests
  has_many :assemblies, :through => :manifests
end
```

독립된 연결 모델의 경우 `has_many :through` 를 사용하지만, 연결 모델 자체가 필요하지 않다면 `has_and_belongs_to_many` 를 사용하는게 좋다. 



## 폴리모픽 관계

폴리모픽을 사용하면, 하나의 모델이 하나 또는 여러 모델에 속할 수 있다. 

```ruby
class Picture < ActiveRecord::Base
  belongs_to :imageable, :polymorphic => true
end
 
class Employee < ActiveRecord::Base
  has_many :pictures, :as => :imageable
end
 
class Product < ActiveRecord::Base
  has_many :pictures, :as => :imageable
end
```

