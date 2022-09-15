# Boma-Idea-test

BoMa Idea SA - technical interview

# Technical Interview

Create a git repository for the application (if possible publish it on github, _public_ or _private_ is indifferent). Please use new github standard names , `main` as main branch.

Create a issue for each task on your repository, you can copy/paste from this markdown file.

When you work on a issue create a new branch `issue<number>-issue-title` (insert maxium 2 words to make clear what is in the branch).  
When you finished an issue create a pull request. Then create again a new branch (from the last created one).  
When you will have finished all the tast send us the github repository link (if is private add us to the repository).

## Issue 1 - Setup

Create 
 database infrastructure using docker (and docker-compose). Setup an image of PosgreSQL 11.10.

Then setup the NextJS (v12) project.

## Issue 2 - Models

Create using Prisma the following models and check that the database is created correctly.

```
table Project (
	id number auto_increment pk
	name string
	state enum (Propose, Open, Closed)
	date Date
)

table Access (
	id number auto_increment pk
	project_id fk
	user_id number
	permit enum (Read, Create, Update, Delete)
	
	unique (project_id, user_id, permit)
)
```

The will be mocked.

```sql
INSERT INTO project (id, name, state, date)
VALUES (1, 'Project A', Propose, '2022-01-01'),
		(2, 'Project B', Open, '2022-02-09'),
		(3, 'Project C', Open, '2022-04-13');
		
INSERT INTO project (id, project_id, user_id, permit)
VALUES (1, 1, 1, Read),
		(2, 1, 1, Create),
		(3, 1, 1, Update),
		(4, 1, 1, Delete),
		(5, 1, 2, Read),
		(6, 1, 2, Create),
		(7, 1, 3, Read),
		(8, 2, 1, Read),
		(9, 2, 1, Create),
		(10, 2, 1, Update),
		(11, 2, 1, Delete),
		(12, 2, 2, Read),
		(13, 2, 2, Create),
		(14, 2, 2, Update),
		(15, 3, 1, Read),
		(16, 3, 1, Create),
		(17, 3, 1, Update),
		(18, 3, 1, Delete),
		(19, 3, 2, Read),
		(20, 3, 3, Read),
		(21, 3, 3, Create),
		(22, 3, 3, Update),
		(23, 3, 3, Delete);
```

**Access**

| id   | project_id | user_id | permit |
| ---- | ---------- | ------- | ------ |
| 1    | 1          | 1       | Read   |
| 2    | 1          | 1       | Create |
| 3    | 1          | 1       | Update |
| 4    | 1          | 1       | Delete |
| 5    | 1          | 2       | Read   |
| 6    | 1          | 2       | Create |
| 7    | 1          | 3       | Read   |
| 8    | 2          | 1       | Read   |
| 9    | 2          | 1       | Create |
| 10   | 2          | 1       | Update |
| 11   | 2          | 1       | Delete |
| 12   | 2          | 2       | Read`  |
| 13   | 2          | 2       | Create |
| 13   | 2          | 2       | Update |
| 14   | 2          |         |        |



## Issue 3 - API

Mock the user (you can choose, if save in the session or if you prefer to send it as property or parameter), this side of the solution will not be reviewed.

- [ ] Permissions API (check if the user can create, should bee easily extendible)
- [ ] Read All API - return to the user the project where he has access to
- [ ] Read API - return to the user a project (and the permissions on the project), remember to check if the user has access to the project
- [ ] Create API - create a project, check if the user has the rights to do it and check if the created object is correct
- [ ] Update API - updates a proejct, check if the user has the rights to do it and check if the created object is correct
- [ ] Delete API - delete a project, check if the user has the rights to do it.

## Issue 4 - View

### List

Create a view with an input box to insert the id of the user.

Create a list of ojbect (and the plus button to create if the user has the rights). And display all the objects.

### Item

Create a view with a return button to the previous view, the data of the object and the buttons of the operations the user has access to.

## Issue 5 - Advanced View

Create a filter and oder by on the List View, the user should be able to filter by status and to oder by name or by date.
