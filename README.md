

# Criteria A: Planning

## Problem definition

An competent engineer constructing a house in Japan, seeks a solution to organize his construction progress tracking. Currently he manually documents each build session in a spreadsheet with photos and descriptions, leading to disorganization and difficulty in accessing specific information. Orginally the client has been taking a photo then writing a brief description. However over time the client has just taken photos without writing descriptions planning to go back in the future and write a decription. This also makes it very difficult to find photo/reciepts for differant parts of the house. This has led to a overwellming number of photos without decriptions creating an unorganised system. Reciepts have also been piling up making it hard to track the total expenses for each project within the house. Addd in appendix about meeting.



** Maybe :He also wants to spread his knowledge of building house with thw wourld. Comment System

## Design statement:
I will design a website for a client who is trying to track construction of his house. The website is constructed using the software pyhton/flask. It will be evaluated according to the criteria (please check succes critera below).

## Rationale for Proposed Solution

To address this, he desires a system that automates photo uploads, prompts for descriptions, and extracts metadata for date and time tracking. Additionally, the website should offer project management tools, including categorization by house sections and project types. It should enable easy tagging and tracking of expenses, along with robust search and filter functions for quick access to updates and material information. Lastly, the client seeks a dashboard displaying construction progress visually, highlighting completed tasks, ongoing projects, and material needs.

I chose Python because it’s one of the most user-friendly programming languages that is quickly growing globally. [1] According to Linked In, python is easy to understand because of its simple English syntax that allows the programmer to create programs easily.[2] Python also has access to numerous libraries that allow developers to program more efficiently. These libraries provide an API (application programming interface) which makes it easy for developers to use them with their own software programs.[3] Furthermore, Pythons is versatile language that can be used for web development, software development, scientific computing, data analysis, artificial intelligence, and more.[4] Thats why I believe Python will be able to solve all of my client's problems and let her have a functioning crypto wallet.

I chose to use flask because it is a micro web framework that is written in Python. Specfically, flask offers more flexibility and freedom to developers, allowing them to choose and integrate specific libraries and components as needed[^9]. Flask's design also supports the creation of test cases, ensuring that the application remains robust and error-free as it evolves.



## Success Criteria
1. A The website allows user to upload photos.
1. B The website allows user to add descriptions to the photos after each build session. Prompting user if Picture doen't have comment.
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

End User Testing

## Sources Cited
1. What is python used for? A beginner’s guide. Coursera. (n.d.). https://www.coursera.org/articles/what-is-python-used-for-a-beginners-guide-to-using-python 
2. Ahmed, M. (n.d.). Why is python so easy to learn?. LinkedIn. https://www.linkedin.com/pulse/why-python-so-easy-learn-maqsood-ahmed 
3. GoPract.com. (n.d.). The importance of libraries in Python, Data Science, and the applications they facilitate. GoPract. https://gopract.com/Pages/Importance-of-Libraries-Python-data-science-Applications-They-Facilitate.aspx#:~:text=Python%20libraries%20are%20pre%2Dwritten,data%20analysis%20and%20machine%20learning. 
4. Worsley, S. (2022, March 7). What is python? - the most versatile programming language. DataCamp. https://www.datacamp.com/blog/all-about-python-the-most-versatile-programming-language 
5. Tele, C. (n.d.). What is ethereum and how does it work?. Cointelegraph. https://cointelegraph.com/learn/what-is-ethereum-a-beginners-guide-to-eth-cryptocurrency 
6. Hayes, A. (n.d.). Blockchain facts: What is it, how it works, and how it can be used. Investopedia. https://www.investopedia.com/terms/b/blockchain.asp 
7. Golubev, S. (n.d.). The expansion of Decentralized Finance (DEFI) on the Ethereum Network. LinkedIn. https://www.linkedin.com/pulse/expansion-decentralized-finance-defi-ethereum-network-sergey-golubev 
8. CoinMarketCAP. (n.d.). Ethereum Price Today, ETH to USD live price, marketcap and Chart. CoinMarketCap. https://coinmarketcap.com/currencies/ethereum/ 


