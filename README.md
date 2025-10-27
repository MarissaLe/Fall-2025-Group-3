# Fall-2025-4610-Group-3
MIST 4610: Dr. Srinivasan -
Streaming Platform mySQL Project

# Team Name
62775 Group 3

# Team Members
1. Matthew Wise @mwise12345
2. Ghasan Awad @awadg420
3. Trisha Kattoju @tkattoju
4. Marrissa Le @MarissaLe
5. Isaac Lee

## Project Scenario
This project focuses on developing a relational database that represents the operations of a digital streaming platform. The system is designed to manage subscriber accounts, user profiles, payments, available content, and more. Each subscriber can maintain multiple profiles under one account, allowing for personalized viewing and recommendation features. The database also tracks interactions between users and media, such as watch history, favorites, and content reviews. In addition to user activity, the model incorporates employee and department data to handle administrative tasks, customer support, and service maintenance through ticket tracking. Entities are structured with both straightforward and recursive relationships to accurately reflect real-world dependencies within the platform. By generating realistic sample data and performing analytical queries, this model enables a deeper understanding of user behavior, financial performance, and overall system efficiency within the streaming service.

Our task is to develop a relationship database to represent the operations of a digital streaming service. The data model will represent operations involving the user and operational side of the company. Information will need to be stored about departments, employees, and on the user side, watch history, favorites, and more. Data related to the content on the streaming platform will be stored as well such as content type and genres. We are to populate the databases and model the relationships to enable the digital streaming service to seamlessly operate its data and scale.

## Data Model
Our model is centered on the Account Owner, the entity that represents the primary user who holds the account. The model holds information regarding the owner’s name, email, and password. This Account Owner entity serves as the root for three main branches: Payments, Tickets, and Profiles. The account owner can have many payments. Payment info stored includes credit card number, card type, and transaction dates. The second branch leads to the Profile table. An account owner can create multiple profiles for their account. Profile data includes the profile name.

There are two key branches that come from the Profile table. First, the Watch History table logs every video a profile plays and the date watched. Since one profile can watch many videos over time, this is a one-to-many relationship.

The Favorites table is the second entity that is connected with the profile table. A profile can add many content items to their personal "Favorites" and a single content item like a popular movie can be favorited by many different profiles. Because of this many-to-many relationship, the Favorites table serves as an associative entity that links the Profile and Content tables.
The Content entity represents our entire media catalog of movies and series. It stores descriptive data like the title, release year, duration, language, and content type of a show or movie. To organize this large catalog, we have a Genre table, which defines all possible genres. A single movie can be in multiple genres (like action and science-fiction), and a single genre may apply to many movies. To model this many-to-many relationship, we created the Content Genre associative table, which links the content id to the genre id. The Genre table branches out to a join table called Genre_has_Genre with a many to many recursive relationship, allowing a genre like 'Psychological Thriller' to be linked to its parent, 'Thriller'. A subgenre can have many genres and a subgenre can have many genres.

Finally, our model involves the internal operations of the company. The Department entity represents our internal departments such as billing and customer support. Inside a department, there are many employees. Employee data stored includes name, email, job title, and their hire date. Each employee also has a supervisor, and a supervisor can oversee many employees, indicating a one-to-many recursive relationship.
When a customer has a problem, they need to contact an employee. An account owner can have many support tickets, and an Employee (like a support agent) can work on many tickets. This many-to-many relationship is handled by the Ticket associative table, which links the account owner who has a problem to the Employee assigned to help them. A ticket has a request date and a resolve date

<img width="1249" height="760" alt="DMProject1" src="https://github.com/user-attachments/assets/abcd8903-31f3-4fab-91c8-b7862b45dd61" />


## Data Dictionary 
<img width="417" height="547" alt="image" src="https://github.com/user-attachments/assets/235ed120-012c-4d7c-b1ce-860da386dcdb" />

<img width="417" height="360" alt="image" src="https://github.com/user-attachments/assets/e6f78b21-27a3-4407-9341-58aa94dab2c8" />

<img width="417" height="360" alt="image" src="https://github.com/user-attachments/assets/35a65f82-8922-462a-84bb-5ce8e8b805a4" />

<img width="417" height="526" alt="image" src="https://github.com/user-attachments/assets/957428a5-08b6-4df1-a70f-7d025a16c6f9" />

<img width="417" height="470" alt="image" src="https://github.com/user-attachments/assets/c89841aa-7ca4-4dfa-8d55-55bc1f781a93" />

<img width="417" height="514" alt="image" src="https://github.com/user-attachments/assets/a21330b2-e007-4c12-a7e1-aab5662b08f2" />


## Queries

<img width="1168" height="536" alt="image" src="https://github.com/user-attachments/assets/5278b14f-2352-4789-ba89-d59610de4786" />


1. List favorite movie titles for each profile, when it was added, and only for favorites added in 2024

<img width="800" height="242" alt="image" src="https://github.com/user-attachments/assets/944d4788-327c-4254-9eec-b5e8732db597" />


Query 1 allows managers to analyze recent trends in user engagement by seeing which movies were liked by viewers, specifically in 2024. This helps them identify popular content and aim their marketing campaigns towards these highly rated titles. By seeing which movies are favorited and which ones aren’t, the streaming service can more easily decide what type of content to promote more heavily.



2. List each employee and their supervisor, but only for supervisors in the customer support department

<img width="800" height="172" alt="image" src="https://github.com/user-attachments/assets/f7c22cc3-b2dd-4ba7-b462-7388c17f64b9" />

