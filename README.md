# A/B test results inTableau: Analyzing Wikipedia’s new search functionality
This is adapted case study by Data Science Go workshop to illustrate the use of tableau in A/B Testing

# Case Study Background
The case was inspired by [Wikimedia Foundation Data Analyst Technical Assignment](https://github.com/wikimedia-research/Discovery-Hiring-Analyst-2016). The original dataset was transformed and adapted for the purposes of the workshop.

Today you will become part of Discovery department at Wikimedia Foundation for a day. Your team just made a big change to the [Wikipedia Search](https://www.wikipedia.org/) experience and ran an A/B test to determine whether the new version of the search is better than the old one. It is your task to analyze the data and prepare a brief explaining the results of the test.

Discovery team relies on event logging (EL) to track a variety of performance and usage metrics to help the team make decisions. Specifically, Discovery is interested in:

  * *clickthrough rate*: the proportion of search sessions where the user clicked on one of the results displayed\
  * *zero results rate*: the proportion of searches that yielded 0 results \
\
and other metrics outside the scope of this task. Event Logging uses JavaScript to asynchronously send messages (events) to Discovery servers when the user has performed specific actions.

# Data
The dataset comes from a [tracking schema](https://meta.wikimedia.org/wiki/Schema:TestSearchSatisfaction2) that Discovery uses for assessing user satisfaction. Desktop users are randomly sampled to be anonymously tracked by this schema which uses a "I'm alive" pinging system to estimate how long users stay on the pages they visit. The dataset contains just a little more than a week of EL data.

**Column**|**Value**|**Description**
-----|-----|-----
uuid|string|Universally unique identifier (UUID) for backend event handling.
timestamp|integer|The date and time (UTC) of the event.
session\_id|string|A unique ID identifying individual sessions.
group|string|A label ("a" or "b").
action|string|Identifies which action triggered the event. See below.
checkin|integer|How many seconds the page has been open for.
page_id|string|A unique identifier for correlating page visits and check-ins.
n_results|integer|Number of hits returned to the user. Only shown for searchResultPage events.
result\_position|integer|The position of the link to the visited page on the search engine results page (SERP).

The following are possible values for the action field of an event:

* searchResultPage: when a new search is performed and the user is shown a search results page.\
* visitPage: when the user clicks a link in the results.\
* checkin: when the user has remained on the page for a pre-specified amount of time.

#Example Session
**uuid**|**timestamp**|**session\_id**|**group**|**action**|**checkin**|**page\_id**|**n\_results**|**result\_position**
-----|-----|-----|-----|-----|-----|-----|-----|-----
4f699f344515554a9371fe4ecb5b9ebc|20160305195246|001e61b5477f5efc|b|searchResultPage|NA|1b341d0ab80eb77e|7|NA
759d1dc9966353c2a36846a61125f286|20160305195302|001e61b5477f5efc|b|visitPage|NA|5a6a1f75124cbf03|NA|1
77efd5a00a5053c4a713fbe5a48dbac4|20160305195312|001e61b5477f5efc|b|checkin|10|5a6a1f75124cbf03|NA|1
42420284ad895ec4bcb1f000b949dd5e|20160305195322|001e61b5477f5efc|b|checkin|20|5a6a1f75124cbf03|NA|1
8ffd82c27a355a56882b5860993bd308|20160305195332|001e61b5477f5efc|b|checkin|30|5a6a1f75124cbf03|NA|1
2988d11968b25b29add3a851bec2fe02|20160305195342|001e61b5477f5efc|b|checkin|40|5a6a1f75124cbf03|NA|1

This user's search query returned 7 results, they clicked on the first result, and stayed on the page between 40 and 50 seconds. (The next check-in would have happened at 50s.)

# Tableau Results
You can check out the tableau analysis [here](https://public.tableau.com/views/ABTestingAnalyzingWikipediasNewSearchFuntionality/Story1?:language=en&:display_count=y&:origin=viz_share_link).


