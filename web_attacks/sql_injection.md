Data is one of the most vital components of information systems. 
Database powered web applications are used by the organization to get data from customers. 
SQL is the acronym for Structured Query Language. 
It is used to retrieve and manipulate data in the database.

# 1. What is a SQL Injection?
SQL Injection is an attack that poisons dynamic SQL statements to comment out certain parts of the statement or appending a condition that will always be true. 
It takes advantage of the design flaws in poorly designed web applications to exploit SQL statements to execute malicious SQL code.

# 2. How SQL Injection Works
The types of attacks that can be performed using SQL injection vary depending on the type of database engine. 
The attack works on dynamic SQL statements. 
A dynamic statement is a statement that is generated at run time using parameters password from a web form or URI query string.

Let’s consider a simple web application with a login form. 
The code for the HTML form is shown below.

```
<form action=‘index.php’ method="post">
<input type="email" name="email" required="required"/>
<input type="password" name="password"/>
<input type="checkbox" name="remember_me" value="Remember me"/>
<input type="submit" value="Submit"/>
</form>
```

*_HERE:_*
- The above form accepts the email address, and password then submits them to a PHP file named index.php.
- It has an option of storing the login session in a cookie. We have deduced this from the remember_me checkbox. It uses the post method to submit data. This means the values are not displayed in the URL.

Let’s suppose the statement at the backend for checking user ID is as follows

```
SELECT * FROM users WHERE email = $_POST['email'] AND password = md5($_POST['password']);
```

*_HERE:_*
- The above statement uses the values of the $_POST[] array directly without sanitizing them.
- The password is encrypted using MD5 algorithm.

We will illustrate SQL injection attack using sqlfiddle. Open the URL http://sqlfiddle.com/ in your web browser. You will get the following window.

