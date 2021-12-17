# ph-sona
A database of Philippine presidents' State of the Nation Addresses, 1936-2020


# In broad strokes, what is this about?

Just as the subhead says this contains all State of the Nation Addresses of former and current presidents of the Philippines.
The database covers speeches from the administration of Manuel Quezon to Rodrigo Duterte, with the exception of Jose Laurel, which the source did not have.


# What is SONA?

It's basically the counterpart of the US president's State of the Union Address. Under the Philippine Constitution, the president is mandated to deliver 
the SONA every fourth Monday of July to open a new session of Congress. The speech is closely watched by the media for policy directions and agenda.


# What is the source of the data?

-Information in the database were scraped from https://www.officialgazette.gov.ph/past-sona-speeches/, which is hosted by the official portal of the
Philippine national government. The website is maintained and updated regularly. Information was scraped using BeautifulSoup and Selenium and coded
using Jupyter Notebook/Python.


# The process

-Scraping was pretty straightforward, but involved two processes to generate two data frames. First, we used Selenium to get to the main page
and loop through the table containing, among others, links to actual speeches.

-We generate a data frame out of the information on the table: which includes the president's name, the date, title of the speech
the venue where the speech was delivered, link to the speech, and the session of Congress that it opened.

-We looped through the information and then transformed them into lists of dictionaries and then a df. 

-The next step involved generating another df for actual speeches. This involved going through all the links and copying their contents into a list
of dictionaries. 

-We used BeautifulSoup for this by making requests to the links we isolated on the first list and getting the contents. To make the new list of dictionary
more organized, we included the "link" to each speech as a key.

-Line breaks were intentionally not removed from this segment to ensure 

**This is a final project in partial fulfillment of requirements at Columbia Journalism School.
All rights reserved.
