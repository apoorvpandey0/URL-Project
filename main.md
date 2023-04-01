**Personal Information**
=====================
- Name: Apoorv Pandey   
- Email: apoorvpandey0@gmail.com
- Github: [ApoorvPandey0](https://github.com/apoorvpandey0)
- Youtube: [Link](https://www.youtube.com/channel/UCqt-XHfPFjSZPV8WqWaTV8Q)
- Location: Bhopal, India
- Time Zone: UTC+530
- University: University Institute of technology RGPV, Bhopal
- Major: Information Technology

**Project Description**
=====================
- Name: [URL Shortener with a twist](https://ccextractor.org/public/gsoc/2022/urlshortener/)
- Mentor: [Undecided](#)
- Goal: Build a web based URL Shortener application which has features like simple email based authentication, Url opened notification, Ability to whitelist people based on email addresses. The application should be scalable and performant.


**About me**
=====================
I have expertise in building backend and mobile applications at scale, I have developed and am currently maintaining mobile applications with over 100,000+ downloads on Google play store [Kisan samadhan Play store link](https://play.google.com/store/apps/details?id=com.kisansamadhan.kisansamadhan&hl=en_IN&gl=US)

Apart from this also I have worked as a Freelancer and Youtube content creator in the past working on Flutter and Django for mobile and backend development. I have also interned at Bajaj Finserv for 6 months.


**Features of the application**
=====================
 - Shorten URL: Create a shortned URL from a given original URL, this could be  automatically assigned or choosen by the user from available links generated based on users preferance
 - Whitelist users based on emails for each URL, This would be an optional feature for each shortned url
 - Simple Email based authentication when opening URL, to login simply goto your email and click a link sent by our system to login. The link will be valid for 5 minutes and will be usable only one time (For security reasons)
 - Send email when a user from our whitelist opens our URL, this would also be a optional feature to select while creating a shortned url
 - Admin panel to manage Users, Emails and Urls, this would be useful for performing admin tasks

**User flow diagram**
=====================
  ![Diagram](UFD.png)

**Architecture**
=====================

### Frontend
Route  | Name | Description | 
------------- | ------------- | ------------- |
`/`| Home |Home page for our application containing project info and maybe some stats on how many url have we opened till now
`/<URL>`| Redirects to url | Redirect user to signin page if not signed in then checks if the url is valid and the current user has access to open it. If so then redirect to url page fetched from server and trigger `/urlOpened` api|
`/login`| Auth page | This is the auth page for our client application|
``| | |


### Backend
We will have the following API's:

Endpoint  | Name | Description | 
------------- | ------------- | ------------- |
`/sendEmail`  | Sends Email | Send email with auth link|
`/urlOpened` | sends mail | Sends url opened mail
`/login`  | Logs in user | Verifies auth code send via `/sendEmail` and returns a jwt token if correct |
`/checkURL` | Checks URLs | Checks if the user given url is available or not
`/createURL` | Creates URL in backend | Creates a shortened URL with all the features specified in json payload
`/profile` | User profile | Returns urls you have created with their basic details
`/getUrlDetails` | Gets all details of a url  | Fetches who viewed the particular url and other details like created date
`/openURL` | Checks and opens urls | If the given email has access to the url then redirect else say 404 url not found
`` |  |  |

 **Tech stack**
=====================
  ### 1. Backend - Django REST framework
  DRF is a modern API development framework which could be used to build applications at scale. 
  We can use PostgreSQL as our database.  

  ### 2. Frontend web - React JS


  ### 3. Frontend mobile - Flutter (Could be done later on or could be included in this GSOC project)


**Timeline**
=====================

## official overview

- **May 20**: accepted GSoC contributor projects announced;
- **May 21: - June 12**: community Bonding Period | GSoC contributors get to know mentors, read documentation, get up to speed to begin working on their projects;
- **June 13 - July 25**: coding officially begins;
- **July 26 - September 4**: work Period | GSoC contributors work on their project with guidance from Mentors;
- **September 5 - September 12**: final week.

## details

- **before May 20**
  - communicate with mentor to understand and details the goal of project;
  - get familiar with the websocket protocol, make a demo [here](https://github.com/Young-Flash/websockets-demo);
  - get the [qualification task](https://github.com/Young-Flash/translator) done.

- **May 21 - June 12**
  - clarify the RPC call process in details, replace SCGI routine with websocket in a thread; first make it work under tcp ip:port, then consider to add unix domain socket support
  - test the connection between rTorrent and websocket client (by [Postman](https://www.postman.com/))

- **June 13 - July 25**
  - implement "server push" capacity: design some callback function (notify client) to execute automatically when events happens (download state changes, etc), **current idea**: when the state of a torrent changes, `DL_TRIGGER_EVENT(download, event_name)` will be called, so we can hook event emitting here according to the parameter "event_name".
  - Take `event.download.finished` as example, when this event happens, websocket routine will send message below to client:
    ```json
    {
        "id":null,
        "jsonrpc":"2.0",
        "result":[
            {
                "torrent_hash_value":"F243DA99EB8A210A5B8AC480878B4564DF6BE221",
                "state":"finished",
                "time_stamp":1649656905
            }
        ]
    }
    ```
  - prepare for phase 1 evaluation

- **July 26 - August 4**
    - buffer week for any unpredictable problems

- **August 5 - September 4**
    - consider to add unix domain socket support for uWebsockets / uSockets, this may challenging as it not merely to set `AF_LOCAL` when socket setup, but need to consider both configuration and API compatibility. This work achieved initial progress, I will try to make a [PR](https://github.com/uNetworking/uWebSockets/pull/1486) to uWebSockets, other features should be add such as make it compiles on Windows, client connection function and benchmark, etc
    - try to reduce the granularity of lock in libtorrent;
    - prepare for the final evaluation

- **September 5 - September 12**
  - code style and quality review, dev documentation
  - prepare for final evaluation

**Why me**
=====================
I like modern C++ and the project was written in C++ 17, I also interested in network programming and the project requires websocket and RPC. I think my technology stack matches the requirements of this project. When I find this project and make some research on it (build and run rTorrent and read the source code of it, communicate with mentor about project requirements and details), I make a decision that all in this one and leave others for no consideration, this is also my usual style of doing things, making decisions after research and focusing on it attentively.

I love the way open source works, and participating in open Source activities has introduced me to things I'd never known before, improved my coding skills and met a lot of interesting people who I've enjoyed communicating with, and I hope to contribute more to the open source world. I first got involved with open source at Summer 2021 (mentioned above) last year, but my open source experience didn't end with the end of the activity, now I am a volunteer contributor in the Nebula Graph community, maintaining on the projects I was previously working on. If I'm lucky enough to be selected for this project, I'll take it seriously, keep contributing to the community by continuing to maintain it in the future. Although GSoC 2022 may be over, my enthusiasm for open source isn't.