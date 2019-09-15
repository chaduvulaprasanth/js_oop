# Inheritance

User
  -properties
    -name
    -score
  -methods
    -increaseScroe: returns score increased by 1
    -decreaseScore: returna score decreased by 1

PaidUser
  -properties
    -name
    -score
    -balance
  -methods
    -increaseScroe: returns score increased by 1
    -decreaseScore: returna score decreased by 1
    -increaseBalance: returna balance decreased by 1

Using Inheritance convert the above into following patterns.

1. Prototypal Pattern
2. Pseudoclassical Pattern
3. Classes

<!-- Prototypal Pattern -->
```js
  var userMethods  = {
    increaseScroe: function (){return this.score = this.score + 1},
    decreaseScore: function (){return this.score = this.score - 1}
  };
  function createuser(name,score){
    var user = Object.create(userMethods);
    user.name = name;
    user.score = score;
    return user;
  }
  var paidMethods = {
    increaseBalance: function (){return this.balance = this.balance + 1}
  }
  function createpaiduser(name,score,balance){
    var paiduser = createuser(name,score);
    paiduser.balance = balance;
    Object.setPrototypeOf(paiduser,paidMethods);
	  Object.setPrototypeOf(paidMethods,userMethods);
	  return paiduser;
  }
```


<!-- Pseudoclassical Pattern -->
```js
  function Createuser(name,score){
    this.name= name;
    this.score = score;
  }
  Createuser.prototype.increaseScroe = function (){return this.score = this.score + 1};
  Createuser.prototype.decreaseScore = function (){return this.score = this.score - 1};
  function Paiduser(name,score,balance){
  Createuser.call(this,name,score);
  this.balance = balance;
  }
  Paiduser.prototype.increaseBalance = function (){return this.balance = this.balance + 1};
  Object.setPrototypeOf(Paiduser.prototype,Createuser.prototype)
    
```



<!-- classes -->
```js
class User {
	constructor(name,score){
		this.name = name;
		this.score = score;
    }
increaseScroe(){
	return this.score = this.score + 1;
}
decreaseScore(){
	return this.score = this.score - 1;
}
}
class Paiduser extends User {
constructor(name,score,balance){
	super(name,score);
	this.balance = balance;
}
increaseBalance(){
return this.balance = this.balance + 1;
}
```