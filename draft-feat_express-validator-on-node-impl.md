# [DRAFT] Feat: `express-validator` Implementation on node `express` project

## Background

![Insert image that depict all of this process](url)

At my workplace im assigned to develop a whole new feature starting from the mongodb collection schema analysis
after finishing it up and getting approved now its the time to implement it in the code! (finally)
It's an existing new repo initialized by my colleagues at work, he already implement some basic functionality
I then followed his way of implementing the web services, just a simple CRUD for a collections,
I begin with the most basic and fundamental collections, finishing the basic CRUD functionality for each routes
following the appropriate GET, POST, PUT, DELETE for each routes, however if im not mistaken OWASP reccomendation is to
"Apply an allowlist of permitted HTTP Methods".

> The Insecure HTTP Method vulnerability refers to the use of insecure HTTP methods, such as PUT or DELETE, without proper security controls. These methods were originally intended for file management operations but are now commonly used in RESTful services for updating or deleting resources. The vulnerability arises when these methods are not properly secured or restricted, allowing attackers to manipulate or delete sensitive data.
> from [Stackhawk](https://docs.stackhawk.com/vulnerabilities/90028/#:~:text=The%20Insecure%20HTTP%20Method%20vulnerability%20refers%20to%20the%20use%20of,for%20updating%20or%20deleting%20resources.), [Cheatsheet](https://cheatsheetseries.owasp.org/cheatsheets/REST_Security_Cheat_Sheet.html), [WSTG](https://owasp.org/www-project-web-security-testing-guide/v41/4-Web_Application_Security_Testing/02-Configuration_and_Deployment_Management_Testing/06-Test_HTTP_Methods)

Upon completing all the routes, im testing the CRUD functionality
What i found is that despite I already define schema types options (required, enum, unique) I found out that required is
enforced i.e when i try to create the doc, and request body is missing the field, itll throw error.
However if i try to then insert a field that has enum option defined (admin or member) when i try to give it another type other than that two
it still can be created, well i have to also mention that the enum option is within an embedded field.
Also when i tried to create a new entry into that embedded array doc, I want it to be unique item, that's why i try to entry the unique option
apparently it's for indexing only, not for "distinct" value

I have previously implemented `express-validator` before, so as i try to implement it in this project, i will document my experience while implementing it now
while also learning it again and understanding it better, hopefully this article could help any of you reading this

## Contents

![To approach every task as a noob japan philosophy](url)

### why validation matters?

Input validation is performed to ensure only properly formed data is entering the workflow in an information system, preventing malformed data from persisting in the database and triggering malfunction of various downstream components. Input validation should happen as early as possible in the data flow, preferably as soon as the data is received from the external party.

Data from all potentially untrusted sources should be subject to input validation, including not only Internet-facing web clients but also backend feeds over extranets, from suppliers, partners, vendors or regulators, each of which may be compromised on their own and start sending malformed data.

Input Validation should not be used as the primary method of preventing XSS, SQL Injection and other attacks which are covered in respective cheat sheets but can significantly contribute to reducing their impact if implemented properly.
https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html

in the REST Security cheatsheet, here are the key point to do

- [x] Do not trust input parameters/objects.
- [x] Validate input: length / range / format and type.
- [x] Achieve an implicit input validation by using strong types like numbers, booleans, dates, times or fixed data ranges in API parameters.
- [x] Constrain string inputs with regexps.
- [x] Reject unexpected/illegal content.
- [x] **_Make use of validation/sanitation libraries or frameworks in your specific language._**
- [x] Define an appropriate request size limit and reject requests exceeding the limit with HTTP response status 413 Request Entity Too Large.
- [x] Consider logging input validation failures. Assume that someone who is performing hundreds of failed input validations per second is up to no good.
- [x] Have a look at input validation cheat sheet for comprehensive explanation.
- [x] Use a secure parser for parsing the incoming messages. If you are using XML, make sure to use a parser that is not vulnerable to XXE and similar attacks.

### well why not just add some validation codeblock inside the controller?

### or why not just create an util functions?

### alright, now how do i implement it in my project?

<!--TODO: finish @ 25/07/2024-->

## Summary
