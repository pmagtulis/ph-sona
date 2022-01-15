# ph-sona
A database of Philippine presidents' State of the Nation Addresses, 1936-2020


# What is this about?

Just as the subhead says this contains all State of the Nation Addresses of former and current presidents of the Philippines.
The database covers speeches from the administration of Manuel Quezon to Rodrigo Duterte, with the exception of Jose Laurel, which the data source did not have.


# What is SONA?

It's the counterpart of the US president's State of the Union Address. Under the Philippine Constitution, the president is mandated to deliver 
the SONA every fourth Monday of July to open a new session of Congress. The speech is closely watched by the media for policy directions and agenda.


# What is the source of the data?

Information in the database were scraped from [here](https://www.officialgazette.gov.ph/past-sona-speeches/) which is the official portal of the
Philippine national government. The website is maintained and updated regularly. Information was scraped using BeautifulSoup and Selenium and coded
using Jupyter Notebook/Python.


# The process

1. Scraping was pretty straightforward, but involved two processes to generate two data frames. First, we used Selenium to get to the main page
and loop through the table containing, among others, links to actual speeches.

2. We generate a data frame out of the information on the table: which includes a separate columns for "administration" or president's name, the date, 
title of the speech, the venue where the speech was delivered, link to the speech, and the session of Congress that it opened.

3. We looped through the information and then transformed them into lists of dictionaries and then a df. 

4. We generate another df for actual speeches. This involved going through all the links and copying their contents into a list
of dictionaries. 

5. We used BeautifulSoup for this by making requests to the links we isolated on the first list and getting the contents. To make the new list of dictionary
more organized, we included the "link" to each speech as a key.

6. Line breaks were intentionally not removed from this segment to ensure that we do not unintentionally lose some words or phrases. It is worth noting that
the SONAs are unstructured texts and therefore differ in many characteristics such as length, use of sub-headers in some, inclusion of non-speech material 
(i.e. "Applause," which indicates clapping during actual speech), etc.

7. We generate a df with the entire speeches contained in rows. Essentially, the speeches were organized as big chunks in rows, for efficiency purposes. 
We recognize there may be a better way to do this and welcome suggestions. 

8. The two dfs (SONA tabled information and actual speeches) were then merged.

# What can we do with this?

One of the primary goals is to be able to conduct textual analysis from the database. This includes finding patterns through regex, filtering through pandas,
and running other statistical methods in measuring unstructured texts easier.

SONAs are good sources of government policy directions and may help text scholars in studies as well as journalists for research. 

# Definition of terms

1. **SONA** - State of the Nation Address
2. **Administration** - the administration when the speech was delivered. But essentially, the president who delivered it.
3. **Title** - a non-uniform ID per speech. Some speech have specific titles like "The Nation on the Road to Prosperity," while some didn't
and had the generic "State of the Nation" or "State of the Nation Address." Differences do not have material bearing.
4. **Date** - formatted "month, day year" that tells the exact date when the speech was delivered. Data type is an "object" but may be transposed 
into "datetime" as needed.
5. **Venue** - from 1926 to 1972, speeches were delivered at the "Legislative Building" in Manila where the bicameral congress was originally based. The building
had since been transformed into the National Museum. In succeeding years, SONAs were delivered instead in "Batasang Pambansa" in Quezon City. There were a couple of 
SONAs delivered elsewhere like Rizal Park.
6. **Session** - indicates the session of Congress when the speech was delivered. 



**This is a final project in partial fulfillment of requirements at Columbia Journalism School.**

**Comments and suggestions are always welcome! All rights reserved.**
