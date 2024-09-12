A competent engineer constructing a house in Japan seeks a solution to organize his construction progress tracking. Currently, he manually documents each build session in a spreadsheet with photos and descriptions, which leads to disorganization and difficulty in accessing specific information. Originally, the client has been taking a picture and then writing a brief description. However, over time, the client has just taken photos without writing descriptions and is planning to go back in the future and write a description. This also makes it very difficult to find photos/receipts for different parts of the house. This has led to an overwhelming number of photos without descriptions, creating an unorganized system. Receipts have also been piling up, making it hard to track the total expenses for each project within the house. An in the appendix about the meeting.


# Rationale for Proposed Solution

To address this, I proposed a system that automates photo uploads, prompts for descriptions, and extracts metadata for date and time tracking. Additionally, the website should offer project management tools, including categorization by house sections and project types. It should enable easy tagging and tracking of expenses, along with robust search and filter functions for quick access to updates and material information. Lastly, the client seeks a dashboard displaying construction progress visually, highlighting completed tasks, ongoing projects, and material needs.

I propose using Python over other programming languages, such as Node and Nest, because Python is run on an external server instead of being downloaded from the Internet and then run on your computer (aka client-side software). Using Python prevents client-side attackers from injecting malicious code into the system and allows the application to run on a third-party server. I propose using Flask for the HTML framework because it works exceptionally well for small-scale applications and is completely customizable and flexible, unlike Fast API or Django, which have only one standard way to customize the application. I propose using an SQL database, specifically MySQL, due to its flexibility and easy migration to other SQL databases. In contrast, NoSQL databases can be more complex and challenging to transfer between systems. MySQL is a relational database management system that offers the advantage of server-based deployment, which is preferable to running the database on the client’s machine.







## Success Criteria
1. A The website allows users to upload photos. (Issue Tackled: Photo management and documentation)

2. B The website allows users to add descriptions to the photos after each build session and anytime thereafter, prompting the user if a photo doesn't have a comment. (Issue Tackled: Ensuring descriptive metadata and improving photo context)

3. C The website extracts meta-data from photos to keep track of specific dates and times when photos were taken. (Issue Tackled: Automatic tracking of photo timestamps)

4. A The website includes a project management feature that organizes and categorizes updates by different parts of the house or specific projects. (Issue Tackled: Project organization and categorization)

5. B The website allows basic operations on tags for specific projects (e.g., Tiling, Roofing). (Issue Tackled: Tag management for project specifics)

