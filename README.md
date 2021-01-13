## [Radmin - Laravel Admin starter with REST API User Roles Permission](https://codecanyon.net/item/laravel-admin-template-roles-permission-editable-datatables/26005211)
<img src="https://github.com/RakibDevs/Radmin-Laravel-Admin-starter-with-REST-API-User-Roles-Permission/blob/main/radmin.jpg">




- [Getting started with Radmin](#getting-started-with-radmin)
    - [Installation](#installation)
    - [Page Structure](#page-structure)
    - [Create New Page](#create-new-page)
    - [Sidebar](#sidebar)
    - [REST API](#rest-api)
    - [Roles & Permissions](#roles-permission)
    - [Serverside Datatable](#serverside-datatable)
    - [Editable Datatable](#editable-datatable)
    - [Sources and Credits](#sources-and-credits)

# Installation
Create a database in phpmyadmin. Open `.env` file and change following credentials
```bash
  DB_DATABASE=your_database_name
  DB_USERNAME=your_database_user
  DB_PASSWORD=your_database_password
```
Don't forget to import `database.sql` file which is located in projects database folder or manually create a user in phpmyadmin 
and assign `Super Admin` role. Because `Super Admin` role can access all the premissions.

Credentials
Super Admin: admin@test.com
HR: hr@test.com
Project Manager: pm@test.com
Sales Manager: sm@test.com

Password: 1234

# Page Structure
This template is a fixed layout with header, left sidebar, right sidebar (chat List) and main content area. All of the information within the main content area is yeilded within a div with an class of `main-content`. Left sidebar's (menu) content is within a div with an class of `app-sidebar`. Here is the general folder structure of blade files
