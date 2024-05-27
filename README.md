                                  Clash Royale ETL and Analytics 
![Databricks](https://a11ybadges.com/badge?logo=databricks)  ![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white) ![Apache Spark](https://img.shields.io/badge/Apache%20Spark-FDEE21?style=flat-square&logo=apachespark&logoColor=black) ![Power Bi](https://img.shields.io/badge/power_bi-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)



Let’s brief ourselves about Clash Royale mobile game,

Clash Royale is a real-time strategy game developed and published by Supercell. Released in March 2016, it combines elements of collectible card games, tower defense, and multiplayer online battle arenas.
In Clash Royale, players engage in head-to-head battles with opponents, aiming to destroy the enemy's towers while defending their own. The game features a variety of troops, spells, and defenses that players can collect and upgrade. These elements are represented as cards, which players deploy in battles using an elixir-based system.
The game's objective is to earn crowns by destroying opponent towers and winning battles to advance through different arenas and leagues.
Clash Royale has gained a large, active player base across the globe due to its competitive gameplay and strategic depth.


![image](https://github.com/Jay-05022000/Clash-Royale-ETL-and-Analytics/assets/110780565/b8483217-eb38-499e-a015-7a491bb704c7)



Motivation: 

I've been playing Clash Royale since 2021. In 2024, I decided to work on a data engineering project and aimed to find a decent and reliable data source for creating a data engineering and analytics project. After researching online, I discovered that many available data sources were too simple, and others had already been extensively used in existing projects. Additionally, some sources didn't interest me.
To create a personal project that would be both useful and engaging, I started analyzing the applications I have used over the years. This led me to the idea of working on a project centered around the Clash Royale mobile game. Having played the game for a long time, I'm familiar with its intricacies, and this knowledge will help me in my project. My goal is to build a platform that can efficiently analyze various data from the game, ultimately helping me improve my gameplay.


Data Source:

Clash Royale API: https://developer.clashroyale.com/

Note: For each request to this API from different IP addresses, users need to generate unique API keys.


Retrieved Data From the API:

1)	Clans Ranking : I have retrieved clan ranking data for various locations, including the United States, Brazil, Mexico, and Russia due to their high number of Clash Royale downloads, as well as India and Canada because of my presence in these countries, and Singapore because I am a member of a clan based there.
2)	Players Ranking for Path of Legends : The Path of Legends in Clash Royale is a competitive mode where players test their skills and advance through various ranks. I have retrieved player rankings for the locations mentioned in the Clans Ranking section.
I desire to use above mentioned data to analyze top N clans and players for desired location at a given time.
Below mentioned datasets are for personal use cases.
3)	Available Cards : I have gathered details about all available cards (troops) in the game, along with their relevant information to analyze cards based on different rarity and elixir levels.
4)	Clan Members Information : I have retrieved information related to my clan members. From this data, I have derived two additional datasets during the data transformation phase: 'Current Deck' and 'Clan Members Performance'.
      •	Current Deck : This dataset contains information about the deck currently used by clan members. A deck is a set of 8 cards (troops) that players use in battle. I plan to use this data to easily access deck information for my clan members.
      •	Clan Members Performance : This dataset contains statistical performance data about players' performance within the clan.
5)	Battle Logs : I have fetched battle logs for my game to monitor the history of my game outcomes.
6)	Upcoming Chests : Chests serve as rewards for players upon winning battles. These chests contain various cards, points, or gems. I'm fetching this data to stay informed about the upcoming chest types available for me.


Tools Used:

1)	Databricks Community Edition : It is utilized for developing extraction and transformation Python scripts.
2)	AWS s3 : It is employed to store raw data in JSON format and transformed (cleaned) data in CSV format within an S3 bucket.
3)	AWS Glue : AWS Glue is utilized to crawl transformed data within a specified folder of the S3 bucket and subsequently generate tables from it.
4)	AWS Athena : AWS Athena is used to execute SQL queries on tables created by AWS Glue.
5)	ODBC Connector : The ODBC Connector facilitates the connection between AWS Athena and Power BI, enabling the retrieval of available data from Athena into Power BI.
6)	Power BI : Power BI is employed to create an interactive visualization report using the cleaned data.


Workflow Diagram:


![Screenshot 2024-05-26 173341](https://github.com/Jay-05022000/Clash-Royale-ETL-and-Analytics/assets/110780565/3a6afaa4-9108-49fd-8daf-caa1fa9284f7)

 
Visualizations:

The Data Visualization report can be found here: 


https://github.com/Jay-05022000/Clash-Royale-ETL-and-Analytics/blob/main/Clash%20Royale%20Interactive%20Visualization%20Report.pbix


1) Clan Members’ Information Page

   
![image](https://github.com/Jay-05022000/Clash-Royale-ETL-and-Analytics/assets/110780565/97136a7d-81fc-4b37-8fd2-d3cef1da2a8b)
																			

2) Personal account information & tracking page

   
![image](https://github.com/Jay-05022000/Clash-Royale-ETL-and-Analytics/assets/110780565/d4b1cbdf-046d-4d92-8348-48c4230c74c9)
                                      

3) Available cards information page

   
![image](https://github.com/Jay-05022000/Clash-Royale-ETL-and-Analytics/assets/110780565/69c51887-96b7-4362-8162-77f46c9a7714)
                                    

4) Top clans and players ranking page

   
![image](https://github.com/Jay-05022000/Clash-Royale-ETL-and-Analytics/assets/110780565/fa729812-821d-4081-a707-96270fd35ce1)
                                      

Possible Extension of the project:


Currently the extraction and transformation scripts are triggered manually to get the clean data in s3 bucket from the API.AWS Glue crawlers can be scheduled easily to crawl clean data available in s3 at desired time and it is pretty easy to get the fresh data in Power BI once crawlers create glue tables.
The next version of this project could be to automate the extraction and transformation scripts to make them execute without human intervention.

This could be achieved in the following ways.

1)	Databricks Professional account: Databricks Professional account provides in-built feature to schedule or automate notebooks under its ‘Workflows’ option.
2)	AWS Glue ETL: AWS Glue ETL notebooks can also be used to develop scripts and these notebooks are easy to schedule with Workflows (Orchestration) feature of Glue.
3)	Apache Airflow: Apache Airflow can be used to orchestrate complete ETL pipeline and internally this approach requires Databricks professional account to create a connection between airflow and databricks to schedule databricks notebook.




