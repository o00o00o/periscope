---
layout: project
title:  "Hack the North"
date:   2016-09-16 12:34:56
author: Steven Luo
categories:
- project
img: /hackthenorth/hackthenorthedit.png
carousel:
- /hackthenorth/opendata.gif
tagged: SQL, Bash, C++, Open Data
website: https://github.com/o00o00o/hackthenorth2016
---
**From [Devpost](http://devpost.com/software/hackthenorth2016) Submissions**

**Issue:** Nonprofits needs an easy access to reliable data. This data would be use to target select demographics, provide much needed services, and optimize resource allocation.

**The BIG idea:** This project is a proof of concept for increasing hands-on tech opportunities for students and increasing the impact that a nonprofit's can make. Summer interns with the support of Canadian Government’s Summer Student grant will work with Nonprofits on Open Data. With even no prior SQL experience such as myself, students can successfully parse the raw data into a Query-able database. From here the nonprofit can use the data to model predictions and to create targeting strategies. While the student intern receives valuable job experience that is not making coffee. Currently some nonprofits are paying for data but that money can be much better used once fed back into the community. Not only are we enabling students we are exponentially increasing the impact that a nonprofit can make.

**Solve:** Non-profits needs data and the government of Canada provides data from Statistics Canada and other federal departments that is open for the public to use. The only issue is that these data are extremely overwhelming, unorganized, and raw. Having interns or an open-source community where we can make these data usable for the general public will only benefit our community. Read this great article here [http://opendatahandbook.org/guide/en/why-open-data/](http://opendatahandbook.org/guide/en/why-open-data/) on how open data can make a difference.

**Learn:** This is the first time I have worked with SQL databases. I was able to to create an encompassing project where I installed/created a database (ubuntu), inserted data, and created an interface to access the database. The hardest part of the project is working with the volume of data.The raw data is not always consistent as some names or figures includes characters such as commas and the use of quotations. I needed to use tricks such as replace all and wildcard matching to be able to manipulate and then insert into the database.

This project uses this data set [http://open.canada.ca/data/en/dataset/93d89f25-2770-4030-814f-771fea2af2a4](http://open.canada.ca/data/en/dataset/93d89f25-2770-4030-814f-771fea2af2a4) "Neighbourhood income and demographics, taxfilers and dependents, by sex, marital status and age group" which includes 203,902 data points. This data was parsed into a sqlite database separating each category to be easily queried. Then a fast C++ interface was implemented to allow anyone such as the marketing manager to find relevant information.

**Goal:** of this project was to have a system where nonprofits can target select regions based on a variety of indicators. Such as income median, age median, age/sex breakdown. Due to a lack of time only a subset of these features were implemented.
