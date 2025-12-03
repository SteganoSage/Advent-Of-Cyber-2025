### 📝 Overview
  Today's challenge focused mainly on the Linux Shell CLI commands and tools to navigate throught the directories and users and find the flags hidden there
  It also contained some topics related theory based questions.

### 🛠 Commands and Tools Used
  cd
  ls 
  echo
  cat
  sudo
  grep
  find

### ❓ Questions & Answers
  Question 1:
    “Which CLI command would you use to list a directory?”
    As soon as we land in McSkidy’s home directory, the very first task is to explore what files are available.
    Linux gives us the classic command: ls
    This simple command lists everything in your current directory: files, folders, and symlinks. 
    It’s the starting point of almost every investigation, and in our case, it revealed the directory named Guides, which became critical later.

  Question 2:
    “What flag did you see inside McSkidy’s guide?”
    cd Guides
    Inside the Guides folder, things looked empty… until we remembered that Linux hides files when they start with a dot (.). Using:
    
    ls -la
    
   we finally uncovered the hidden file:
    
    cat .guide.txt
    
  This file contains McSkidy’s handwritten security note, guiding us toward the log files and hinting at the presence of attackers.
  Inside this guide was a flag.

  Question 3:
    “Which command helped you filter the logs for failed logins?”
    Logs are massive. Opening them with cat is painful.
    So we use:
    
      grep 
      
   This immediately highlighted repeated failed logins from strange HopSec hostnames, confirming that someone was brute-forcing SOCmas.
  
  Question 4:
    “What flag did you see inside the Eggstrike script?”
    Following log clues, we inspect the home directory of the targeted user, socmas, and search for anything suspicious using:
  
      find /home/socmas -name *egg*
   A malicious shell script pops up:
  
      eggstrike.sh
   Inside the script sits another hidden flag.
  
  Question 5:
    “Which command would you run to switch to the root user?”
    To dig deeper or modify system-level settings, you need root privileges.
    The simplest method on many Linux systems is:
  
      sudo su
   Once inside, you can confirm your identity with:
  
      whoami
   which should output
  
      root
  
  Question 6:
    “What flag did Sir Carrotbane leave in the root bash history?”
    The .bash_history Files record every command a user runs, unless explicitly cleared. Most attackers forget this step.
    Inside /root/.bash_history, we find two suspicious curl commands, one uploading stolen wishlist data and another sending encoded content to HopSec servers.
    Along with them sits the final challenge flag.

### 🧠 Learnings
  The learnings that is drew from this challenge is that how do we change the hostnames and then make them available to run commands. 
  Plus this challenge worked up as a brush up to my knowledge of the various linux shell cli commands and tools
    
