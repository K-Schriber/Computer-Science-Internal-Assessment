A competent engineer constructing a house in Japan seeks a solution to organize his construction progress tracking. Currently, he manually documents each build session in a spreadsheet with photos and descriptions, which leads to disorganization and difficulty in accessing specific information. Originally, the client has been taking a picture and then writing a brief description. However, over time, the client has just taken photos without writing descriptions and is planning to go back in the future and write a description. This also makes it very difficult to find photos/receipts for different parts of the house. This has led to an overwhelming number of photos without descriptions, creating an unorganized system. Receipts have also been piling up, making it hard to track the total expenses for each project within the house. An in the appendix about the meeting.


# Rationale for Proposed Solution

To address this, I proposed a system that automates photo uploads, prompts for descriptions, and extracts metadata for date and time tracking. Additionally, the website should offer project management tools, including categorization by house sections and project types. It should enable easy tagging and tracking of expenses, along with robust search and filter functions for quick access to updates and material information. Lastly, the client seeks a dashboard displaying construction progress visually, highlighting completed tasks, ongoing projects, and material needs.



I propose using Python over other programming languages for three key reasons. Firstly, Python is a highly influential language with versatile libraries and frameworks to cater to various needs. Meaning that no matter the project, python will have a library suitable to create your dream [1]. Next, due to Python’s high-level nature and extensive libraries that allow for the development of features quickly. This means that prototypes can be developed faster ensuring that the product meets the client's needs [2]. Finally, python is extremely flexible as it integrates well with other systems and technologies[2]. This can be helpful in future large-scale projects, or if you want to develop the application further. 

Additionally, I propose using Flask, a web development framework, instead of other web frameworks for its clear navigation and customizable user experience. Flask’s straightforward framework allows for an application with a clear and user-friendly navigation system, ensuring that customers can easily interact with the application[3]. The flexible structure of Flask allows for easy implementation of customized features, creating an engaging experience for the user[4]. Features such as distinctive design or unique functionalities allow for an application that precisely matches the customer's preferences. 

Furthermore, I propose using a database to manage the construction application. Databases offer robust security features to protect sensitive information, ensuring that no unauthorized users can access your data [5]. As you continue to add to your projects, so will the amount of data. Databases are designed to handle large amounts of data effectively, which is why they are perfect for this application [5].











## Success Criteria Proof of Meeting Appendix: 1
1. A The website allows user to upload photos.
1. B The website allows user to add descriptions to the photos after each build session and anytime after. Prompting user if Picture doen't have comment.
1. C The website takes Meta-Data from photo to keep track of the specific dates and times of updates that photos were taken. 
2. A The website includes a project management feature that organizes and categorizes updates by different parts of the house or specific projects.
2. B The webstie allows crude operations on tags for specfic projects (example Tiling, Roofing, etc)
3. A The website tracks expenses on differant categories (example #wood, #tools, Total spending)
4. A The website provides a search and filter function to quickly find specific updates or materials information by date, project, or keyword.
5. A The website includes a dashboard that visually displays the progress of the construction, highlighting completed tasks, ongoing projects, and upcoming material needs.





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

| Description                             | Type           | Inputs                                                                                                                                                                                                  | Outputs                                                                                                                                                                                        | Details                                                                                                                                                         |
|-----------------------------------------|----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Confirm login page authentication       | Functional     | Input "nametest" into the "username" field, enter the password "test1", and press "Login".                                                                                                              | The system should authenticate the user and bring them to the Build Page Dashboard if the credentials are correct                                                                              | This test ensures the login mechanism is correctly authenticating users based on the credentials provided and grants access to the Homescreen.                  |
| Confirm Addition of Projects            | Functional     | Enter project name- Include expected money for project- Click Create                                                                                                                                    | The new project should be created and added to the database and the expected expense.                                                                                                          | This test is designed to confirm the creation of the project within the system.                                                                                 |
| Adding Build Session                    | Functional     | The user clicks add build sesh and is directed to pick which project they worked on. The user uploads a photo and can write a description of the session. It also allows user to enter items and cost.  | The build session is saved to the Database as well a all photos, descriptions, and items. The project page now previews a link to past build sessions and the ability to use RUD transactions. | This test ensures that the user can log all build sessions.                                                                                                     |
| Evaluate code quality                   | Non-functional | N/A                                                                                                                                                                                                     | The code should be well-commented, with clear and descriptive variable and method names, facilitating easy understanding and maintenance.                                                      | This test assesses the maintainability and readability of the code, which includes checking for coding standards, proper documentation, and naming conventions. |
| Check integrity of Users database table | Non-functional | Perform a series of data entry operations on the application. Such as creation of New Project, Photos, comments, and ETC.                                                                               | The Users database table should accurately reflect all the data entered through the application without any loss                                                                               | This test checks the database operations and that all data is correctly put into the table.                                                                     |





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