Query 2 allows management to better understand the reporting structure within specific departments in the company, such as the customer support team used in the query above. This is extremely useful for monitoring an employee’s workloads, as well as ensuring proper supervision from the company’s supervisors. Also, tracking each employee and who they report to can allow the company to plan training and conduct performance reviews within a chosen department.




3. List the number of tickets each employee has handled for the customer support department

<img width="800" height="168" alt="image" src="https://github.com/user-attachments/assets/2d226149-f1c7-40a4-a025-cc3948c17493" />


Query 3 is useful for our streaming service company because it represents employee productivity and their efficiency too. When managers can record and track the number of support tickets each employee resolves, they can better identify top performers who handle user disputes better than employees who may have issues with resolving conflicts in customer service. Higher performers in the department can receive bonuses, incentives, and recognition that boosts their morale and encourage the team to use their practices. For employees with poor records, managers can focus their training efforts on them and give feedback that can allow them to improve their performance. Finally, managers can point out potential issues with workload conflicts and ensure each employee has a sufficient amount of work that doesn’t slow them down nor leaves too much free time for customer support workers.












4. List out the profiles that have no favorites, and the associated account owner email

<img width="800" height="212" alt="image" src="https://github.com/user-attachments/assets/72ef1985-efde-46c3-a728-7e895c7ddba9" />


For profiles that don’t have favorite movies or shows in their watch history, we can most likely assume these users are disengaged or don’t understand how to use our features like favoriting that gives a personalized touch to our service. Managers can promote re-engagement campaigns to these profiles specifically. These promotion efforts may include content recommendation that is similar to their previous viewings, free trial offers for premium features like ad-free watching experience. These efforts make sure the personalized features our service provides are being used efficiently rather than offering basic services that our competitors most likely use.


5. List out the different credit card types used by customers and how many of each are used


<img width="800" height="166" alt="image" src="https://github.com/user-attachments/assets/f38bb3c8-270d-4823-9e25-08abcfd474b9" />


Query 5 provides valuable data for payment methods that helps managers better understand customer payment preferences, specifically which credit cards are most used among our customers. This is useful for financial forecasting and allows our company to negotiate partnerships with card companies. These partnerships would open our service to multiple perks like subscription bonuses and cash back options for Visa users or MasterCard users for example. This mutual relationship between card companies and our streaming service can put our name out in the market and help us stand out among competitors and attract more potential customers to use our services. Additionally, seeing which payment methods are being underused such as gift card or debit options can help our teams improve these lesser-used payment options.






6. List out the number of titles per genre, and order in ascending alphabetical order

<img width="800" height="199" alt="image" src="https://github.com/user-attachments/assets/2262363c-e74a-4639-ac48-0c46542b15e2" />



Query 6 helps managers assess content library balance. This data shows whether our service has enough variety or is under/overrepresenting select genres. By seeing the proportion of genres we offer, we can use this insight for strategic planning, licensing, and improving the content mix to attract diverse audiences rather than offer a small number of genres, regardless of the amount of content our company acquires.


7. List out the profiles that have more watch history than the average account

<img width="800" height="238" alt="image" src="https://github.com/user-attachments/assets/b335e786-adf1-4d17-8b84-7ac6e9bd0c5b" />



This query identifies users who are more engaged than other users based on the amount of titles shown in each person’s watch history. Users who historically watch more movies and shows can be identified by managers as “power users” since they most likely spend more time using our service than others. These power users hold a very important position in our customer retention because of their repeated usage of the streaming service. We can create loyalty programs that are fitted to these viewers, as well as offer feedback surveys that can be used to encourage more activity from less-engaged viewers. Another use of this query is beta testing new features on this group, since they represent the most invested and active portion of our customers.




8. List the percent of account owners that have filed a ticket

<img width="800" height="145" alt="image" src="https://github.com/user-attachments/assets/3ac498bd-58b1-4ab9-8add-fcbe5e3c7e72" />


Query 8 gives managers a measure of customer support demand by seeing what percentage of users have experienced issues that required customer support. It’s important to track the amount of customers filing support tickets because a large amount can indicate repeating technical issues, confusion on certain features, or simply dissatisfaction. Managers can use this data to address common user issues, track efficiency of product improvements, and other methods that improve customer service support and user experience overall.



9. List the number of tickets that have been handled in 2025

<img width="800" height="146" alt="image" src="https://github.com/user-attachments/assets/63b307a8-1ed5-4316-824b-e640da898ec0" />


This query lets managers track overall performance and workload for the customer service team, specifically in 2025. The data shows how many tickets were actually resolved versus those that weren’t able to be completed for whatever reason. This can be used to measure productivity in the support department, helping managers determine if staffing levels were sufficient in a specific year compared to others. This time-based data analysis is important to assess growth in the user base’s relationship with support demand. Finally, this query gives management a quantitative view of customer service’s performance, helping them plan staffing and budget improvements in the future.



10. List the customers’ emails who are not paying

<img width="800" height="168" alt="image" src="https://github.com/user-attachments/assets/1aa4af79-6d1a-4116-8b4b-8a196eeec7a7" />




This query points out customers who have no records of payment history, whether it’s because they are inactive or possibly showing delinquent behavior. This information and distinction is crucial for our company to maintain financial health and improve customer retention. Some steps that we can take with this data involve a billing follow-up to resolve payment issues before accounts are suspended. Also, the marketing department can use this data to target these users with special discounts or limited-time trials to encourage subscription renewals. Another possible reason for lack of payment is fraud, which is important for us to track to maintain company standards and ensure a fair experience for all our customers.


## Database Information

Name of the database: ns_Group3

Additional information: Each query listed above is marked in the database using stored procedures which can be called using the following format: CALL TP_Q1();
