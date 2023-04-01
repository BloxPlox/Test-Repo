# Vulnerability Taxonomy CWE Homework

## Name: James Nagy

### CWE-798: Use of Hard-coded Credentials

The CWE that I chose is the use of passwords or a crytographic key in software that is stored in a variable or a parameter. In other words, the passwords/cryptographic key is hard-coded. Hard-coding your credentials makes it so that someone can get around the authentication methods that have been put in place by the system administrator. This security flaw can be difficult to detect and fix, which may result in the software being disabled completely.

AN example of this CWE could be a hard-coded passowrd that checks if the input for the password is correct:

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
