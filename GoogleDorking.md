**1. What is Google Dorking?**

Google OSINT/Dorking, mean using Google search to gather intelligence (useful information) from open sources.
Google Dorking (also called **Google Hacking**) is the practice of using **advanced search operators** in Google to uncover information that is not easily visible through standard searches.
It’s not about breaking into systems — it’s about asking Google smarter, more specific questions to dig up things that most people never see.

Google Dorking command sheet:-
| Command        | Function                                                           | Example Search                       |
|----------------|--------------------------------------------------------------------|--------------------------------------|
| `site:`        | Searches only within a specific website/domain                     | site:bbc.com climate change       |
| `filetype:`    | Finds specific file types (PDF, DOCX, XLS, etc.)                   | `filetype:pdf cybersecurity report |
| `intitle:`     | Looks for pages with specific words in the title                   | `intitle:"login page"`               |
| `allintitle:`      | Finds or Search for pages with multiple words in the title         | `allintitle: security breach report` |
| `inurl:`           | Finds URL (link) with specific words in it                         | `inurl:admin`                        |
| `allinurl:`        | Finds pages with multiple words in the URL                         | `allinurl: login password`           |
| `cache:`           | Shows Google’s saved version of a webpage                          | `cache:example.com`                  |
| `related:`         | Finds websites similar to the one searched                         | `related:nytimes.com`                |
| `define:`          | Shows definitions of a word/term                                   | `define:OSINT`                       |
| `link:`            | Finds page that is link to a specific url                          | `link:example.com`                   |
| `intext:`          | Searches for a specific word inside the body text of a webpage.    | `intext:"reset password"`            |
| `allintext:`       | Searches for all the given words inside the body text of a webpage.| `allintext:database leak`            |
| `inanchor:`        | Searches for a word/phrase in the anchor text (the clickable text) | `inanchor:download`                  |
| `allinanchor:`     | Searches for pages where the anchor text contains all given words. | `allinanchor:cyber security tools`   |
| `..` range         | Searches numbers in a range (like dates, prices)                   | `cyber attack 2018..2023`            |
| `map:`             | Opens Google Maps for the specified location                      | `map:coffee shops near me`         |
| `around(X)`        | Finds two terms within *X* words of each other (proximity search) | `AI AROUND(5) ethics`              |
| `before:`          | Shows pages published before a specific date                      | `climate change before:2020-01-01` |
| `after:`           | Shows pages published after a specific date                       | `AI after:2021-06-01`              |
| `info:`            | Displays info about a website                                     | `info:openai.com`                  |
| `movie:`           | Retrieves details about a movie                                   | `movie:Inception`                  |
| `weather:`         | Shows weather for a location                                      | `weather:London`                   |
| `phonebook:`       | Searches for contact info like phone numbers                      | `phonebook:John Doe`               |
| `source:`          | Searches within a specified news source                           | `AI source:nytimes`                |
| `allinmeta:`       | Finds pages with all specified words in metadata                  | `allinmeta:keyword1 keyword2`      |
| `inmeta:`          | Searches for a word in page metadata                              | `inmeta:description`               |
| `allintext:`       | Finds pages with all specified words in body text                 | `allintext:cyber security leak`    |
| `numrange:`        | Finds results within a number range (years, prices, etc.)         | `camera $100..$200`                |
| `post intitle:`    | Finds blog posts with words in the title                          | `post intitle:"tutorial"`          |
| `blogurl:`         | Finds blogs with URLs containing a specific keyword               | `blogurl:tech`                     |
| `allinpostauthor:` | Finds blog posts by a specific author                             | `allinpostauthor:"John Doe"`       |
| `author:`          | Searches for content by a specific author                         | `author:Jane Doe`                  |
| `patent:`          | Searches patents (via Google Patents)                             | `patent:"light bulb"`              |
| `parentdir:`       | Finds open directory listings                                     | `intitle:"index of" parentdir`     |
| `insubject:`       | Searches within email subject lines                               | `insubject:"meeting"`              |
| `indomain:`        | Searches results only within a specific domain                    | `indomain:harvard.edu AI`          |
| `group:`           | Searches Google Groups for discussions/posts                      | `group:machinelearning`            |
| `isbn:`            | Finds books by their ISBN number                                  | `isbn:9780131103627`               |
| `imgtype:`         | Searches for images of a specific type (clipart, face, etc.)      | `cats imgtype:clipart`             |
| `linkdomain:`      | Finds sites linking to a specific domain (similar to `link:`)     | `linkdomain:mit.edu`               |
| `intitle:index.of` | Finds open directory listings                                     | `intitle:index.of "mp3"`           |

Speacial Operator
| Command        | Function                                                              | Example Search                      |
|----------------|--------------------------------------------------------------------|--------------------------------------|
| `" "` (search term)| Finds the **exact phrase** inside quotes.                         | `"digital marketing strategy"`     |         
| `OR`               | Finds results with **either one term or the other**.              | `python OR java`                   |        
| `-`(Minus Operator)| **Excludes** results containing the specified word.               | `apple -fruit`                     |  
| `+` (Plus Operator)| Used to **force include** a word (rarely needed now, as Google does it by default). | `cats +cute`     |  
| `*` (Wildcard Operator) | Acts as a placeholder for any unknown/missing word.      | `"machine * learning"`             |  
| `()` (Grouping)         | Groups queries together for complex searches.     | `(site:.edu OR site:.org) intitle:research` |  
| `intitle:index.of` | Finds open directory listings                                  | `intitle:index.of "mp3"`             |
