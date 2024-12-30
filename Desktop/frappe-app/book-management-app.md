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
<br>
<code>$ bench --site books.localhost list-apps</code>
<br>
This should show our app(book_management) and frappe(default)
![Screenshot from 2024-12-30 14-53-49](https://github.com/user-attachments/assets/8124830f-1bce-4fd8-bd7a-8d232463727f)
<br><br>
### Let's setup desk of application
First of all create all doctypes that needed.
#### Create Book Doctype 
* Step: 1 Search for doctype list in search bar <br>
![Screenshot from 2024-12-30 15-03-14](https://github.com/user-attachments/assets/cccf6b12-9ec0-4989-b076-93d40072f423)
<br>

* Step: 2 Click to button +Add DocType
* Step: 3 File Module with Book Management and doctype name is Book
* Step: 4 Save
* Step: 5 Go to Fields
* Add Row

| Label          | Data Type        | Name        |
|----------------|------------------|-------------|
| Book Name      | Data             | book_name   |
| Author         | Data             | author      |
| Image          | Attach Image     | image       |
| ISBN           | Data             | isbn        |
| Status         | Select           | status      |
| Publisher      | Data             | publisher   |
| Description    | Text Editor      | description |
| Route          | Data             | route       |
| Published      | Check            | published   |

<br>
It should look like:
<br>

![Screenshot from 2024-12-30 15-23-26](https://github.com/user-attachments/assets/cda781b1-7985-41f8-b71d-265db3e229ce)
<br><br>
#### Create Library Member Doctype
* Go to fields
* Add Row

| Label          | Type            | Name        | Options          |
|----------------|-----------------|-------------|------------------|
| First Name     | Data            | first_name  |                  |
| Last Name      | Data            | last_name   |                  |
| Full Name      | Data            | full_name   |                  |
| Email Address  | Data            | email_address | Email          |
| Phone          | Data            | phone       |                  |

<br>
It Should look like:
<br>

![Screenshot from 2024-12-30 15-34-15](https://github.com/user-attachments/assets/861be22b-be19-4147-bedd-43325df9a63d)
<br><br>
#### Create Library Membership Doctype
* Go to fields
* Add Row

| Label           | Type  | Name           | Mandatory | Options             |
|------------------|-------|----------------|-----------|---------------------|
| Library Member   | Link  | library_member | true      | Library Member      |
| Full Name        | Data  | full_name      |           |                     |
| From Date        | Date  | from_date      |           |                     |
| To Date          | Date  | to_date        |           |                     |
| Paid             | Check | paid           |           |                     |
| Amended From     | Link  | amended_from   |           | Library Membership  |

<br>
It should look like:
<br>

![Screenshot from 2024-12-30 16-05-08](https://github.com/user-attachments/assets/e3a858a0-c38b-41a7-825a-fc7d3c7f63c3)
<br><br>
#### Create Library Transaction Doctype
* Go to fields
* Add Row

| Label           | Type   | Name           | Mandatory | Options               |
|------------------|--------|----------------|-----------|----------------------|
| Book            | Link   | book           | true      | Book                  |
| Library Member  | Link   | amended_from   | true      | Library Transaction   |
| Type            | Select | type           |           | Issue, Return         |
| Date            | Data   | date           | true      |                       |

So, Four Doctypes are created.

#### Let's create a role with name od Librarian (who have the access to add books)
* Step: 1 search for role
* Step: 2 create new role
* Step: 3 set Role Permissions MAnager
* Step: 4 Give access to Librarian (create, read, delete, write, print, report, export, share)
* Step: 5 Give Librarian role access to Doctypes (Book,Library Membership, Library Transaction)

