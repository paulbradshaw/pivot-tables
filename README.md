# Resources for building skills with pivot tables

You can [find a screencast I've made about pivot tables here](https://www.youtube.com/watch?v=wKQznyIHOys), or just search Google or YouTube for tutorials on pivot tables until you find one that works for you. The short ebook [Data Journalism Heist](https://leanpub.com/DataJournalismHeist) explains how to use pivot tables as well as lots of other useful quick techniques for getting stories out of data.

## Case study 1: investigating Nigerian football agents

At the beginning of an [investigation into Nigerian football agents](https://vimeo.com/187993647) (you can [read it on Premium Times](https://www.premiumtimesng.com/news/194420-investigation-how-nigerian-young-footballers-are-trafficked-abused-abroad.html) or [IQ4News](http://www.iq4news.com/follow-the-money/)), I collected details on hundreds of Nigerian football players to try to establish which agents had the most Nigerian players on their books. A simple pivot table gave me the answer. It's a good example of how pivot tables can give you an overview of a field and help you focus on the most important parts.

[Download this spreadsheet from an investigation into Nigerian football agents](https://github.com/paulbradshaw/nigerian-footballers/raw/master/nigerianfootballersonly.xlsx) - or make a copy of [this Google sheet version](https://docs.google.com/spreadsheets/d/1yvqC9_T1o5OgDo9JyLhJPjmGTq2Mf0_PpbgZ-BsKxEo/edit?usp=sharing)

Create a pivot table. You will need:

* In **rows**: *agent*
* In **values**: *agent* again. This is because you want to COUNT how many mentions there are of each agent. 

The pivot table will be sorted alphabetically (A-Z) by agent. But you want to sort it numerically by count of agent (values). To do this in Excel, click anywhere in the column of numbers, and then click the small Z-A sort button in the *Data* menu. In Google Sheets you need to use the pivot table sort option.

## Case study 2: investigating the Olympic Torch Relay

In 2012 I came across the official Olympic Torch Relay website, which listed every torchbearer with details on where they came from, where they would be carrying the torch, their age, and their nomination story. Simple sorting helped identify the youngest and oldest torchbearer, while filters helped drill down to find local stories on who was carrying a torch from 'your area'.

Pivot tables, however, could provide an overview to show what sort of age distribution there was (the organisers had stated that a quarter of torchbearers would be 16-24 as part of a celebration of youth), and which parts of the country were best (or least) represented.

