# Project guidelines

**NOTE**: This document is under construction

Key dates:

- Dec 4 (Tue): Final presentation for JOUR7280
- Dec 7 (Fri): Final presentation for COMM7780
- Dec 16 (Sun): Final submission (report/ dataset/ codes/ aux files) due for JOUR7280/ COMM7780, i.e. finalise your GitHub repo by this date

## Final Presentation Guideline

Every group has up to 20 min including Q/A time. It is suggested to control your presentation time to ~12 min, up to 15 min. 15 min will be a hard cut. We will stop you immediately at 15 min no matter how many slides are left. The presentation is rated by the lecturer, as well as invited guests from the industry. The formula of a good presentation:

- It usually catches people's attention very quickly and then goes through the main story points without messing the audience with too many technical details.
- People then raise various questions, related with the presentation but may well beyond the presentation itself. Since you have studied the topic in depth via the final project, you have the best expertise to answer those questions. You can prepare some "backup slides", so when people ask, you can jump there.

The rule of thumb: when people challenge you, they are actually interested to know more. The more attention they devote to your project, the deeper impression they will have about your project. Don't feel bad when people ask questions. Try to make them excited by your inspiring and insightful answers.

## Final Submission Guideline

Technical requirements:

- Create **a repository dedicated for the project** and keep updating. You can choose to put the repo under an individual user, or more preferrably you create [an organisation](https://help.github.com/articles/differences-between-user-and-organization-accounts/) for your final project. We advocate to use GitHub as a **collaboration platform**, instead of merely a place to publish your works. [GitHub Desktop](notes-weeek-00.md#github-desktop) is very convenient for you to synchronize files between the group members, or between your multiple devices.
- Include at least one Jupyter notebook (`.ipynb`) in the repo, showing how you reach all the story points and conclusions. That is, the notebook needs to be **reproducible**. When there is gap, e.g. timing of execution/ login credentials, please leave enough notes, so that others are able to execute your script with the help of your notes.
  - You are welcome to leave more Jupyter notebooks in the repo when applicable. Usually, we organise our data pipeline into several stages and use one notebook for one stage. There are usually three stages: 1) data collection; 2) data analysis & visualisation; 3) data presentation. In this way, when people try to reproduce the analysis part, they don't have to spend time re-executing the data collection script. When people first come to your project, they can start with the presentation notebook, which load intermediate data files produced by upstreams. If they find one part interesting, they may dig out the processing details from upstream.
- Put all data files, photos, videos, documents and slides related with your final project into the repo. If the files are too large (> 100MB), find us to discuss case by case.
- Put a `README.md` at the root of the repo, which includes the following information:
  - Title
  - Team members
  - Background and motivation
  - (optional) Executive summary
  - Quick pointers to key files
  - References

Data requirements:

- **Original data**: The project needs to have at least one original dataset, in the form of *raw dataset*, not summarised statistics. The volume of this dataset is no less than that of Assignment 1.
- You can use existing public datasets to assist your data-driven report. That may come in the form of downloadable data files; or available via API. Please cite the source properly.

You can refer to [archive of past projects](https://github.com/data-projects-archive/) to get some ideas. Note that, not all the projects there conform to our current standard. The requirements are evolving, so please observe the above closely. Feel free to ask whenever in doubt.

## Content guideline: JOUR7280 -- Data Journalism

The final output is a **complete story** powered by data. Depending on the group expertise, you can emphasise more on data, or more on story. Besides using data, you can leverage conventional techniques from journalism production, e.g. interview, photo, video. We adopt the broad sense of "newsworthiness" -- new knowledge on old topic also counts. Of course, if the project can tackle a question with social impact, that is better. The best one starts from a current affair, scrape/ find relevant dataset, and mine the data to get new insights not yet told/ not well told in the public. Introducing diversfied perspectives are always highly appreciated. Constructive discussions, either from the group or from interviewee, are also highly appreciated. Two past references suitable for JOUR7280 are [AirCrash](https://dnnsociety.org/2018/04/30/flying-in-the-sky-a-report-of-air-crash-worldwide/) (more data) and [Syria War](https://dnnsociety.org/2018/05/10/syrias-toxic-war-on-itself/) (more story).

## Content guideline: COMM7780 -- Data-driven report on communication issues

Being data-driven should be easy for most students who have taken the course. Finding questions concerned in communication field and use data-driven insights to answer them could be hard. Following are potential ideas and treatment related with communication, for your reference:

- Study brands' outlook on rating sites. Ref. [Fastfood on Dianping](https://nbviewer.jupyter.org/github/data-projects-archive/201804-Fast-Food-on-Dianping/blob/master/final_project/final%20project.ipynb).
- Analyse current trend in Internet product, and devise content strategies.
- Auto media monitoring, e.g. keywords alert on Twitter/ Weibo; sentiment analysis.
- Study career prospect for communication students. Ref. [HKBU MA career study](https://nbviewer.jupyter.org/github/data-projects-archive/201804-HKBU-MA-Career-Perspective/blob/master/Final%20Project%20from%20Pili%20Fans%20Club/final%E2%80%94%E2%80%94notebook.ipynb)
- User profiling for a website/ product/ service. 
- Content profileing for a website/ product/ service. Ref. [Recipe on Xiachufang](https://nbviewer.jupyter.org/github/data-projects-archive/201804-Xia-Chu-Fang/blob/master/final%20assignment/Big%20Data%20Project%20-%20Xiachufang_revised.ipynb)
- Build a chat bot to conduct Customer Relationship Management (CRM). Ref. [Twitter earthquake bot](https://github.com/hupili/python-for-data-and-media-communication-gitbook/blob/master/notes-week-04.md#bonus-automatic-earthquake-writer) 
- Analyse network structure to get insights of community operation. Ref. [wechat ego-net](https://mp.weixin.qq.com/s/DgAXmcR2kn3q2xjsEiwpJg)
- Build a categorized journalist's catalogue for PR specialist. Ref. [global data journalist directory](http://jplusplus.github.io/global-directory/), pointers from [this post](https://gijn.org/2016/05/23/resources-guides-to-finding-expert-sources/)
- Conduct SEO auditing. Ref. [SEO auditing exercise](https://github.com/hupili/python-for-data-and-media-communication-gitbook/blob/master/notes-week-06.md#in-bound-marketing-and-seo-auditing)
- Market analysis that supports a startup idea.

We will keep the list growing when more ideas and references are available. You are suggested to discuss with the instructor as early as possible, to help evaluate the relevance and viability. The final deliverable could be a report like industrial research report, e.g. [Reuters X Oxford digital media report](https://reutersinstitute.politics.ox.ac.uk/sites/default/files/digital-news-report-2018.pdf). However, you are not limited to this form. A product document, planning document, or pitch deck/ business proopsal are all valid. You can even build a web based data query service if you'd like to. Note that, one important factor is **communication perspective**. A report that purely enumerates data/ statistics/ charts and describes only what they are, will not meet the requirement. You need to extract communication insights or make derivative works that is relevant to a communication issue.
