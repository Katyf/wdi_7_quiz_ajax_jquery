# JQuery/Ajax Quiz

Write your answer below each question.

### Question 1
(a) What is a click handler?
It binds an event handler to a click event - e.g, it connects to something that does something when the user clicks

(b) Where in your JS file should you put it, and WHY?
It should be in your (document).ready function
So it can access all functions/variables elsewhere

### Question 2
If you get the error `$ is undefined`, what does that mean and what could you do to fix it?

### Question 3
What should go in the `$(document).ready()` part of your JS file?
At the bottom, because it reads the code top down

### Question 4
In an AJAX GET request, what does the argument of the `.done()` callback - in the example below, that would be `data` - represent?
the results of the get request

```
$.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'GET',
  })
  .done(function(data) {
    console.log("success!")
  });
```
### Question 5
In an AJAX POST request, what does the argument of the `.done()` callback - in the example below, that would be `data` - represent? (Hint: it's not the same as in Question 4.)
the data inputted from the post request, =>  data: { user: { name: "Anna", about: "instructor", email: "hi@gmail.com" } }
```
  $.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'POST',
    dataType: 'JSON',
    data: { user: { name: "Anna", about: "instructor", email: "hi@gmail.com" } },
  })
  .done(function(data) {
    console.log("success!");
  });
```
### Question 6
Suppose you had the following form in your HTML file. Use jQuery to write a single line of code that takes whatever the user entered in the textbox and saves it to the variable `user_input`.

var $user_input = $('input[type="text"]');

```
  <form>
    <p>The dress is:</p><input type="text" id="color">
    <input type="submit" value="Submit" id="submit">
  </form>
```

### Question 7
This code looks like it works, but when you run it, you see that the `UserApp.add_all_users()` function executes but `console.log` displays `undefined`. What's wrong with the code?
Data is not defined outside the scope of the ajax get request

```
var UserApp = {};
UserApp.get_all_users = function() {
  $.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'GET',
  })
  .done(function(data) {
    console.log("success!")
  });
  UserApp.add_all_users(data);
};

UserApp.add_all_users = function(data) {
  console.log(data);
};
```



