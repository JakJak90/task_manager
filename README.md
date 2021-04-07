# task_manager
Fourth Python capstone project - Expand upon existing task manager project functionality. Completed 26/06/2020

Timeline:

Rename functions to match given function names - 23-06-2020

Number added to view my tasks function - 23-06-2020

select task function - started 23-06-2020 completed 24-06-2020

	number added as a manual counter
	
		enumerate function resulted in a tuple output when list prefered
		
		number is global number in relation to all tasks to aid in editing specific
		task line for select task functionality
		
	Taks selection by number implemented

mark_task function - 24-06-2020

edit_task function - 25-06-2020

generate_tasks function - 25-06-2020

	generation of task_overview.txt file
		
	generation of user_overview.txt file

display_statistics function - 26-06-2020
	
	Modified to use task_overview.txt and user_overview.txt for information
	
	Added functionality to check when files were last updated, if already exist
	
	added functionality to autmatically generate files if not present
	

Task : 
Note, task at hand is an extention of an existing capstone project, detailed below.

	Modify the previous task to use functions for the register user, add task, view 
	all and view my tasks sections.

	The register user function should be able to check for existing users and not allow
	a duplicate to be registered. If attempted an appropriate error message should be 
	displayed.

	If view my tasks is selected, the display should have a corresponding task number,
	which the user can select or use '-1' to return to the menu. The user can then 
	choose to edit the task or mark as complete. editing allows only the assigned
	user and the due date to be changed. This can only be done if task has not been
	marked complete.
	
	Add a new menu input called generate reports, which outputs 2 txt files: 
	task_overview.txt and user_overview.txt. 
	
	Modify display statistics option to generate statistics from task_overview.txt
	and user_overview.txt files. If the files do not exist, first run generate 
	reports option.
	
Planning:

Original project was performed using functions already, however specific names
were given for this task:

	Rename functions to comply with given function names
	
Register user function was given duplicate checking functionality in original project

Add a selectable numbering system to view my tasks function:

	Generate a number when calling view_my_tasks function
		View my tasks uses a for loop
			a counter can be implemented to increase with each succesive iteration
			
			Alternately, the enumerate() function can add numbers without the need for
			a counter variable
				only viable if enumerate numbering can be referenced and would number
				each list within a list, not individual elements within a nested list
				
				Attempted to use enumerate within task_check() function,
				found that that the resulting tuple was messy to work with.
				Counting loop selected for ease of use.
	
	Add all data to a new list variable
		not needed, count forms part of returned variable.
	
	implement function that gives the option to select a task by number or return to menu
	
		User can edit task complete value
			Allow user to write to tasks.txt file
			only specific task must be targeted, only completed value targeted
			
		
		User can edit task
			Allow user to write to tasks.txt file
			Only possible if task not indicated complete
			only specific task must be targeted, only due date and assigned targeted
			
Add generate reports function:

	option must be added to menu selection - gr as selector
	
	Output must generate 2 files:
		task_overview.txt must contain
			Total number of tasks generated
			Total number of completed tasks
			Total number of uncompleted tasks
			Total number of overdue, uncompleted tasks
			Percentage of tasks incomplete
			Percentage of tasks overdue
			
		user_overview.txt must contain
			Total number of registered users
			Total number of tasks generated
			for each user:
				Total number of tasks assigned to user
				Percentage of total tasks assigned to user
				Percentage of those tasks completed
				Percentage to still complete
				Percentage overdue and incomplete

Modify display statistics
	
	New source of data to be task_overview.txt and user_overview.txt
	
	Files above must be generated if not present
	
	Look into checking when last files were updated
	
		from http://effbot.org/zone/python-fileinfo.htm
			import os, time module
			use variable = os.stat(file_name.txt)
			last_modified = time.asctime(time.localtime(variable[ST_MTIME]))
		
		Ask user if they would like to update the files prior to proceeding


Previous Task:

Part 1:

	Create a task manager program for a small business to keep track of assignments
	given to each worker, the date issued and date due, task description, and an
	indication if task is complete or not. Data stored/retrieved from file "tasks.txt".

	Program must allow users to login with a matching username/password combination
	that has been stored, and display an error message if username/password incorrect.
	Combinations stored and retrieved from file "user.txt".

	After login, menu of options must be displayed for user registration, add task,
	view all tasks, view tasks assigned to user specifically and exit. Each option must
	perform the function indicated by its name.

Part 2:

	Format the program to restrict menu options: only the username admin must be allowed
	to register users.
	Additionally, admin must have a new menu option to display statistics


Planning:

Functions:

	login:
	
		have user enter a username, then enter a password.
			check if username/password combination appears in "user.txt" file
			if both appear in combination continue to menu
			if one or both do not match, print error message
	
	register user:
		
		Only allow admin user to access this option
			use an if statement to check if user is admin upon login
			if result false, display error message if user attempts to add a new user
	
		prompt user for a new username, password and confirm password
			check that username doesn't exist already, print error message if it does
			check that password and confirmed password match, print error message if not
			write username/password combination to file "user.txt"
		
	add task:
	
		prompt user for username to which the task is assigned
			check that user exists within "user.txt" file
			if not, display error message and prompt again
		
		prompt user for task title
		
		prompt user for task description
		
		prompt user for task due date
		
		Write task to file "tasks.txt", defaulting completed to "No" and date assigned to current date
			import module datetime
			use input today = datetime.date.today()
				for formatting, use today.strftime(%x). output result will formatted to local version
				otherwise, use today.strftime(%d %b %Y) to output as dd mmm yyyy
	
	view all tasks
		
		display each task in an easy to ready format
	
	view my tasks
		
		display only tasks assigned to logged in user in an easy to read format
	
	display statistics
		
		only allow admin user to see and access this option
			use an if statement to check if user is admin upon login
			if result false, display error message if user attempts to display statistics
		
		when selected, option displays total number of tasks and total number of users


Timeline :

Readme file planning 16-06-2020

Menu created 17-06-2020

Login function created 17-06-2020

register user function created 17-06-2020

username check function created 17-06-2020
	did not form part of initial planning
	function created to prevent duplication of code in login and register user functions

task check function created 18-06-2020
	did not form part of initial planning
	function created to prevent duplicate code in view_tasks, view_my_tasks and display_statistics functions

add task function created 18-06-2020

view tasks function created 18-06-2020

view my tasks function created 18-06-2020

display statistics function created 18-06-2020
