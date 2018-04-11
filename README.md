<!DOCTYPE html>
<html>
    <head>
        <title>Learning JavaScript</title>
    </head>
    <body>
        <form id="register-form"> 
            <input id="name" type="text" placeholder="Name" value=""/>
            <input id="pw" type="password" placeholder="Password" value=""/>
            <input id="rgstr_btn" type="submit" value="get Account" onClick="store()"/> 
        </form>

        <form id="login-form"> 
            <input id="userName" type="text" placeholder="Enter Username" value=""/>
            <input id="userPw" type="password" placeholder="Enter Password" value=""/>
            <input id="login_btn" type="submit" value="Login" onClick="check()"/> 
       </form>

    <script type="text/javascript" src="jquery-1.11.3.min.js"></script>
    <script type="text/javascript" language="javascript" src="login.js"></script>

    </body>
</html>

And here is my JavaScript code:

// Name and Password from the register-form
var name = document.getElementById('name');
var pw = document.getElementById('pw');

// storing input from register-form
function store() {
    localStorage.setItem('name', name.value);
    localStorage.setItem('pw', pw.value);
}

// check if stored data from register-form is equal to entered data in the   login-form
function check() {

    // stored data from the register-form
    var storedName = localStorage.getItem('name');
    var storedPw = localStorage.getItem('pw');

    // entered data from the login-form
    var userName = document.getElementById('userName');
    var userPw = document.getElementById('userPw');

    // check if stored data from register-form is equal to data from login form
    if(userName.value !== storedName || userPw.value !== storedPw) {
        alert('ERROR');
    }else {
        alert('You are loged in.');
    }
}
you have 2 issues: 1. "name" is a reserved word, it's gonna act goffy on you, change it to something else like name1 or nm or something. 2. don't use !==, != will do, you logic is faulty anyways, change it to this:

if(userName.value == storedName && userPw.value == storedPw) {
        alert('You are loged in.');
    }else {
        alert('ERROR.');
    }

But yeah, I know you are just practicing, but don't actually save usernames and passwords on the client side.
