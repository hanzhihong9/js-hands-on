### Fail fast

```
// version 1
const checkActive = (isActive, isOwner) = {
  if(isActive) {
    if(isOwner) {
      return 'active Owner';
    }
    else {
      return 'active';
    }
  }
  return 'inactive';
}

// version 2, not nested if
const checkActive = (isActive, isOwner) = {
  if(!isActive) {
    return 'inactive';
  }
  if(!isOwner) {
    return 'active';
  }
  return 'active Owner';
}

// version 
const checkActive = (isActive, isOwner) = {
  if(!isActive) {
    return 'inactive';
  }
  return isOwner ? 'active Owner' : 'active';
}

```

### nullish coalescing operator

```
const user = {
 name: 'main'
}

const name = user.name || 'noname';  // 0, '', null , undefined, 

const name = user.name ?? ''noname; // null, undefined

```

### boolean conversion

```
const user = {};
const isActive =  user && user.name
const isActive =  !!(user && user.name)
const isActive =  Boolean(user && user.name)

if(isActive) {
  console.log(`user name ${user.name}`)
}
```


### avoid for loops

```
const orders = [234,234 234,34234,23423];
let total = 0;
const tax = [];
const hiValue = [];

for( let i = 0 ; i < orders.length ; ++1) {
  total += orders[i];
  tax.push(orders[i]* 1.2);
  if(orders[i] > 999) {
    hiValue.push(orders[i]);
  }
}

// version 2 
total = orders.reduce( (t, order) => t + order, 0);
tax = orders.map( order =>  order *1.2);
hiValue = orders.filter( order =>  order > 999);
```
