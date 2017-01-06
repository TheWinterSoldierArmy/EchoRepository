# Echo Repository!
  
## What is this?
This is where all the pre-defined functions for Echo's A.R.S Will be held.
  
## Predfined ..what??
Yeah, that's right. **Pre-defined** functions. A new feature in the Echo 2.0 A.R.S System.  
Allows users to easily store template rules.  

## Function Example
Let's start you off with a simple one, this function has no parameters.
```php
.define func HelloUser():Hello {/user}!!
```
  
Looks easy enough right? Now when you type that it will be stored in your guilds `Defines` object.  
Allowing you to easily access that function in your server with any A.R.S Rule.  
Let's give you an example how to use the function in our A.R.S.  
```php
.auto .hello={init}
call::HelloUser();
```
Yay! Now when you type `.hello` you will get your `pre-defined` function's response.
  
## More Advanced Example
The function below has two parameters. And will redirect their message to a channel.
```php
.define func HelloUser(ChannelID, Message):{redirect:{0}}{1}
```
Alright now before we teach you how to use this function in your A.R.S Rules let's explain..  
What we're doing here is creating a function with Two parameters. And than defining those parameters  
using the `{0}` for ChannelID and `{1}` for Message.  
When you think about it, it's pretty simple. You can have an unlimited amount of parameters in your function  
**However** You need to define those parameters with a `{num}` counterpart.  
Meaning..If you have a function with 4 paramters `HelloUser(Param1, Params2, Params3, Params4)`  
you will need to define them in the functions response as such `{0}=Param1`, `{1}=Params2`, `{2}=Params2`, `{3}=Params4`  
  
Alright now let's learn how to use that function in the A.R.S Rules.  
Technically there are a few different ways to do this, let's try to cover them!  
This one will post a `pre-defined` message to a channel the user types with the command.  
```php
.auto &.hello {params}={init}
call::HelloUser({params}, This message is pre-defined);
```
Ok, now if the user types `.hello CHANNELID-HERE` the predfined message will be sent to the channel id they typed.  
Now let's switch it up, do the opposite!  
```php
.auto &.hello {params}={init}
call::HelloUser(1268555466456789, {params});
```
Ok now when someone types `.hello What is up guys!` Their message will be redirected to the channel: `1268555466456789`  
And since the `{redirect}` key requires the channel id. We need to make sure to place the channel ID not the name.
