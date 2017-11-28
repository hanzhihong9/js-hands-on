# js-hands-on

 ## JS Object is as dict 
 - Object to array
  
  __refer https://stackoverflow.com/questions/14810506/map-function-for-objects-instead-of-arrays__
 ```
 let newObject = {
            "a": 1,
            "b" :2
          };
 //to array
 let arr = Object.keys(newObject).map( key => new Object({ "name": key, "value": newObject[key]}) )    

//change itself
 Object.keys(myObject).map(function(key, index) {
   myObject[key] *= 2;
});
 
 //in for in 
 for(var key in myObject) {
    if(myObject.hasOwnProperty(key)) {
        myObject[key] *= 2;
    }
}


//new dict
var newObject = Object.keys(myObject).reduce(function(previous, current) {
    previous[current] = myObject[current] * myObject[current];
    return previous;
}, {});
 ```


## asyn mongoose testing
```
async function() { //insert new user
    //clean db
    //await dbcleaner.clean_promise();

    //create user
    username = uuid.v4();
    var user = new User({
      "username": username,
      "permissions":  ["sss", "aaa"]
    });
    let user_save_results = await user.save();
    userId = user_save_results._id;

    // create oauth client
    let datenow = new Date();
    var now = new Date();
    var expires_utc = new Date(now.getUTCFullYear(), now.getUTCMonth(), now.getUTCDate(),  now.getUTCHours()+8, now.getUTCMinutes(), now.getUTCSeconds());
    bearer_accessToken = uuid.v4();

    let accessToken_data = {
      "accessToken" : bearer_accessToken,
      "clientId" : "unit-test-client-id",
      "userId" : userId,
      "expires" : expires_utc,
      "scope" : [
        "https://scope1l",
        "https://scope2",
        "https://scope3"
      ]
    };

    let accessToken = new AccessToken_Model(accessToken_data);
    await accessToken.save();


    //
    sysconfigs = {
            "a": "1",
            "b" :"222",
            "c": "eet",
             
          };

    let sysconfigs_data = Object.keys(sysconfigs).map( key => new Object({ "name": key, "value": sysconfigs[key]}) )

    let sysconfig_Models = sysconfigs_data.map(item =>  new Sysconfig_Model(item) );
    await Promise.all( sysconfig_Models.map( aconfig => aconfig.save() ) );
```

