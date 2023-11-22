# Updating a File Through a Python Algorithm


-------

# Description <a name="description">

An allow list of IP addresses is used at my company to manage access to content that is restricted. These IP addresses are identified in the "allow_list.txt" file. The IP addresses that need to be blocked from accessing this content are listed in a separate remove list. I developed an algorithm to automatically remove these IP addresses that shouldn't be able to access the "allow_list.txt" file and update it. 

This assessment was completed as a component of my cybersecurity portfolio and as part of the <a href='https://www.coursera.org/google-certificates/cybersecurity-certificate'>Google Cybersecurity Professional Certificate</a> on Coursera, specifically in the  <a href='https://www.coursera.org/learn/automate-cybersecurity-tasks-with-python'> "Automate Cybersecurity Tasks with Python" </a> Course.


# Open the file that contains the allow list  <a name="scenario">
First, I opened the "allow_list.txt" file to begin the algorithm. Initially, I put this file name in the import_file variable as a string:

<p align="center">
Code: <br/>
<img src="https://i.imgur.com/Dui0ydq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Next, I used a with statement to open the file:

<p align="center">
Code: <br/>
<img src="https://i.imgur.com/ivLIqw4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

The allow list file is opened for reading in my algorithm by using the with statement and the read-only .open() function. I'm opening the file so I can access the IP addresses that are kept in the allow list file. By exiting the with statement and closing the file, the with keyword can help in resource management. Two parameters are passed to the .open() function in the code that uses open(import_file, "r") as file:. The first specifies which file needs to be imported, and the second tells me what I want to do with it. "r" in this instance refers to the need to read it. Additionally, the code assigns a variable called file using the as keyword; file holds the result of the .open() function while I'm working inside the with statement.

------------------------
   
Read The File Contents  <a name="control-assessment">
===================
I converted the file's contents into a string using the.read() method in order to read it.

<p align="center">
Code: <br/>
<img src="https://i.imgur.com/ShdDHX3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

I can call the.read() function in the body of the with statement when I use an .open() function that takes the argument "r" for "read." I can read the file by converting it to a string using the .read() method. I used the with statement's file variable to apply the .read() method. I then set the variable ip_addresses to contain the string output of this method. 

To put it briefly, this code reads the data from the "allow_list.txt" file and converts it into a string format that I can use in my Python program to organize and extract data.

Convert the string into a list  <a name="control-assessment">
===================

I needed the list format in order to remove specific IP addresses from the allow list. As a result, I then turned the string representing the IP addresses into a list using the.split() method:
 
<p align="center">
Code: <br/>
<img src="https://i.imgur.com/q49k1ql.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

A string variable is appended with the.split() function to run it. It functions by turning a string's contents into a list. To make removing IP addresses from the allow list simpler, ip_addresses has been divided into a list. The .split() function divides text by whitespace into list elements by default. The data kept in the variable ip_addresses, which is a string of IP addresses separated by whitespace, is fed into the.split() function in this algorithm, which turns it into a list of IP addresses. I returned this list to the variable ip_addresses in order to store it. 

Iterate Through The Remove List  <a name="control-assessment">
===================

Iterating through the IP addresses that are components of the remove_list is a crucial component of my algorithm. I used a for loop in order to accomplish this:

<p align="center">
Code: <br/>
<img src="https://i.imgur.com/RMX5LHO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Python's for loop repeats code for a given sequence. In a Python algorithm such as this one, the for loop's main goal is to apply particular code statements to each element in a sequence. The for loop is started by the for keyword. The keyword in and the loop variable element come next. The keyword in instructs the loop variable element to assign each value as iterates through the sequence of IP addresses. 

Remove IP Addresses That Are On The Remove List  <a name="control-assessment">
===================
Any IP address that appears in remove_list and the allow list, ip_addresses, must be removed according to my algorithm.  I could use the following code to accomplish this because ip_addresses did not contain any duplicates:

<p align="center">
Code: <br/>
<img src="https://i.imgur.com/KzFD2Wc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

I started by adding a conditional to my for loop to determine whether the loop variable element could be found in the ip_addresses list. I took this action since .remove() would fail when used on elements that weren't located in ip_addresses. 

After that, I applied.remove() to ip_addresses inside of that conditional. To ensure that every IP address in the remove_list was eliminated from ip_addresses, I supplied the loop variable element as an argument.

Update The File With The Revised List of IP Addresses   <a name="control-assessment">
===================
I had to update the allow list file with the updated list of IP addresses as the last stage in my algorithm. I had to first turn the list back into a string in order to accomplish this. For this, I employed the.join() method:

<p align="center">
Code: <br/>
<img src="https://i.imgur.com/jS49guB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

An iterable's items are all combined into a string using the join() method. When a string is joined together, the characters in the string that make up the iterable's elements are separated using the.join() method. In this algorithm, I created a string from the list of IP addresses using the join() method so that I could pass it as an argument to the write() method and write to the "allow_list.txt" file. The separator that I used to tell Python to start a new line for each element was the string ("\n"). 

Next, I updated the file using a second with statement and the.write() method:

<p align="center">
Code: <br/>
<img src="https://i.imgur.com/OSbG0pX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

I used the open() function in my with statement this time, passing in a second argument of "w". My desire to open a file and write over its contents is indicated by this argument. I am able to use the .write() function within the with statement's body by using the argument "w". In addition to replacing any existing file content, the .write() function writes string data to a specified file. 

In this instance, I wanted to write the updated allow list to the "allow_list.txt" file in the form of a string. In this manner, any IP addresses that were taken off the allow list will no longer be able to access the restricted content. I added the.write() function to the file object file that I specified in the with statement in order to rewrite the file. To indicate that the contents of the file mentioned in the with statement should be replaced with the data in this variable, I entered the ip_addresses variable as the argument.

Summary  <a name="control-assessment">
===================
I developed an algorithm that removes IP addresses from the "allow_list.txt" file of permitted IP addresses that are found in a remove_list variable. This algorithm read the file, converted it to a string that could be read, and then turned the string into a list that was kept in the ip_addresses variable. After that, I went through each IP address in remove_list one by one. I determined whether the element was included in the list of IP addresses with each iteration. If so, I removed the element from ip_addresses using the .remove() method. Subsequently, I employed the .join() function to transform the IP addresses back into a string, enabling me to append the updated list of IP addresses to the "allow_list.txt" file's contents.
