# Employee Reimbursement System

## Description

The Expense Reimbursement System (ERS) will manage the process of reimbursing employees for expenses incurred while on company time. All employees in the company can login and submit requests for reimbursement and view their past tickets and pending requests. Finance managers can log in and view all reimbursement requests and past history for all employees in the company. Finance managers are authorized to approve and deny requests for expense reimbursement.

## Technologies Used

- Java 8
- JDBC
- PostgreSQL
- Javalin
- Log4j
- JUnit
- Mockito
- React
- Redux
- Typescript
- HTML
- CSS

## Features

### Regular Users

- Log in and out
- View employee homepage
- Submit a reimbursement request
- View pending reimbursement requests
- View resolved reimbursement requests
- View account information
- Update account information

### Managers

- View manager homepage
- Approve/deny pending reimbursement requests
- View all pending requests of all employees
- View all resolved requests of all employees
- View reimbursement requests of a specific employee
- View all employees

## Getting Started

### Setting up the repository

Create a gitbash terminal in the directory where you want to store the repository and run the following commands:

```
git clone
cd ./employee-reimbursement-system/ers-frontend
npm install
```

### Setting up the database

- Create a database in the SQL client software application of your choice (DBeaver was used in this project)
- Create the necessary tables by running the following queries:

```
create table reimbursement_status (
	status_id int primary key generated always as identity,
	status varchar(64)
);

create table reimbursement_type (
	type_id int primary key generated always as identity,
	type varchar(64)
);

create table reimbursement (
	reimbursement_id int primary key generated always as identity,
	amount numeric not null,
	submitted_date date not null,
	resolved_date date,
	description varchar(128), 
	reimbursement_author int references users(user_id), 
	reimbursement_resolver int references users(user_id),
	reimbursement_status int references reimbursement_status(status_id), 
	reimbursement_type int references reimbursement_type (type_id)
);

create table users (
	user_id int primary key generated always as identity,
	username varchar(64),
	password varchar(25),
	first_name varchar(28),
	last_name varchar(28),
	email varchar(64),
	role int references user_roles(role_id)
);

create table user_roles ( 
	role_id int primary key,
	role varchar(28) unique
);
```

## Usage



## Contributors

Hailey "Yue" McNelis
Robert Duong
