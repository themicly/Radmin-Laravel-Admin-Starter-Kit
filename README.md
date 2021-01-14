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

Project Manager:pm@test.com

Sales Manager: sm@test.com

Password: 1234

# Page Structure
This template is a fixed layout with header, left sidebar, right sidebar (chat List) and main content area. All of the information within the main content area is yeilded within a div with an class of `main-content`. Left sidebar's (menu) content is within a div with an class of `app-sidebar`. Here is the general folder structure of blade files.

<img src="https://github.com/RakibDevs/Radmin-Laravel-Admin-starter-with-REST-API-User-Roles-Permission/blob/main/folder-structure.JPG">

The general template structure is the same throughout the template. Here is the main layout structure located in ```resources/views/layouts/main.blade.php```

```php
<!doctype html>
<html lang="{{ str_replace('_', '-', app()->getLocale()) }}" >
<head>
	<!-- initiate head with meta tags, css and script -->
	@include('include.head')
</head>
<body id="app">
    <div class="wrapper">
    	<!-- initiate header-->
    	@include('include.header')
    	<div class="page-wrap">
	    	<!-- initiate sidebar-->
	    	@include('include.sidebar')
	    	<div class="main-content">
	    		<!-- yeild contents here -->
	    		@yield('content')
	    	</div>
	    	<!-- initiate chat section-->
	    	@include('include.chat')
	    	<!-- initiate footer section-->
	    	@include('include.footer')
    	</div>
    </div>    
	<!-- initiate modal menu section-->
	@include('include.modalmenu')
	<!-- initiate scripts-->
	@include('include.script')	
</body>
</html>

```

# Create New Page
If you would like to create a new page the basic structure of the page is,
```php
@extends('layouts.main') 

@section('content')
    <!-- push external head elements to head -->
    @push('head')
        <title>Page title | Site title</title>
        <!-- add some inline style or css file if any -->
        <link rel="stylesheet" href="{{ asset('file-path')}}">
        <style type="text/css">
        	/* inline css
        </style>
    @endpush
    <div class="container-fluid">
    	<!-- page contents here -->
    </div>
    <!-- push external js if any -->
    @push('script') 
        <script src="{{ asset('script-path') }}"></script>
    @endpush
@endsection

```

# Sidebar
Basically this template has two sidebar. First one is left sidebar which is used as menu and second one is used for chatlist.

If you want to add a new menu items in the sidebar open ```resources/views/include/sidebar.blade.php``` and add menu,
```php
<div class="nav-item {{ ($segment1 == 'menu-route') ? 'active' : '' }}">
     <a href="{{url('menu-route')}}">
         <i class="ik ik-bar-chart-2"></i>
         <span>Menu Name</span>
     </a>
</div>
```
Note ```$segment1``` is use to determine active url

				```$segment1 = request()->segment(1);```
			
Suppose https://rakibul.dev/portfolio-cat/core-php/ is the basic url. here ```portfolio-cat``` is ```segment(1)``` and ```core-php``` is ```segment(2)```

# REST API

The [Radmin API](https://documenter.getpostman.com/view/11223504/Szmh1vqc?version=latest) is a low-level HTTP-based API for a Laravel admin starter kit that you can use to ```create/edit/update```

Radmin API uses [Laravel Passport](https://laravel.com/docs/7.x/passport)

Documentation: https://documenter.getpostman.com/view/11223504/Szmh1vqc?version=latest
After successful login, an access_token will be provided to user. This token will be used for further requests

```access_token``` will be like,
```
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwczpcL1wvd29ya3N1aXRlLmRldlwvYXBpXC92MVwvYXV0aFwvbG9naW4iLCJpYXQiOjE1ODAyODA3MjksImV4cCI6MTYxMTkwMzEyOCwibmJmIjoxNTgwMjgwNzI5LCJqdGkiOiJBYXE1QkdnT0p1dG1ycUdIIiwic3ViIjoxLCJwcnYiOiI4MThmNWM5OGFjZTIzNzUzMmQ5ZDQ5NDNmZDhlZmI1NDBiODU1YjQyIiwicmVtZW1iZXIiOjEsInR5cGUiOjF9.wK4OhcwUWa9uwFboqkZCOznjnRnjU19yzoCGCKIZUY0
```

User must set request header with this data,
```
'headers' => [
    'Accept' => 'application/json',
    'Authorization' => 'Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwczpcL1wvd29ya3N1aXRlLmRldlwvYXBpXC92MVwvYXV0aFwvbG9naW4iLCJpYXQiOjE1ODAyODA3MjksImV4cCI6MTYxMTkwMzEyOCwibmJmIjoxNTgwMjgwNzI5LCJqdGkiOiJBYXE1QkdnT0p1dG1ycUdIIiwic3ViIjoxLCJwcnYiOiI4MThmNWM5OGFjZTIzNzUzMmQ5ZDQ5NDNmZDhlZmI1NDBiODU1YjQyIiwicmVtZW1iZXIiOjEsInR5cGUiOjF9.wK4OhcwUWa9uwFboqkZCOznjnRnjU19yzoCGCKIZUY0',
],
```

# Roles and Permission
In this template, I create some users with different roles and permission. Lets see, how to apply this permissions in any where

If you'd like to open a group of routes for some sprcific permission in the route file follow this example,
```php
            //only those have permission_name permission will get access

	        Route::group(['middleware' => 'can:permission_name1|permission_name2'], function(){
	        	//route here
	    	})
```


