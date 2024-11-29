<h1>Book Management System</h1>
This App is developing in Linux ubuntu 24.04.1 LTS

So, I am going to develope BMS(Books Management System)
Using frappe and FrappeUI, VueJS, TailwindCSS

First of all let's create an App:
Open terminal (ctrl + Alt + t)
Run this command under frappe-bench directory
<br>
<code>$ bench new-app book_management</code>
<br>
![alt text](<Screenshot from 2024-11-29 23-09-38.png>)
<br>
Congrats we have created our app within a second!

Now, we're going to create our site.
Run this command under frappe-bench directory
<br>
<code>$ bench new-site book.localhost</code>
<br>
![alt text](<Screenshot from 2024-11-29 23-18-57.png>)
<br>
Congrats we have created our site 
so now we can open on browser and can do further process
But before going to browser we need to tell our operating system that books.localhost should point to localhost.
so to do this we need to add this (127.0.0.1 books.localhost)
How can we do and where we have to add this?
so we need to add at /etc/hosts file.
we can do it manually by navigate in hosts file and add manually, Just write:
127.0.0.1 books.localhost
But there is another way just run this:
<br>
<code>$ bench --site books.localhost add-to-hosts</code>
<br>
![alt text](<Screenshot from 2024-11-29 23-27-34.png>)
<br>
So, Open any browser (Recommanded Chrome)
and Type http://books.localhost:8002/#login
This will show credentials for login
<br>
![alt text](<Screenshot from 2024-11-29 23-36-30.png>)
<br>
Now Install app on site
Run this command under frappe-bench directory
<br>
<code>$ bench --site books.localhost books_management</code>
<br>
To check the app installed?
Run this command to check the app installed or not!
<code>$ bench --site library.localhost list-apps</code>
This should show our app(book_management) and frappe(default)







