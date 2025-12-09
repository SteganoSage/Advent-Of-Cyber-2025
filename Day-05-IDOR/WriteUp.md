## 📝 Overview

Today's challenge focused on Insecure Direct Object Reference (IDOR), a common web security vulnerability that falls under Broken Access Control.
IDOR vulnerabilities occur when an application exposes internal object identifiers, such as user IDs or file IDs, and fails to properly validate whether the authenticated user is authorized to access the requested resource.

In this challenge, we learned how attackers can manipulate object references in requests to gain unauthorized access to sensitive information belonging to other users.

## 🛠 Tools Used

Web Browser
Burp Suite (for request inspection)

## 🚀 Steps I Followed

First, I logged into the application using a normal user account and explored its functionality to understand how user-specific data was being accessed.

Then, I inspected the URLs and HTTP requests and noticed direct references to object identifiers such as user IDs being passed as parameters.<br>

Next, I attempted to modify these object identifiers manually in the request, changing the ID values to those belonging to other users.<br>

After sending the modified requests, the application responded with data belonging to another user without performing proper authorization checks.<br>

This confirmed the presence of an IDOR vulnerability, as sensitive information could be accessed by simply manipulating object references.

## ❓ Questions & Answers

The answers for today’s challenge were obtained by identifying unauthorized data exposure through modified object identifiers and observing the server responses after altering request parameters.

## 🧠 Learnings
Today I learnt :

The concept of Insecure Direct Object Reference (IDOR)<br>
The difference between authentication and authorization<br>
How improper access control can lead to serious data breaches<br>
The importance of enforcing server-side authorization checks<br>
Best practices to prevent IDOR vulnerabilities in web applications<br>
