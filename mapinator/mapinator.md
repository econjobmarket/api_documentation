# Mapinator Project

In the first pandemic summer in 2020, the first version of the mapinator was written by Amedeus D'Souza.  The current version is located at [https://sage.microeconomics.ca](https://sage.microeconomics.ca).  It displays a network map that shows where various graduate schools in economics managed to place their graduate students.  The data is not complete, but it uses data from 2008 to the present.  At the time of writing there are over 14 thousand observations in the data set.

The database was initially created by Kim Nguyen, who now works at the Reserve Bank of Australia.  In summer 2020, Amedeus, along with his colleague Felipe Grosso organized what they called a 'workathon' designed to enlarge the size of the database.  They convinced  handful of students in the honors program at the Vancouver School of Economics to volunteer their time to enlarge the database. Their wages were donated to a couple of charities, including The Sadie Foundation, Indspire, and Qmunity. 

Following the success of that project, a group of students. led by Jin Wang, Soren Rajani, Alex Dong and James Yu organized a second workathon in 2021.  This time volunteers participated from a number of different departments at UBC.

# Practical Appeal

One thing that makes the workathon attractive to students is that all the data that is collected is made available in a public database (mostly through the mapinator).  The database is a nice resource for economics students who are planning to go on to higher graduate studies in economics.  The mapinator will basically show them where they are likely to get a job when they graduate from different schools.  So the volunteers for the mapinator project know they are contributing to a public good.

# The Data

The database consists of outcome information that is manually collected on the internet.  University placement lists are used if they are available.  Manual search is used with names from [https://econjobmarket.org](https://econjobmarket.org), though the database itself does not provide any names. Unless there is a publicly available record on the internet that indicates a placement, applicants' names do not appear in the database at all.

So far there is no data for applicants who do not register at econjobmarket.  Offhand comments by researchers who have worked with econjobmarket data suggest that somewhere between a half and three quarters of all Ph.D. graduates from American universities actually register on econjobmarket.

Applicants are more likely to register when they can also submit applications on econjobmarket.

The list of organizations who hire graduates comes from econjobmarket.

The only metadata that is used is the applicants year of graduation, the name of the institution and organization that they graduated from, and their primary field.


Each node in the graph is an organization, its location on the map and its rank according to Tilburg.  At this point the organizations rank on RePEc should also be attached.  Each edge corresponds to an applicant.

# Categories

One research project that is based on this data attempts to assign categories or types to organizations based on their placements.  The project is described in more detail at [this document](sbm_project_description.md). 

The types are identified using a simple directed search model that predicts placement patterns for each category of organization to each other category of organization.  The basic theory assumes that different organizations can graduate students who have the same value to all market participants. Organizations whose students have the same value will exhibit similar placement patterns.

Current estimates of the type assignment suggest there are four basic types of organizations.  First category organizations are research departments that graduate students who place predominantly in other category 1 and category 2 research organizations, though all organizations who produce graduates will place them in all the different categories.

Second category organizations also place graduates primarily with other second category organizations.  They are more likely (relative to demand) to place graduates at category three organizations than category 1 organizations are.

Category three organzations place graduates primarily with other category three organizations and with teaching institutions.

Category four organizations generally have few graduates and place most of them in teaching institutions.

Categories are generated from the data itself. The number of categories is determined using maximum liklihood along with penalty term whenever an additional category is added.  Likelihoods for a given number of categories are computed by stochastically moving organizations between categories.

# Other

If you find errors in the data please submit an issue report to [https://github.com/michaelpetersubc/mapinator](https://github.com/michaelpetersubc/mapinator).  If you'd like to work further with the data or participate in the project, submit a support request to [Econjobmarket.org](https://econjobmarket.org/users/feedback/threads/s).
