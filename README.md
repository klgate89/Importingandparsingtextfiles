<h1> Update a file through a Python algorithm </h1>

 
<h2>Project Description</h2>
<i>This scenario is based on a fictional company:</i>
<br>
<br>

At my organization, access to restricted content is controlled with an allow list of IP addresses. The <b>"allow_list.txt"</b> file identifies these IP addresses. A separate remove list identifies IP addresses that should no longer have access to this content. I created an algorithm to automate updating the <b>"allow_list.txt"</b> file and remove these IP addresses that should no longer have access. 

<h2> Open the file that contains the allow list </h2>

For the first part of the algorithm, I opened the <b>"allow_list.txt"</b> file. First, I assigned this file name as a string to the import_file variable:

<img src="https://i.ibb.co/jyyqN21/PYTHONIMAGE1.png" alt="PYTHONIMAGE1" border="0">

Then, I used a <b>with</b> statement to open the file:

<img src="https://i.ibb.co/yq9WmHf/PYTHONIMAGE2.png" alt="PYTHONIMAGE2" border="0">

In my algorithm, the <b>with</b> statement is used with the <b>.open()</b> function in read mode to open the allow list file for the purpose of reading it. The purpose of opening the file is to allow me to access the IP addresses stored in the allow list file. The <b>with</b> keyword will help manage the resources by closing the file after exiting the <b>with</b> statement. In the code with <b>open(import_file, "r") as file:</b>, the <b>open()</b> function has two parameters. The first identifies the file to import, and then the second indicates what I want to do with the file. In this case, <b>"r"</b> indicates that I want to read it. The code also uses the <b>as</b> keyword to assign a variable named <b>file; file</b> stores the output of the <b>.open()</b> function while I work within the <b>with</b> statement.

<h2> Read the file contents </h2>

In order to read the file contents, I used the <b>.read()</b> method to convert it into the string.

<img src="https://i.ibb.co/0K7hw8T/PYTHONIMAGE3.png" alt="PYTHONIMAGE3" border="0">

When using an <b>.open()</b> function that includes the argument <b>"r"</b> for “read,” I can call the <b>.read()</b> function in the body of the with statement. The <b>.read()</b> method converts the file into a string and allows me to read it. I applied the <b>.read()</b> method to the file variable identified in the <b>with</b> statement. Then, I assigned the string output of this method to the variable <b>ip_addresses</b>. 

In summary, this code reads the contents of the <b>"allow_list.txt"</b> file into a string format that allows me to later use the string to organize and extract data in my Python program.

<h2> Convert the string into a list </h2>

In order to remove individual IP addresses from the allow list, I needed it to be in list format. Therefore, I next used the <b>.split()</b> method to convert the <b>ip_addresses</b> string into a list:

<img src="https://i.ibb.co/4S9mmJG/PYTHONIMAGE4.png" alt="PYTHONIMAGE4" border="0">

The <b>.split()</b> function is called by appending it to a string variable. It works by converting the contents of a string to a list. The purpose of splitting <b>ip_addresses</b> into a list is to make it easier to remove IP addresses from the allow list. By default, the <b>.split()</b> function splits the text by whitespace into list elements. In this algorithm, the <b>.split()</b> function takes the data stored in the variable <b>ip_addresses</b>, which is a string of IP addresses that are each separated by a whitespace, and it converts this string into a list of IP addresses. To store this list, I reassigned it back to the variable <b>ip_addresses</b>. 

<h2> Iterate through the remove list </h2>

A key part of my algorithm involves iterating through the IP addresses that are elements in the <b>remove_list</b>. To do this, I incorporated a <b>for</b> loop:

<img src="https://i.ibb.co/R3DNJ6x/PYTHONIMAGE5.png" alt="PYTHONIMAGE5" border="0">

The <b>for</b> loop in Python repeats code for a specified sequence. The overall purpose of the <b>for</b> loop in a Python algorithm like this is to apply specific code statements to all elements in a sequence. The <b>for</b> keyword starts the <b>for</b> loop. It is followed by the loop variable element and the keyword <b>in</b>. The keyword <b>in</b> indicates to iterate through the sequence <b>ip_addresses</b> and assign each value to the loop variable <b>element</b>. 

<H2> Remove IP addresses that are on the remove list </H2>

My algorithm requires removing any IP address from the allow list, <b>ip_addresses</b>, that is also contained in <b>remove_list</b>.  Because there were not any duplicates in <b>ip_addresses</b>, I was able to use the following code to do this:

<img src="https://i.ibb.co/7Q4bq8n/PYTHONIMAGE6.png" alt="PYTHONIMAGE6" border="0">

First, within my <b>for</b> loop, I created a conditional that evaluated whether or not the loop variable <b>element</b> was found in the <b>ip_addresses</b> list. I did this because applying <b>.remove()</b> to elements that were not found in <b>ip_addresses</b> would result in an error. 

Then, within that conditional, I applied <b>.remove()</b> to <b>ip_addresses</b>. I passed in the loop variable <b>element</b> as the argument so that each IP address that was in the <b>remove_list</b> would be removed from <b>ip_addresses</b>.

<H2> Update the file with the revised list of IP addresses </H2>

As a final step in my algorithm, I needed to update the allow list file with the revised list of IP addresses. To do so, I first needed to convert the list back into a string. I used the <b>.join()</b> method for this:

<img src="https://i.ibb.co/4PTzM87/PYTHONIMAGE7.png" alt="PYTHONIMAGE7" border="0">

The <b>.join()</b> method combines all items in an iterable into a string. The <b>.join()</b> method is applied to a string containing characters that will separate the elements in the iterable once joined into a string. In this algorithm, I used the <b>.join()</b> method to create a string from the list <b>ip_addresses</b> so that I could pass it in as an argument to the <b>.write()</b> method when writing to the file <b>"allow_list.txt"</b>. I used the string <b>("\n")</b> as the separator to instruct Python to place each element on a new line. 

Then, I used another <b>with</b> statement and the <b>.write()</b> method to update the file:


<img src="https://i.ibb.co/gdcW08T/PYTHONIMAGE8.png" alt="PYTHONIMAGE8" border="0">

This time, I used a second argument of <b>"w"</b> with the <b>open()</b> function in my with statement. This argument indicates that I want to open a file to write over its contents. When using this argument <b>"w"</b>, I can call the <b>.write()</b> function in the body of the <b>with</b> statement. The <b>.write()</b> function writes string data to a specified file and replaces any existing file content. 

In this case I wanted to write the updated allow list as a string to the file <b>"allow_list.txt"</b>. This way, the restricted content will no longer be accessible to any IP addresses that were removed from the allow list. To rewrite the file, I appended the <b>.write()</b> function to the file object <b>file</b> that I identified in the <b>with</b> statement. I passed in the <b>ip_addresses</b> variable as the argument to specify that the contents of the file specified in the <b>with</b> statement should be replaced with the data in this variable.

<H2>Summary</H2>

I created an algorithm that removes IP addresses identified in a <b>remove_list</b> variable from the <b>"allow_list.txt"</b> file of approved IP addresses. This algorithm involved opening the file, converting it to a string to be read, and then converting this string to a list stored in the variable <b>ip_addresses</b>. I then iterated through the IP addresses in <b>remove_list</b>. With each iteration, I evaluated if the element was part of the <b>ip_addresses</b> list. If it was, I applied the <b>.remove()</b> method to it to remove the element from <b>ip_addresses</b>. After this, I used the <b>.join()</b> method to convert the <b>ip_addresses</b> back into a string so that I could write over the contents of the <b>"allow_list.txt"</b> file with the revised list of IP addresses.

