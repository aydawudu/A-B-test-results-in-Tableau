# A/B test results inTableau: Analyzing Wikipedia’s new search functionality
This is adapted case study to illustrate the use of tableau in A/B Testing

# Case Study Background
The case was inspired by Wikimedia Foundation Data Analyst Technical Assignment [https://github.com/wikimedia-research/Discovery-Hiring-Analyst-2016]. The original dataset was transformed and adapted for the purposes of the workshop.

Today you will become part of Discovery department at Wikimedia Foundation for a day. Your team just made a big change to the Wikipedia Search experience and ran an A/B test to determine whether the new version of the search is better than the old one. It is your task to analyze the data and prepare a brief explaining the results of the test.

Discovery team relies on event logging (EL) to track a variety of performance and usage metrics to help the team make decisions. Specifically, Discovery is interested in:

clickthrough rate: the proportion of search sessions where the user clicked on one of the results displayed
zero results rate: the proportion of searches that yielded 0 results
and other metrics outside the scope of this task. Event Logging uses JavaScript to asynchronously send messages (events) to Discovery servers when the user has performed specific actions.

Data
The dataset comes from a tracking schema that Discovery uses for assessing user satisfaction. Desktop users are randomly sampled to be anonymously tracked by this schema which uses a "I'm alive" pinging system to estimate how long users stay on the pages they visit. The dataset contains just a little more than a week of EL data.

Column	Value	Description
uuid	string	Universally unique identifier (UUID) for backend event handling.
timestamp	integer	The date and time (UTC) of the event.
session_id	string	A unique ID identifying individual sessions.
group	string	A label ("a" or "b").
action	string	Identifies which action triggered the event. See below.
checkin	integer	How many seconds the page has been open for.
page_id	string	A unique identifier for correlating page visits and check-ins.
n_results	integer	Number of hits returned to the user. Only shown for searchResultPage events.
result_position	integer	The position of the link to the visited page on the search engine results page (SERP).
The following are possible values for the action field of an event:

searchResultPage: when a new search is performed and the user is shown a search results page.
visitPage: when the user clicks a link in the results.
checkin: when the user has remained on the page for a pre-specified amount of time.
