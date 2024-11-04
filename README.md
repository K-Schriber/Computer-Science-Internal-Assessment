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

![Comp-36 2](https://github.com/user-attachments/assets/4511afb5-fe17-4f3c-9fec-177f7ea85976)



Figure 1 This diagram shows a client-server system. The client side is a MacBook Pro running a Python-based project management site with a GUI. It communicates with a MySQL database on the server side through HTTP requests over Ethernet. The system manages construction projects with backend storage and frontend interaction. 
<img width="649" alt="Screenshot 2024-08-23 at 9 52 53 AM" src="https://github.com/user-attachments/assets/cf091ac1-e918-4c35-82a9-a1088e718af9">

Figure 2 WireFrame diagram for Constuction App showcasing all the success criteria. 



<img width="919" alt="Screenshot 2024-09-23 at 10 46 29 AM" src="https://github.com/user-attachments/assets/3d73ae5f-0d86-4692-ad5e-3324069e8f01">



Figure 3 ER Diagram of the construction Application. This diagram depicts the database structure used to store the phots, projects, comments, and users of the application. It also shows the relationsships between tables.A 1-to-1 relationship exists between build_session and photo, where each build session can have one photo. 1-to-many relationships include a project having multiple tasks and build_sessions, and each build_session having multiple build_session_costs. There are also many-to-many relationships, such as between project and tag through the project_tags table, where a project can have many tags and a tag can belong to many projects. 


<img width="1192" alt="Screenshot 2024-09-23 at 11 00 52 AM" src="https://github.com/user-attachments/assets/b35387c9-09f9-4e58-a601-160f747329c6">


Figure 4: An example of the table photos. This includes ID, project_id, filename,description, upload_date, and date_taken.


<img width="450" alt="Screenshot 2024-09-23 at 10 47 36 AM" src="https://github.com/user-attachments/assets/5a227abc-06c8-423b-8a7b-ed5db2a568cc">



Figure 5 Login Flow Chart; Flow chart shows the process for USer to login

<img width="269" alt="Screenshot 2024-09-23 at 10 54 48 AM" src="https://github.com/user-attachments/assets/3ba52da4-ddc0-495a-8b48-ec9ce6afc9a1">



Figure 6 EXIF Image data Flow Chart: Shows the process of how the Photo Metadata is extract


<img width="290" alt="Screenshot 2024-09-19 at 11 02 07 PM" src="https://github.com/user-attachments/assets/f8b1a562-7f91-4c42-96e1-9116b6387078">


Figure 7 Project Editing Flow Chart: Shows the proccess of editing projects including changing names and tags

Test Plan


| **Test No.** | **Success Criterion**                                                                                            | **Procedure**                                                                                                                                     | **Expected Outcome**                                                                                                                                        | **Date**   |
|--------------|------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|
| 1            | The website allows users to upload photos.                                                                       | Log in, navigate to the "Upload Photo" section, select a photo to upload, enter a description, and click "Submit."                                | The photo is stored in the database with the entered description, and it appears in the associated project or build session view.                           | 11/04/2024 |
| 2            | Users can add descriptions to photos after each build session or anytime thereafter.                             | Log in, navigate to a previously uploaded photo, click "Edit Description," enter a new description, and save changes.                             | The photo's description is updated in the database. If the photo lacks a description, the website prompts the user to add one.                              | 11/04/2024 |
| 3            | The website extracts metadata from photos to record specific dates and times when photos were taken.             | Upload a photo with metadata (e.g., a taken date in EXIF data). Then, view the photo’s details page.                                              | The photo’s metadata (e.g., "DateTimeOriginal") is automatically extracted and stored in the database, displaying the taken date on the photo details page. | 11/04/2024 |
| 4            | The website includes a project management feature for categorizing updates by parts of the house or projects.    | Log in, go to the "Create Project" page, enter a project name (e.g., "Roofing"), and save. Then, navigate to the "View Project" page.             | The project appears in the project management dashboard, organized by the specified category (e.g., "Roofing").                                             | 11/04/2024 |
| 5            | The website allows CRUD operations on projects, build sessions, and photos.                                      | Log in and go to "Projects" page. Create a project, update the project details, add a build session, upload a photo, and then delete the project. | The created project, session, and photo are saved in the database. After deletion, all related data is removed from the database.                           | 11/04/2024 |
| 6            | The website tracks expenses across different categories.                                                         | Log in, navigate to the "Add Expense" section, select a project, enter expense details (e.g., "#wood" or "#tools"), and click "Submit."           | The expense is stored in the database, categorized under the specified tag (e.g., "#wood"), and appears on the expense summary page for tracking.           | 11/04/2024 |
| 7            | The website provides a search and filter function for finding updates or materials by date, project, or keyword. | Log in, navigate to the search page, enter a keyword or date range, and filter by a specific project.                                             | The search results show only updates that match the specified date, project, or keyword, efficiently displaying relevant information.                       | 11/04/2024 |
| 8            | The website includes a dashboard displaying construction progress with completed tasks and ongoing projects.     | Log in, navigate to the "Dashboard" page. Add tasks to a project, mark some tasks as complete, and check the dashboard for progress updates.      | The dashboard visually shows project progress, with indicators for completed tasks and ongoing projects.                                                    | 11/04/2024 |



| Task No | Planned Action                                                   | Planned Outcome                                                                               | Design cycle | Time Estimate | Completion date | Criterion |
|---------|------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|--------------|---------------|-----------------|-----------|
| 1       | Conduct first interview with client (Planning)                   | To understand client problem and requirements                                                 | Planning     | 45 minutes    | June 1          | A         |
| 2       | Write down success criteria (Planning)                           | To list down the first success criteria                                                       | Planning     | 60 minutes    | June 2          | A         |
| 3       | Write problem definition (Planning)                              | Relisten to meeting and then write problem definition                                         | Planning     | 1 hour        | June 3          | A         |
| 4       | Finalize success criteria (Planning)                             | Prepare a satisfactory criteria to present to client                                          | Planning     | 20 minutes    | June 3          | A         |
| 5       | Meet with client to discuss success criteria (Planning)          | Receive final approval to start creating the application or any changes                       | Planning     | 20 minutes    | June 6          | A         |
| 6       | Review changes and update success criteria (Planning)            | Reschedule meeting to ensure clients' needs are met                                           | Planning     | 30 minutes    | June 7          | A         |
| 7       | Create system diagram (Planning)                                 | Develop a clear idea of the hardware and software requirements for the proposed solution      | Planning     | 30 minutes    | Aug 19          | B         |
| 8       | Create ER diagram (Design)                                       | Create an ER diagram that illustrates the tables used and how they interact                   | Design       | 30 minutes    | Aug 20          | B         |
| 9       | Create wireframe diagram (Design)                                | Create the predicted Graphic User Interface vision for the application                        | Design       | 30 minutes    | Aug 21          | B         |
| 10      | Complete Login/Registration page (Design)                        | Create a functional login/registration page with HTML templates                               | Design       | 40 minutes    | Aug 21          | B         |
| 11      | Produce flow diagrams including descriptions (Design)            | Create flow diagrams that explain code functions                                              | Design       | 2.5 hours     | Aug 22          | B         |
| 12      | Develop photo upload functionality (Development)                 | Implement a feature where users can upload photos and store them in the database              | Development  | 1 hour        | Aug 23          | C         |
| 13      | Add description prompt for photos (Development)                  | Ensure the system prompts users to add descriptions to their uploaded photos                  | Development  | 45 minutes    | Aug 29          | C         |
| 14      | Implement metadata extraction for photos (Development)           | Automate extraction of photo metadata like timestamps during the upload process               | Development  | 1 hour        | Sep 2         | C         |
| 15      | Create project management feature (Development)                  | Implement a feature that categorizes updates by house parts or project type                   | Development  | 2 hours       | Sep 7          | C         |
| 16      | Implement CRUD operations for project components (Development)   | Add functionality to create, read, update, and delete tags, projects, and photos              | Development  | 3 hours       | Sep 14          | C         |
| 17      | Expense tracking functionality (Development)                     | Implement a feature to track and categorize expenses for materials and tools                  | Development  | 2 hours       | Sep 18          | C         |
| 18      | Develop search and filter functionality (Development)            | Create a search feature to find updates or materials by date, project, or keyword             | Development  | 1 hour        | Sep 21          | C         |
| 19      | Build dashboard for project progress visualization (Development) | Create a dashboard to display construction progress, highlighting completed and ongoing tasks | Development  | 3 hours       | Sep 21          | C         |



# Criteria C : Documenting the development

## List of techniques used
- Flask Library/Routes
- HTTP - GET and POST requests
- Python/Jinja inside HTML
- CSS Styling
- SQLAlchemy ORM (Object Relational Mapping):
	- Models
	- Relationships
	- Cascading:
- Token/ Sessions
- Hashing


# Succes Criteria 1 and 2: 

The website allows users to upload photos. (Issue Tackled: Photo management and documentation)

The website allows users to add descriptions to the photos after each build session and anytime after that, prompting the user if a photo doesn't have a comment. (Issue Tackled: Ensuring descriptive metadata and improving photo context)




Within the application, the user can upload photos anytime throughout the session. Using the * class Photos *, an SQLAlchemy model is utilized to represent the photos associated with projects or build sessions in the database. In SQLAlchemy, Object Relational Mapping (ORM) is used to define how different tables relate to each other. Within the *Photo model*, there are two important relations, aka foriegn keys, project and build session. *project_id* defines a many-to-one relationship between the photos and the project. For example, the project can have many associated photos, but each photo belongs to only one project. Similarly, this is the case ‘session_id’, where many photos can belong to a build session. 

While uploading photos, the user can include a description of the photo Figure1 . If the user forgets to add a description of the photo, the system will prompt the user to review the photo Figure(2). While reviewing the photo, the user can also edit any other existing photo descriptions Figure (3). Using the class *Photo*, we can easily query the database for the photo based on the photo ID. If the user clicks edit photo, it sends a post request to the server, in turn prompting the user to input the description change. It then checks that the user didn't leave the description empty and saves it to the database Figure(4).







Figure(1) shows graphic user interface for photo upload


Figure (2) Once the photo is uploaded without a description it prompts the user to input description







Figure (3) Shows all the photos for the project/build project as well as the ability to edit or delete 
```.py
def edit_photo(photo_id):
   photo = Photo.query.get_or_404(photo_id)
   if request.method == 'POST':
       description = request.form['description']
       if not description:
           flash('Description cannot be empty.', 'warning')
       else:
           photo.description = description
           db.session.commit()
           flash('Photo description updated successfully!')
       return redirect(url_for('view_project_photos', project_id=photo.project_id))


   return render_template('edit_photo.html', photo=photo)
Figure(4) The edit photo function


```



# Succes Criteria 3: 

The website extracts meta-data from photos to keep track of specific dates and times when photos were taken. (Issue Tackled: Automatic tracking of photo timestamps)




The *get_exif_data* function extracts EXIF (Exchangeable Image File Format) data from an image Figure(5). EXIF data includes metadata such as the camera settings, the date and time the photo was taken, and other details embedded within the image file by the camera. Using Pillow's image processing library, we can get the EXIF data from each photo. Then, using the *get_photo_date* function, we can scrap the date and time for the photo figure(6).
```.py

def get_exif_data(image):
   """Extract EXIF data from an image."""
   exif_data = {}
   try:
       info = image._getexif()  
       if info:
           for tag, value in info.items():
               decoded = ExifTags.TAGS.get(tag, tag)  
               exif_data[decoded] = value
   except AttributeError:
       pass 
   return exif_data

```
Figure (5) The EXIF data function

```.py

def get_photo_date(exif_data):
   """Extract the 'DateTimeOriginal' from EXIF data."""
   return exif_data.get('DateTimeOriginal', None)


```
Figure(6) Exif data Date extraction Function




To do this Photo class is then called to create a new photo entry. The credentials, photo ID, build_session ID, file_name, description, and the newly extracted metadata are saved to the database Figure(7). There is a fall back in case there is no metadata for the photo in which the time of upload is used. The resulting photos are shown in Figure(8)


```.py
new_photo = Photo(
   project_id=session.project_id,
   build_session_id=session.id,
   filename=filename,
   description=description,
   uploaded_at=photo_date or datetime.utcnow()  
)
db.session.add(new_photo)

```
Figure (7): The queries that save photos into the data base.



Figure(8): The photo with the Time stamp as well as the date uploaded


# Succes Criteria 4: The website includes a project management feature that organizes and categorizes updates by different parts of the house or specific projects. (Issue Tackled: Project organization and categorization)




When creating a new project the user has the choice to create multiple projects depending on various sub projects for construction figure (9). The user is prompted to enter tags associated with each project. Using jinja which allows python functions inside html files, the tags queried through using a if-else conditional block Figure(10). If a tag exists it will be displayed in the drop down table otherwise no tags will so Figure(10). The projects are then all layed out for the user to choose from. Figure(11)


Figure (9) Shows the project creation page where all the details related to the project go.

```.html
{% if tags %}
   <select multiple class="form-select" id="tags" name="tags">
       {% for tag in tags %}
           <option value="{{ tag.id }}">{{ tag.name }}</option>
       {% endfor %}
   </select>
   <small class="form-text text-muted">Hold Ctrl (or Cmd on Mac) to select multiple tags.</small>
{% else %}
   <p class="text-muted">No tags available. <a href="{{ url_for('create_tag') }}">Create a new tag</a>.</p>
{% endif %}



```
Figure(10)



Figure (11) The users project dashboard




# Succes Criteria 5: The website allows CRUD operations on projects, build sessions, and photos (e.g., Tiling, Roofing). (Issue Tackled: Management for project specifics as well as project)


For each creatable project, build sessions, and photo there is a way that the user can Create, Read, Update, or Delete the contents. 

For these examples, I will explain the build session functionality. The user is prompted to create a new build session under a project Figure(12). When the user clicks submit the first step is connecting to the database which is done using ORM under the class Project Figure(13). Next is checking if the user submits a HTTP post request, if so the data that the user answered is committed to database and the project home page is rendered Figure(13).



Figure(12) Build Session Creation 

```.py
def create_build_session(project_id):
   project = Project.query.get_or_404(project_id)
   if request.method == 'POST':
       description = request.form['description']
       new_session = BuildSession(project_id=project.id, description=description)
       db.session.add(new_session)
       db.session.commit()
       flash('Build session created successfully!')
       return redirect(url_for('view_project', project_id=project.id))


   return render_template('create_build_session.html', project=project)

```
Figure (13) Build Session Creation function using ORM






The build session can be clicked on a separate route and pull up a page dedicated to the build session with the route *'/view-build-session/<int:session_id>'*. On this page the user can view the description of the build session as well as upload any photos or costs figure(14).








Figure(14) Build Session View


Deleting or editing a build session is an option within the project page. For deleting, using the BuildSession object, we can easy query the database based on the *Build Session* id then using ORM's  ‘db.session.delete(session)’ method. The build session is then deleted. For editing the session the *Buildsession* object is queried by the session ID. It then generates a form that allows the user to edit the description. Figure(15). The code then checks once the user submits sending a post request and saving the new description into the database Figure (16).



Figure(15) Form that allows user to edit build session description

```.py
def edit_build_session(session_id):
   session = BuildSession.query.get_or_404(session_id)
   if request.method == 'POST':
       session.description = request.form['description']
       db.session.commit()
       flash('Build session updated successfully!')
       return redirect(url_for('view_project', project_id=session.project_id))


   return render_template('edit_build_session.html', session=session)
```

Figure(16) The Edit Build Session Function


# Succes Criteria 6: A The website tracks expenses across different categories (e.g., #wood, #tools, Total spending)

Within each build session, the user can input the amount spend on that build session as well as under one of the four categories as well as a description Figure (17). The costs are then displayed on the build session page as well as the total amount spent on the build session using a for loop that cycles through each costs and sums the total Figure(18) .

Figure (17) Creation of Cost for build Session

```py
total_cost = sum(cost.amount for cost in costs)
```
Figure (18) For Loop for total costs of build sessions


# Succes Criteria 7: A The website provides a search and filter function to quickly find specific updates or material information by date, project, or keyword. (Issue Tackled: Efficient information retrieval)


To allow the user to search all projects, build session, or photos, I implemented a search feature that allows the user to type in key words.


```.py
def search():
   project_name = request.args.get('project', '').strip()
   keyword = request.args.get('keyword', '').strip()
   start_date = request.args.get('start_date', '')
   end_date = request.args.get('end_date', '')


   query = BuildSession.query.join(Project).filter()


   # Filter by project name
   if project_name:
       query = query.filter(Project.name.ilike(f"%{project_name}%"))


   # Filter by keyword in description
   if keyword:
       query = query.filter(BuildSession.description.ilike(f"%{keyword}%"))


   # Filter by date range
   if start_date:
       query = query.filter(BuildSession.date >= start_date)
   if end_date:
       query = query.filter(BuildSession.date <= end_date)


   # Execute the query
   results = query.all()


   return render_template('search.html', results=results)
```
Figure (19) 





| Task No | Planned Action                                                   | Planned Outcome                                                                               | Design cycle | Time Estimate | Completion date | Criterion |
|---------|------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|--------------|---------------|-----------------|-----------|
| 1       | Conduct first interview with client (Planning)                   | To understand client problem and requirements                                                 | Planning     | 45 minutes    | June 1          | A         |
| 2       | Write down success criteria (Planning)                           | To list down the first success criteria                                                       | Planning     | 60 minutes    | June 2          | A         |
| 3       | Write problem definition (Planning)                              | Relisten to meeting and then write problem definition                                         | Planning     | 1 hour        | June 3          | A         |
| 4       | Finalize success criteria (Planning)                             | Prepare a satisfactory criteria to present to client                                          | Planning     | 20 minutes    | June 3          | A         |
| 5       | Meet with client to discuss success criteria (Planning)          | Receive final approval to start creating the application or any changes                       | Planning     | 20 minutes    | June 6          | A         |
| 6       | Review changes and update success criteria (Planning)            | Reschedule meeting to ensure clients' needs are met                                           | Planning     | 30 minutes    | June 7          | A         |
| 7       | Create system diagram (Planning)                                 | Develop a clear idea of the hardware and software requirements for the proposed solution      | Planning     | 30 minutes    | Aug 19          | B         |
| 8       | Create ER diagram (Design)                                       | Create an ER diagram that illustrates the tables used and how they interact                   | Design       | 30 minutes    | Aug 20          | B         |
| 9       | Create wireframe diagram (Design)                                | Create the predicted Graphic User Interface vision for the application                        | Design       | 30 minutes    | Aug 21          | B         |
| 10      | Complete Login/Registration page (Design)                        | Create a functional login/registration page with HTML templates                               | Design       | 40 minutes    | Aug 21          | B         |
| 11      | Produce flow diagrams including descriptions (Design)            | Create flow diagrams that explain code functions                                              | Design       | 2.5 hours     | Aug 22          | B         |
| 12      | Develop photo upload functionality (Development)                 | Implement a feature where users can upload photos and store them in the database              | Development  | 1 hour        | Aug 23          | A         |
| 13      | Add description prompt for photos (Development)                  | Ensure the system prompts users to add descriptions to their uploaded photos                  | Development  | 45 minutes    | Aug 24          | B         |
| 14      | Implement metadata extraction for photos (Development)           | Automate extraction of photo metadata like timestamps during the upload process               | Development  | 1 hour        | Aug 25          | C         |
| 15      | Create project management feature (Development)                  | Implement a feature that categorizes updates by house parts or project type                   | Development  | 2 hours       | Aug 26          | A         |
| 16      | Implement CRUD operations for project components (Development)   | Add functionality to create, read, update, and delete tags, projects, and photos              | Development  | 3 hours       | Aug 27          | B         |
| 17      | Expense tracking functionality (Development)                     | Implement a feature to track and categorize expenses for materials and tools                  | Development  | 2 hours       | Aug 28          | A         |
| 18      | Develop search and filter functionality (Development)            | Create a search feature to find updates or materials by date, project, or keyword             | Development  | 1 hour        | Aug 29          | A         |
| 19      | Build dashboard for project progress visualization (Development) | Create a dashboard to display construction progress, highlighting completed and ongoing tasks | Development  | 3 hours       | Aug 30          | A         |


## Sources Cited
1. Gupta, A. (2024). Top 10 reason why you should learn python in 2023. Retrieved from https://www.simplilearn.com/tutorials/python-tutorial/why-learn-python 
2. Learn enough to be dangerous. (n.d.). Retrieved from https://www.learnenough.com/blog/10-Companies-Using-Python-In-2023-&-Why-It’s-Their-Go-To#:~:text=Python%20has%20grown%20in%20favor,a%20basic%20knowledge%20of%20coding. 
3. 6 reasons why flask is better framework for web application development. (n.d.). Retrieved from https://able.bio/hardikshah/6-reasons-why-flask-is-better-framework-for-web-application-development--cd398f73 
4. Mahalias, I. (2024). Why should you use flask: 7 reasons. Retrieved from https://www.planeks.net/why-use-flask/
5. Programming Foundations: Databases Online Class: LinkedIn Learning, formerly Lynda.com. (n.d.). Retrieved from https://www.linkedin.com/learning/programming-foundations-databases-2 
7. Hayes, A. (n.d.). Blockchain facts: What is it, how it works, and how it can be used. Investopedia. https://www.investopedia.com/terms/b/blockchain.asp 
8. Golubev, S. (n.d.). The expansion of Decentralized Finance (DEFI) on the Ethereum Network. LinkedIn. https://www.linkedin.com/pulse/expansion-decentralized-finance-defi-ethereum-network-sergey-golubev 
9. CoinMarketCAP. (n.d.). Ethereum Price Today, ETH to USD live price, marketcap and Chart. CoinMarketCap. https://coinmarketcap.com/currencies/ethereum/ 