6. A The website tracks expenses across different categories (e.g., #wood, #tools, Total spending). (Issue Tackled: Expense tracking and categorization)

7. A The website provides a search and filter function to quickly find specific updates or material information by date, project, or keyword. (Issue Tackled: Efficient information retrieval)

8. A The website includes a dashboard that visually displays the progress of the construction, highlighting completed tasks, ongoing projects, and upcoming material needs. (Issue Tackled: Visualization of project progress and task management)




# Criteria B: Planning

## Design Overview 


<img width="571" alt="Screenshot 2024-08-23 at 9 56 05 AM" src="https://github.com/user-attachments/assets/92584afe-3091-4a3f-9d09-ad0715fb997c">

Figure 1 System Diagram

<img width="649" alt="Screenshot 2024-08-23 at 9 52 53 AM" src="https://github.com/user-attachments/assets/cf091ac1-e918-4c35-82a9-a1088e718af9">

Figure 2 WireFrame diagram for Constuction App


<img width="558" alt="Screenshot 2024-08-23 at 10 35 49 AM" src="https://github.com/user-attachments/assets/a5ca8371-45a1-4c10-a124-e23b614e8673">


Figure 3 ER Diagram of the construction Application. This diagram depicts the database structure used to store the phots, projects, comments, and users of the application. It also shows the relations ships between simliar tables variables.

<img width="452" alt="Screenshot 2024-08-23 at 10 32 56 AM" src="https://github.com/user-attachments/assets/592f8656-3ab5-415b-8e3b-9e6f9e257ceb">


Figure 4 Login Flow Chart; Flow chart shows the process for USer to login

<img width="431" alt="Screenshot 2024-08-23 at 2 48 06 PM" src="https://github.com/user-attachments/assets/d616f00f-9bc4-42cb-83c8-afa693dd0dcb">


Figure 5 EXIF Image data Flow Chart: Shows the process of how the Photo Metadata is extract


<img width="252" alt="Screenshot 2024-08-23 at 3 38 26 PM" src="https://github.com/user-attachments/assets/214b63cd-4e76-45d2-9bc7-09e485c9b7ca">

Figure 6 Project Editing Flow Chart: Shows the proccess of editing projects including changing names and tags

Test Plan


| Description                      | Type       | Inputs                               | Outputs                          | Details                                                                              | Test                                                                                                     |
|----------------------------------|------------|--------------------------------------|----------------------------------|--------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|
| User Uploads Photos              | Functional | Photo file                           | Success/Failure message          | Test different photo formats and sizes for upload                                    | Upload various photo formats (JPEG, PNG, etc.) and check for successful upload or error messages.        |
| User Adds Descriptions to Photos | Functional | Photo, Description text              | Success/Failure message          | Ensure descriptions can be added both after and during build sessions                | Add descriptions to photos and verify if descriptions are saved and displayed correctly.                 |
| Meta-Data Extraction from Photos | Functional | Photo file                           | Extracted meta-data (Date, Time) | Verify that meta-data is correctly extracted from photo files                        | Upload photos and check if the correct date and time meta-data are extracted and displayed.              |
| Project Management Organization  | Functional | Project updates, Categories          | Organized updates by category    | Ensure updates are correctly categorized by different parts of the house or projects | Add updates for various parts of the house and verify if they are categorized correctly in the system.   |
| Tag Operations for Projects      | Functional | Project tags (e.g., Tiling, Roofing) | Updated tag list                 | Test adding, editing, and removing tags                                              | Perform tag operations and verify if tags are updated and managed correctly.                             |
| Expense Tracking                 | Functional | Expense data (e.g., wood, tools)     | Expense summary by category      | Check if expenses are tracked and categorized correctly                              | Enter different expenses and verify if they are tracked and categorized accurately in the summary.       |
| Search and Filter Function       | Functional | Search keywords, Filter criteria     | Search results, Filtered data    | Ensure the search and filter functions return accurate results                       | Perform searches and apply filters to find specific updates or materials and check for accurate results. |
| Dashboard Progress Visualization | Functional | Project data (tasks, materials)      | Visual progress display          | Verify if the dashboard accurately reflects project status and upcoming needs        | Check if the dashboard correctly shows completed tasks, ongoing projects, and material needs.            |






| Task No | Planned Action                                        | Planned Outcome                                                                          | Design cycle | Time Estimate      | Completion date | Criterion |
|---------|-------------------------------------------------------|------------------------------------------------------------------------------------------|--------------|--------------------|-----------------|-----------|
| 1       | First interview with client                           | To understand client problem and requirements                                            | Planning     | 45 minutes         | June 1          | A         |
| 2       | Write down success criteria                           | To list down the first success criteria                                                  | Planning     | 60 minutes         | June 2          | A         |
| 3       | Write problem definition                              | Relisten to meeting and then write problem definition                                    | Planning     | 1 hour             | June 3          | A         |
| 4       | Finalise success criteria                             | Prepare a satisfactory criteria to present to client                                     | Planning     | 20 minutes         | June 3          | A         |
| 5       | Meet with the client to discuss the success criteria. | Receive final approval to start creating the application or any changes                  | Planning     | 20 minutes         | June 6          | A         |
| 6       | Review Changes and update success CRIT                | Reschedule Meeting to make sure clients needs are met                                    | Planning     | 30 minutes         | June 7          | A         |
| 7       | Create system diagram                                 | Develop a clear idea of the hardware and software requirements for the proposed solution | Planning     | 30 minutes         | Aug 19          | B         |
| 8       | Create ER diagram                                     | Create an ER diagram that illustrates the tables used and how they interact              | Design       | 30 Minutes         | Aug 20          | B         |
| 9       | Wire Frame Diagram                                    | Created the predicted Graphic User interface Vision for the application                  | Design       | 30 Minutes         | Aug 21          | B         |
| 10      | Complete Login/Registration Page                      | Create a function Login/Registration Page that has HTML templates                        | Design       | 40 min             | Aug 21          | B         |
| 11      | Produce Flow diagrams including descriptions          | Flow diagrams that explain a code functions                                              | Design       | 2 and a half hours | Aug 22          | B         |
|         |                                                       |                                                                                          |              |                    |                 |           |
|         |                                                       |                                                                                          |              |                    |                 |           |




# Criteria C : Documenting the development

## List of techniques used
- Flask Library/Routes
- HTTP - GET and POST requests
- Python/Jinja inside HTML
- CSS Styling
- SQLITE Databases
- If statements
- Variables
- Functions
- Token/ Sessions
- Hashing


# Memes database
The memes.database which is ran through the driver SQLlite stores all the information from memes to users information. To access/query/add/delete data I first need to connect to my program (python.file) with the database. The function `get_db` below connects to the database [^1] . It ensures that a single connection is used per request to avoid opening multiple connections to the database. 
```.py
def get_db():
    db = getattr(g, '_database', None) #defines the db as database, also utalizes an object provided by flask called g to store data during lifetime of request [^1]
    if db is None: #checks if there isn't a current database connection for request 
        db = g._database = sqlite3.connect(DATABASE)
        db.row_factory = sqlite3.Row
    return db
```
The next function I use disconnects from the database, ensuring that the connection is closed after each request is processed. [^1].

```.py

def close_connection(exception):
    db = getattr(g, '_database', None)
    if db is not None: # Checks if there is an existing database connection and if there is disconnected from Database
        db.close()
```
The pros of using a function is whenever you need to Query the data base you aren't repetetive with the connection and closing connection code. This also allows me to focus on the more complex and important aspects of the application, such as the user interface and functionality.

# CSS Styling
CSS (Cascade Style Sheet) styling allows you to have a standard format and presentation for the spacing of images/textboxs/headers/etc. In this project I utalized a premade template [^2]. 

# Base HTML
To maintain the same visual format within each page of the program the use of a html named base. This HTML file is the shell which all the other pages will be rendered from [^3]. In other words, it provides the same format for the header, depending if you're logged in the header will show login /register or Home/Add Meme/Logout/Profile. Within the base HTML Jinja is to give the url hyper links and for a if statement that if the user is logged in then only certain headers will appear.

Fig 1: LOGGED IN

<img width="432" alt="Screenshot 2024-05-25 at 8 09 26 PM" src="https://github.com/K-Schriber/Unit-4-Comp-Sci/assets/142757998/51d5dc01-78b5-4470-af81-2a3bd46cd2ad">


Fig 2: LOGGED OUT

<img width="539" alt="Screenshot 2024-05-25 at 8 09 19 PM" src="https://github.com/K-Schriber/Unit-4-Comp-Sci/assets/142757998/d90cfff6-689e-49da-9d28-1d9290c163cf">


```html
<!DOCTYPE html>
<html>
<head>
    <title>Flask Meme Manager</title>
    <link rel="stylesheet" type="text/css" href="{{ url_for('static', filename='style.css') }}">
</head>
<body>
    <header>
        <h1>Meme Manager</h1>
        {% if session.user_id %} 
        <nav>
            <a href="{{ url_for('home') }}">Home</a> # Top headers for the each page
            <a href="{{ url_for('manage_memes') }}">Add Meme</a> # Top headers for the each page
            <a href="{{ url_for('logout') }}">Logout</a> # Top headers for the each page
            <a href="{{ url_for('profile') }}">Profile</a>
        </nav>

        {% else %}
        <nav>
            <a href="{{ url_for('login') }}">Login</a>
            <a href="{{ url_for('register') }}">Register</a>
        </nav>
        {% endif %}
    </header>
    <main>
        
    </main>
</body>
</html>
```

# Session function
The session function stores information about a user's session across multiple requests. In the Flask application, cookies and sessions are closely related that the session data in this case `user_id` is stored in cookies. When you store information in the session object in Flask the data is serialized and placed into a cookie that is sent to the user's browser (Figure 3)[^6]. This session cookie is then included in all the next HTTP requests. By verifying the session cookie Flask can retrieve the stored session data. This ensures a secure and consistent user experience throughout the application [^6]. Through the entire application the Session function is checked after the function is called for maximum security.

The function 
```.py
@app.route('/')
def index():
    if not session.get('user_id'): # if the session is not user id then redirects for login
        return redirect(url_for('login'))
    return redirect(url_for('home')) #else it stays on home page
```

Figure 3: User Cookie: User_id Cookie = 1

<img width="451" alt="Screenshot 2024-05-27 at 8 39 02 AM" src="https://github.com/K-Schriber/Unit-4-Comp-Sci/assets/142757998/f4b3a37a-1594-4310-92e3-e53a28560b43">

# Flask App Routes
App routes is the framework for mapping the url destincations to functions. Specficallyin `@app.route` is a decorator used to map URL paths (endpoints) to view functions. The mapping determines what function should be called when the a specfic URL is requested by the user [^9]. The `app.route` also defines the methods that are allowed for the root such as GET and POST requests. For each page within the application there is an app route. An example of an app route python code in this application is below  which takes the user to the specfic meme the user has clicked on. The url is formated by /meme/(the meme id in the database) and can be seen below Figure 4:  

```.py
@app.route('/meme/<int:meme_id>', methods=['GET', 'POST'])
```

Figure 4: The url contains HTTP (Hypertext Transfer Protocol) which is used to communicate with the server. The next part of the URL is 127.0.0.1 which is the ip of the server address (THis id is special cause it's ran on a local server). The next section is the port where the server is waiting for requests in this case 5000 (Defeault port for flask development server). And finally, specific path to meme on the server (explained above).

<img width="228" alt="Screenshot 2024-05-30 at 2 03 27 PM" src="https://github.com/K-Schriber/Unit-4-Comp-Sci/assets/142757998/ad38050b-18a3-4dfd-914b-123cbbd6e29a">

# Succes Criteria 1: The application for the Meme Reddit has a login/register system
I have created a login/registration system that allows users to each have there own account by loggin in or registering if they don't have an account. 


## Registration
The first part of the process of the application is registering. To create the webserver page the url endpoint is called `/register`.  The following `registration` function allows new users to create an account by providing a username and password. When the user clicks submit it stores the user's entered information. This process of appending data to the database is a Post request in which data is saved to the server in this case the SQLLITE database. The program uses a try block to test if there are any errors in the entries and uses a except block to handle the error by returning the `sqlite3.IntegrityError`. The error is if the user already exists [^4]. The SQL query uses ? which is place holder for the values doing this changes the query into a parameterized query [^5]. In this type of query actual values are provided separately from the SQL statement itself this is done to prevent SQL Injections which is a web attack that uses malicious SQL code for backend database manipulation to access information that not intended to be displayed [^5]. Before the username and password are appended to the database the password is hashed for extra security. Hashing involves taking an input `password` and converting it into a fixed-size string of characters using a mathematical function. Figure 5: Registration page

The code for the registration system is below. I have provided comments next to the code to provide better understanding

```.py
@app.route('/register', methods=['GET', 'POST']) # defines the URL end point and the HTTP methods GET and POST
def register():
    error = None
    if request.method == ['POST']: 
        username = request.form['username'] # User inputs username into text box
        password = request.form['password'] # User inputs password into text box
    db = get_db() #connection to database
    try: # Runs the block of code within and checks to see if there is a repeated user if there is it goes to except block
        db.execute('INSERT INTO user (username, password) VALUES (?, ?)', # ? place holder values 
                   (username, generate_password_hash(password))) # Inserts the two values of username/ passowrd into placeholder values database hashing password
        db.commit()
        return redirect(url_for('login')) # Redirects user to Url route /Login
    except sqlite3.IntegrityError: # Brings up error and returns prompt to user
        error = 'Username already taken. Please choose another.'
    return render_template('register.html', error=error) # If errors returns to register template 

```
Figure 5: REGISTRATION PAGE

<img width="1511" alt="Screenshot 2024-05-27 at 9 10 54 AM" src="https://github.com/K-Schriber/Unit-4-Comp-Sci/assets/142757998/39ec58c0-f0d0-4c51-832a-47b96d029751">

## Login 
The login system works similary to the registration system except will only allow the user to login if there is an exsisting account. The login page asks the user to input username and password into two text boxes and has a submit button. Once the user clicks the submit button using an if statement if it sends a POST request. Then the username/password are saved in two variables and the the program connects to the database. The database then does a parameteraidsed query (Query for SQL injection prevention) to see if the username is located in the database. If it is then it checks if the provided password matches the hashed password stored in the database. If both match username/password match in database the users id is put into a session via `user_id` and the fucntion redirects the user to the home page. Else if they don't match the user is returned with an error. The HTML rendering of the login figure 6

Figure 6: LOGIN PAGE

<img width="1501" alt="Screenshot 2024-05-27 at 9 08 58 AM" src="https://github.com/K-Schriber/Unit-4-Comp-Sci/assets/142757998/f728564c-bf85-4fa4-80ab-8f7c8a5530f8">

Code for login page 
```.py
@app.route('/login', methods=['GET', 'POST'])
def login():
    error = None
    if request.method == 'POST':
        username = request.form['username']
        password = request.form['password']
        db = get_db()
        cur = db.execute('SELECT * FROM user WHERE username = ?', (username,))
        user = cur.fetchone()
        if user and check_password_hash(user['password'], password):
            session['user_id'] = user['id']
            return redirect(url_for('home'))
        else:
            error = 'Invalid Credentials. Please try again.'
    return render_template('login.html', error=error)
```

# Succes Criteria 2: A posting system to EDIT/CREATE/DELETE comments
The user is able to edit, create, and review comments under memes. This allows multiple users to add input about the meme.

## Adding Comment
The first part of the comments system is letting users be able to add comments. To add comments it uses a function called Meme details. The first step is connection to the database. Then it uses a if Statement to check if the the user has clicked the comments button and if it's a `POST` request. If it is it the users comment is saved into a variable called content and then a insert paramatized query is execute for three values `content`, `meme_id`, and `user_id`. After the values are commited (saved) to the table Comment the data bases closes and the meme.html is rendered.  A time stamp is also saved into the comments table to show when users made comments. However if the HTTP request is a `GET` request then the function gets the meme details along with all the associated comments. This first query fetches the details of a specific meme,  category name, and the username of its creator. The result is stored in the meme variable. The next query gets all comments associated with the specified meme and the username of each commenter. The results are stored in the `comments` variable. The meme detail HTML is then Rendered Figure 7. More details about the SQL queries are next to the code below.

```.py
@app.route('/meme/<int:meme_id>', methods=['GET', 'POST'])
def meme_detail(meme_id):
    if not session.get('user_id'):
        return redirect(url_for('login')) #Extra Security to make sure the User is in the right session
    
    db = get_db()
    if request.method == 'POST':
        content = request.form['content']
        db.execute('INSERT INTO comment (content, meme_id, user_id) VALUES (?, ?, ?)',
                   (content, meme_id, session['user_id']))
        db.commit()
        return redirect(url_for('meme_detail', meme_id=meme_id))
    
    cur = db.execute('SELECT meme.*, category.name as category_name, user.username as creator_name ' # Selects all columns from the meme table and selects the name column from the category table and renames it to category_name
                     'FROM meme '
                     'JOIN category ON meme.category_id = category.id ' #joins  the meme and category tables and matches rows so meme.category_id equals category.id
                     'JOIN user ON meme.created_by = user.id ' # joins meme and user tables and matches rows so meme.created_id equals user_id
                     'WHERE meme.id = ?', (meme_id,))
    meme = cur.fetchone()
    
    cur = db.execute('SELECT comment.*, user.username as commenter_name ' # selects all collums from table users
                     'FROM comment ' 
                     'JOIN user ON comment.user_id = user.id ' # joins the comment and user table matching rows  so comment.user_id = user.id
                     'WHERE comment.meme_id = ?', (meme_id,)) #filters the results so it only includes rows that match the meme_id
    comments = cur.fetchall()
    return render_template('meme_detail.html', meme=meme, comments=comments)
```


Figure 7: Add Comment System : The Comments display the user who created it and the time it was added. It also shows other users comments on the post

<img width="483" alt="Screenshot 2024-05-29 at 9 32 13 AM" src="https://github.com/K-Schriber/Unit-4-Comp-Sci/assets/142757998/e635ec8c-c307-4221-8465-5767b988f6df">

## Deleting Comment
The second part of the comment system is being able to the delete commements that the user has posted. Using a function called `delete_comment` the first process is connecting to the database then from using and paratized query to select the comment_id from the comments table. Using an if statement the program checks if the comment_id saved in the variable `comment` is eqaul to the `user_Id` of the session. If it is the comment is deleted from the comment table and the meme_detail page is rendered again. On the screen the user sees a delete button next to all there comments Figure 8:

```.py
@app.route('/delete_comment/<int:comment_id>', methods=['POST'])
def delete_comment(comment_id):
    db = get_db()
    cur = db.execute('SELECT * FROM comment WHERE id = ?', (comment_id,))
    comment = cur.fetchone()
    if comment and comment['user_id'] == session['user_id']:
        db.execute('DELETE FROM comment WHERE id = ?', (comment_id,))
        db.commit()
    return redirect(url_for('meme_detail', meme_id=comment['meme_id']))
```
Figure 8: Delete Comment button to delete comments from user

<img width="395" alt="Screenshot 2024-05-29 at 9 55 10 AM" src="https://github.com/K-Schriber/Unit-4-Comp-Sci/assets/142757998/d2a1ba31-bdd9-45b4-a58a-e2aa7d686928">

## Editing Comment
The final part of the comments system is the editing comments which allows users to edit posted comments changing the contents of it Figure 9. To make sure users can only edit there own comment I utalize and If statement that checks if there is no comments or if the Comment_user_id is eqaul to the session ID in one of the equirments are met it returns to home page. The next if statment checks if the User sends a POST request to the program [^7]. If so the function updates the `comment` in the comment table with the updates and redirects the user back to the meme detail page. Else if it is a GET request then the the function and renders the html page for editing the comment Figure 10.
```.py
def edit_comment(comment_id):
  
    db = get_db()
    cur = db.execute('SELECT * FROM comment WHERE id = ?', (comment_id,))
    comment = cur.fetchone()

    if not comment or comment['user_id'] != session['user_id']:
        return redirect(url_for('home'))

    if request.method == 'POST':
        content = request.form['content']
        db.execute('UPDATE comment SET content = ? WHERE id = ?', (content, comment_id))
        db.commit()
        return redirect(url_for('meme_detail', meme_id=comment['meme_id']))

    return render_template('edit_comment.html', comment=comment)

```

The editing HTML that is rendered allows the user to edit the comment. And change the get request to Post Request once they have clicked the edit comment button. In the HTML syntax the `form` element specfies that it should be submit using POST method. The URl for edit_comment and comment_id gets the url for the specfic meme through the uses of Jinja a web templant engine for pyhton. Jinja allows embedding Python-like expressions and control structures within your HTML templates such as if statements, loops, and compose different templates together using inheritance. The next part of the html synatx is the text box which uses jinja again to inserts the current content of the comment into the textarea when the form is rendered. The last element the button submits the form and runs it through the edit_comment fucntion but ths time as a Post request.

```.html
<h2>Edit Comment</h2>
<form method="post" action="{{ url_for('edit_comment', comment_id=comment.id) }}">
    <textarea name="content" required>{{ comment.content }}</textarea><br>
    <button type="submit">Update Comment</button>
</form>
```
Figure 9: The user is prompted in the Specfic meme page The choice to edit

<img width="412" alt="Screenshot 2024-05-29 at 2 54 12 PM" src="https://github.com/K-Schriber/Unit-4-Comp-Sci/assets/142757998/549fc312-b3b6-4e12-a5fe-6553a20bd776">

Figure 10: The user can edit the comment. Once they click Update sends POST request to the function edit comment.

<img width="267" alt="Screenshot 2024-05-29 at 2 54 18 PM" src="https://github.com/K-Schriber/Unit-4-Comp-Sci/assets/142757998/62616293-32c8-43b8-a48e-fd913e143c33">

# Succes Criteria 3: A system to add/remove likes
The application must have a way for users to like and unlike posts so users can tell what is popular and what is not. The like system works similiarly to the comment system. First connects to database then does a parmaterized query in the `like table` to check if the user has liked the meme based on the `meme_id` and the `user_id`. If there is no like that exists in the table then the program queries to insert a new like into the `like table`. If there is a like that exists in the table then the application uses a delete paramaterized query to delete the like. The meme detail HDML is then rendered.(Python Code) The meme_detail HDML (see HDML below) uses JINJA such as calling for the `like count`, which is a seperate function that uses a count querie through the like table to count the amount of likes. This is also seen when the the liking the meme creates a POST request utalizing jinja to get the URL. Following that the Jinja is used to rename the button if the user wishes to like (figure 11) or if they want to unlike (figure 12).  

## Python code
```.py
def like_meme(meme_id):
    db = get_db()
    cur = db.execute('SELECT * FROM like WHERE meme_id = ? AND user_id = ?', (meme_id, session['user_id']))
    if cur.fetchone() is None:
        db.execute('INSERT INTO like (meme_id, user_id) VALUES (?, ?)', (meme_id, session['user_id']))
    else:
        db.execute('DELETE FROM like WHERE meme_id = ? AND user_id = ?', (meme_id, session['user_id']))
    db.commit()
    return redirect(url_for('meme_detail', meme_id=meme_id))
```
## HTML syntax
```.html
<p><strong>Likes:</strong> {{ like_count }}</p>
<form method="post" action="{{ url_for('like_meme', meme_id=meme.id) }}">
    <button type="submit">{{ 'Unlike' if user_liked else 'Like' }}</button>
</form>
```

Figure 11: The user can like the post

<img width="341" alt="Screenshot 2024-05-29 at 7 56 30 PM" src="https://github.com/K-Schriber/Unit-4-Comp-Sci/assets/142757998/55b64e40-297f-48ed-8e05-f483782f73bb">

Figure 12: The user can unlike the post

<img width="313" alt="Screenshot 2024-05-29 at 7 56 38 PM" src="https://github.com/K-Schriber/Unit-4-Comp-Sci/assets/142757998/964886f6-002b-4377-9eaa-49cc3ea9b4f3">


# Succes Criteria 4: The application for the Meme Reddit has a system to follow/unfollow categories

The user is given 5 categories to select from to choose what memes show up on there home page feed. The five categories are managed under two functions `follow_category` and `unfollow_category`. When the user clicks a text box to follow the category the first function uses an SQL querie add an entry user category table to track the link between the user and category. Similiary, the second function when the user unclicks the catergories the entry from the table is removed.  The functions utalize the session data which has the `user_id` to track what users follow which categories. The use of the tools like SQL queries (to insert and delete rows), Session management(to stores users data across requests), and routes (to map the URL paths to view functions and the HTTP methods they use).

### Follow Category Function
```.py
@app.route('/follow/<int:category_id>', methods=['POST'])
def follow_category(category_id):
    if not session.get('user_id'):
        return redirect(url_for('login'))
    
    db = get_db()
    db.execute('INSERT INTO user_category_follow (user_id, category_id) VALUES (?, ?)', 
               (session['user_id'], category_id))
    db.commit()
    return redirect(url_for('home'))

```
### Unfollow Category Function
```.py
@app.route('/unfollow/<int:category_id>', methods=['POST'])
def unfollow_category(category_id):
    if not session.get('user_id'):
        return redirect(url_for('login'))
    
    db = get_db()
    db.execute('DELETE FROM user_category_follow WHERE user_id = ? AND category_id = ?', 
               (session['user_id'], category_id))
    db.commit()
    return redirect(url_for('home'))

```
As you can see both functions are extremely similiar in the type of HTTP methods they accept, session id check, and connecting to the database for an Parameterised SQL query. However, the queries are both differant with one INSERTing values into the table and the other DELETing values then they both render the home page HTML. Which shows all the memes under the categories the user selected.

```.py
if followed_categories:
        query = f'''
            SELECT meme.*, category.name as category_name, user.username as creator_name 
            FROM meme 
            JOIN category ON meme.category_id = category.id 
            JOIN user ON meme.created_by = user.id
            WHERE category.id IN ({placeholders})
            '''
 cur = db.execute(query, followed_categories)
```

This if statment above takes all the memes under the catergories the user follows

Part of the home HTML is below which utalizes Jinja to use for loops and if statements to check if the user follows the categories. If they do the next for loop look goes through the memes of the SQL query above and displays all memes of the catergory the user follows showing the Meme detail link, caterogy its under, and the meme creator name Figure(13). Helpful comments on the side of the HTML syntax to better understand the processs

```.html
{% for category in categories %} #goes through categories user follow
        <div>
            <strong>{{ category.name }}</strong>
            {% if category.id in followed_categories %}
                <form method="post" action="{{ url_for('unfollow_category', category_id=category.id) }}" style="display:inline;">
                    <button type="submit">Unfollow</button> #displays unfollow button and also tell system to run UNfollow function above
                </form>
            {% else %}
                <form method="post" action="{{ url_for('follow_category', category_id=category.id) }}" style="display:inline;">
                    <button type="submit">Follow</button> #displays follow button and also tell system to run follow function above
                </form>
            {% endif %}
        </div>
    {% endfor %}
{% for meme in memes %} #goes through erach meme in category user follows
    <li>
        <h3><a href="{{ url_for('meme_detail', meme_id=meme.id) }}">{{ meme.title }}</a></h3>
        <p><strong>Category:</strong> {{ meme.category_name }}</p>
        <p><strong>Created by:</strong> {{ meme.creator_name }}</p>
        <img src="{{ meme.image_url }}" alt="{{ meme.title }}" width="300">
    </li>
    {% endfor %}
```
Figure 13: The home menu. Options for users to follow categories and shows memes.

<img width="561" alt="Screenshot 2024-05-31 at 8 24 20 AM" src="https://github.com/K-Schriber/Unit-4-Comp-Sci/assets/142757998/ca73ba6c-1198-4e6d-a341-1f6c4c01810b">

# Succes Criteria 5: The application for the Meme Reddit has a profile page with relevant information

 I have created the profile page so when users click the page they get all the relevent informatuion related to their account. The profile page shows the Username, the memes created, the comments made, and the categories the user follows Figure 14, figure 15. This is done through multiple SQL queries that select all the Memes, comments, and categories based session `user_id` and then display . One of the many similiar sql queries is below with comments next to it to provide a better understanding. The qqueries all select 

 ```.py
user = db.execute('SELECT * FROM user WHERE id = ?', (user_id,)).fetchone() # Fetch user details * selects all the collums 

memes = db.execute('SELECT * FROM meme WHERE created_by = ?', (user_id,)).fetchall() # Fetch memes created by the user based on user id * selects all the collums where userid matches with session id

comments = db.execute('SELECT comment.*, meme.title as meme_title FROM comment '
                      'JOIN meme ON comment.meme_id = meme.id WHERE comment.user_id = ?', (user_id,)).fetchall() # Fetch comments made by the user * selects all the collums 
```

 


Figure 14: Shows the username and the memes the user has uploaded

<img width="565" alt="Screenshot 2024-05-31 at 8 42 14 AM" src="https://github.com/K-Schriber/Unit-4-Comp-Sci/assets/142757998/8ccf790d-70d7-40f4-bac7-c228c6a43389">


Figure 15: Shows the comments made on posts and the categories the user follows

<img width="525" alt="Screenshot 2024-05-31 at 8 42 19 AM" src="https://github.com/K-Schriber/Unit-4-Comp-Sci/assets/142757998/5eab1e16-082c-4b3e-b3af-6c9b3f6041b4">


# Succes Criteria 6: The application for the Meme Reddit allows users to upload images

The final criteria is the ability for the user to upload memes to the meme reddit. This done through the `add_meme` function. The function only works if the user clicks the submit button sending a POST request and submits the fields required which are the title of the meme, Image Url of the meme, and the category field it falls under. The page that is rendered is what the user sees this when uploading a meme (figure 16). 


```.py
def add_meme():
    if request.method == 'POST':
            title = request.form['title']
            image_url = request.form['image_url']
            category_id = request.form['category_id']
            
            db = get_db()
            db.execute('INSERT INTO meme (title, image_url, created_by, category_id) VALUES (?, ?, ?, ?)',
                       (title, image_url, session['user_id'], category_id))
            db.commit()
            return redirect(url_for('home'))
       
        
        return render_template('add_meme.html')
```


Figure 16: The fields for adding a meme

<img width="1507" alt="Screenshot 2024-05-31 at 9 05 29 AM" src="https://github.com/K-Schriber/Unit-4-Comp-Sci/assets/142757998/3bb8cdb4-b84c-4d2d-b646-cd2e9e7a02b6">

Once the meme is added to the database with its image URL it can be displayed on the home page or profile page using the image URL and html synatx below. It uses Jinja to call the variables `meme.category_name`, `meme.creator_name`, and using an image tag `<img>` displays the variable `meme.image_url` with the variable title `meme.title`.  The rendered home page with memes is below (figure 17).


Figure 17: The rendered home page with memes

<img width="929" alt="Screenshot 2024-05-31 at 1 35 24 PM" src="https://github.com/K-Schriber/Unit-4-Comp-Sci/assets/142757998/098f27bf-00a5-46fc-a0ba-299670e9dfcf">



```.html
<p><strong>Category:</strong> {{ meme.category_name }}</p> #tag <p> starts paragraph
        <p><strong>Created by:</strong> {{ meme.creator_name }}</p> # tag <strong> makes it bold
        <img src="{{ meme.image_url }}" alt="{{ meme.title }}" width="300">
```


# Computational Thinking
Computational Thinking is a problem-solving technique requires programmers to break down complex problems and scenarios into bite size pieces that can be fully understood in order to then develop solutions that are clear to both computers and humans [^10]. This is done through Decomposition, Abstraction, Pattern Recognition, and Algorithm Design. 

## Decomposistion
Decomposition is the process of breaking down a problem or challenge – even a complex one – into small, manageable parts [^10]. This is done throughout my application via routes. Each route handles a specfic part of the functionaliy. For example the home route displays the home page with memes or the profile page displays the users profile. Additionally, each HTML is organised via a template base which allows for easier to manage the presentation of the page.

## Abstraction
Abstraction requires to focus only on the most important information and elements of the problem, and to ignore anything else, particularly irrelevant details or unnecessary details.[^10] One example within my application the database connection function is abstracted into helper function(Reduce Redundency) `get_db` which connects to database. Also session management is broken down into helper functions that check if the user session ID is correct or redirected them to the login page.  

## Pattern Recognition
Pattern Recognition is identifying similarities or patterns among smaller problems. This can help solve complex problems more efficiently by reusing solutions [^10]. In my application the use of SQL queries to gather data about the user such as meme posted, comments, userid, and more are frequently reused in differant pages. Additionally using if statments to check the method REQUESTs and error handling or incorrectly entered forms is also reused. 

## Algorithm Design
Algorithm Design involves creating a step-by-step procedure to solve a problem [^10]. In the application almost everyn function uses a step by step procedure. One of them is the login system which first collects username and password from the login form, next checks if the user exists and retrieve their stored password hash, next compare the entered password with the stored hash, then if the password is correct, store the user ID in the session, or redirect the user to the profile page or show an error message if authentication fails.


# Criteria D: Appendix

1. Audio File From Orginal Meeting With client : https://drive.google.com/file/d/14s_D84gPGZhhtRZJzvpFrEU4pIIoE1hL/view?usp=sharing


## Sources Cited
1. Gupta, A. (2024). Top 10 reason why you should learn python in 2023. Retrieved from https://www.simplilearn.com/tutorials/python-tutorial/why-learn-python 
2. Learn enough to be dangerous. (n.d.). Retrieved from https://www.learnenough.com/blog/10-Companies-Using-Python-In-2023-&-Why-It’s-Their-Go-To#:~:text=Python%20has%20grown%20in%20favor,a%20basic%20knowledge%20of%20coding. 
3. 6 reasons why flask is better framework for web application development. (n.d.). Retrieved from https://able.bio/hardikshah/6-reasons-why-flask-is-better-framework-for-web-application-development--cd398f73 
4. Mahalias, I. (2024). Why should you use flask: 7 reasons. Retrieved from https://www.planeks.net/why-use-flask/
5. Programming Foundations: Databases Online Class: LinkedIn Learning, formerly Lynda.com. (n.d.). Retrieved from https://www.linkedin.com/learning/programming-foundations-databases-2 
7. Hayes, A. (n.d.). Blockchain facts: What is it, how it works, and how it can be used. Investopedia. https://www.investopedia.com/terms/b/blockchain.asp 
8. Golubev, S. (n.d.). The expansion of Decentralized Finance (DEFI) on the Ethereum Network. LinkedIn. https://www.linkedin.com/pulse/expansion-decentralized-finance-defi-ethereum-network-sergey-golubev 
9. CoinMarketCAP. (n.d.). Ethereum Price Today, ETH to USD live price, marketcap and Chart. CoinMarketCap. https://coinmarketcap.com/currencies/ethereum/ 


