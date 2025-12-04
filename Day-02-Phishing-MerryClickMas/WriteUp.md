## 📝 Overview
  Today's challenge was called Phishing-MerryClickMas which mainly focused on teaching us about phishing attack - a type of social engineering attack.
  It focused on making us learn about different types of phishing attacks and how red teamers use these to attack organisations to infiltrate their systems.
  I learnt how to create and send phishing emails and how we can infiltrate a host when the threat vector sent in the email is activated.

## 🛠 Tools Used
  Linux CLI <br>
  Python Script <br>
  Social Engineering Toolkit <br>

## 🚀 Steps I Followed
  After starting the AttackBox, I navigated to the directory where our Python Script was present. The python was a simple server hosting a fake login page and listening for any connection.
  Once a connection was established the login page captured all the credentials entered into page.
  After running the server, I navigated to the main directory to set up a phishing emaail using the `setoolkit` tool.
  The setting up of the email required several tasks which were mentioned in the question itself.
  The email contsained a link to the server that we were running on the AttackBox.
  Once the email was sent I had wait for 1-2 minutes and see if there was any activity recorded by the script running.

## ❓ Questions & Answers
  ### What is the password used to access the TBFC portal? <br>
   Ans : The login credentials were recoreded by the script running on the server and could be easily extracted from there.

  ### Browse to http://MACHINE_IP from within the AttackBox and try to access the mailbox of the factory user to see if the previously harvested admin password has been reused on the email portal. 
  ### What is the total number of toys expected for delivery?
   Ans : In this question we could browse to the given ip address and then we come across a login page which we had to login which **factory** as username and the found password credentials from the previouss question.

## 🧠 Learnings
  I learned about the various phishing attacks and how the red teamers carry out these.
  Learned to use the `setoolkit` tool and how it helps to carry out various Social Engineering Attacks.
  Also learnt how clicking unverified links can lead to catastrophic results.
