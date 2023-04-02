# Vulnerability Taxonomy CWE Homework

## Name: James Nagy

### CWE-798: Use of Hard-coded Credentials

The CWE that I chose is the use of passwords or a crytographic key in software that is stored in a variable or a parameter. In other words, the passwords/cryptographic key is hard-coded. Hard-coding your credentials makes it so that someone can get around the authentication methods that have been put in place by the system administrator. This security flaw can be difficult to detect and fix, which may result in the software being disabled completely.

An example of this CWE could be a hard-coded passowrd that checks if the input for the password is correct:

```java
int VerifyUser(String password) {
  // Hard-coded password is in the parameters of the equals() method
  if(!password.equals("football123")) {
    // If password is incorrect...
    return(0);
  }

  // If password is correct...
  return(1);
```

My experience with this CWE comes from a class I took at Clark State. The class focused around creating a website that utilized a database of products. In order to connect to this database, our credentials were hard-coded in a php file. While this method is convenient for the students, it teaches them bad coding practices. I'm unsure why the instructors taught us to connect to our database this way. Even just not hard-coding the passwords would have been a simple task. 

The php file in question (I omitted the credentials):
```php
<?php
/* The Connection to mysql Database */
// all the info is on your mysql handout provided to you by the instructor
// the xxx is your connection data
$db_host = "some-server-at.clarkstate.edu";
// your user name
$db_user = "My username";
// your password
$db_pass = "Password stored here";
// database name 
$db_dbname = "DATABASE";
// database port
$db_port = "1234";
?>
```

There's a few ways that this flaw could be mitigated. Storing the user credentials in an encrypted config file would be a good first step. This file would only be on the users system and would never be put in the database. Prompting the user for a password would be another solution. Another way would be to use a secrets manager. But this may cost money and may not be worth it with this class. I think showing students how to use a config file would be the best solution to this security flaw. It'll save money, time, and be more secure than hard-coding the passwords. 
