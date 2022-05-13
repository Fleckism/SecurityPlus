see lesson 9

## Add probable passwords to the word list file

John the Ripper uses word list files as the basis for its password cracking attempts. The employee survey results above include many probable passwords. You will extract the compressed wordlist file, and then add the probable passwords to the list.

1.  Run the following command to extract the **/usr/share/wordlists/rockyou.txt.gz** word list file:
    
    ```bash-notab-nocopy
    gunzip /usr/share/wordlists/rockyou.txt.gz
    ```
    
    > This word list is used as the source for the password cracking attempt.
    
    > The rockyou.txt wordlist contains entries with language that some may find offensive. If you are offended by bad language, please do not examine the file contents.
    
2.  Enter the following command to open the **rockyou.txt** wordlist file for editing:
    
    ```bash-notab-nocopy
    vim /usr/share/wordlists/rockyou.txt
    ```
    
    Vim quick reference  
      
      
    
      
      
    
    -     
        
    
3.  Select the **i** key to enter Vim's Insert mode, and then add the following passwords, each on a separate line, at the _top_ of the file:
    
    06101988  
    Password  
    Duke  
    george  
    $p0T
    
    Updated password list![Updated password list](https://labondemand.blob.core.windows.net/content/lab84043/Screen%20Shot%202020-11-07%20at%2011.28.33%20AM.png)
    
    > You would normally enter every survey response for each user (birthday, spouse name, anniversary, favorite color, favorite band, pet name). In order to better manage time, you will only enter the passwords John needs to guess. Note that you cannot enter a possible password for user06, because that user declined to fill out the survey.
    
4.  In Vim, press **ESC**, and then type :wq and press **ENTER** to save your changes and exit the file.
    
    You are returned to the command prompt.