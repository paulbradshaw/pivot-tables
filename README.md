# Resources for building skills with pivot tables

You can [find a screencast I've made about pivot tables here](https://www.youtube.com/watch?v=wKQznyIHOys), or just search Google or YouTube for tutorials on pivot tables until you find one that works for you. The short ebook [Data Journalism Heist](https://leanpub.com/DataJournalismHeist) explains how to use pivot tables as well as lots of other useful quick techniques for getting stories out of data.

## Case study 1: investigating Nigerian football agents

At the beginning of an [investigation into Nigerian football agents](https://vimeo.com/187993647) (you can [read it on Premium Times](https://www.premiumtimesng.com/news/194420-investigation-how-nigerian-young-footballers-are-trafficked-abused-abroad.html) or [IQ4News](http://www.iq4news.com/follow-the-money/)), I collected details on hundreds of Nigerian football players to try to establish which agents had the most Nigerian players on their books. A simple pivot table gave me the answer. It's a good example of how pivot tables can give you an overview of a field and help you focus on the most important parts.

### Using pivot tables

[Download this spreadsheet from an investigation into Nigerian football agents](https://github.com/paulbradshaw/nigerian-footballers/raw/master/nigerianfootballersonly.xlsx) - or make a copy of [this Google sheet version](https://docs.google.com/spreadsheets/d/1yvqC9_T1o5OgDo9JyLhJPjmGTq2Mf0_PpbgZ-BsKxEo/edit?usp=sharing)

Create a pivot table. You will need:

* In **rows**: *Agent*
* In **values**: *Player*. This is because you want to COUNT how many players there are for each agent (COUNTA in Google Sheets). 

The pivot table will be sorted alphabetically (A-Z) by agent. But you want to sort it numerically by count of agent (values). To do this in Excel, click anywhere in the column of numbers, and then click the small Z-A sort button in the *Data* menu (Z-A means descending, i.e. largest to smallest; A-Z means ascending, i.e. smallest to largest). 

In Google Sheets it's a bit trickier to sort by values: in the pivot table builder on the right, look in the **rows** box for the drop-down menu *Sort by:*. Currently it is sorting by agent but you can change it to *COUNTA of Player*. To the left there is an *Order:* option. Change this to **Descending** so that it orders from largest to smallest).

Which agents have the most players?

## Case study 2: investigating the Olympic Torch Relay

In 2012 I came across the official Olympic Torch Relay website, which listed every torchbearer with details on where they came from, where they would be carrying the torch, their age, and their nomination story. This was the beginning of a series of stories across national and local newspapers in the UK and internationally, TV and radio, and questions in Parliament. The full story is told in the short ebook [8000 Holes](https://leanpub.com/8000holes).

Once I had gathered data from the website, I began with simple data techniques: **sorting** helped identify the youngest and oldest torchbearer, while **filters** helped drill down to find local stories on who was carrying a torch from 'your area'.

**Pivot tables**, however, could provide an overview to show what sort of age distribution there was (the organisers had stated that a quarter of torchbearers would be 16-24 as part of a celebration of youth), and which parts of the country were best (or least) represented.

### Using pivot tables

[Download this spreadsheet from the investigation](https://github.com/paulbradshaw/olympic-torch-relay/raw/master/torchbearersMay24_TO_Jul24.xlsx) - or make a copy of [this Google sheet version](https://docs.google.com/spreadsheets/d/1ICs1kw0_bm5gYp_l1-vv6gzUGM6cgppf9-oVjysx8pE/edit?usp=sharing)

Create a pivot table. You will need:

* In **rows**: *Age*
* In **values**: *Name*. This is because you want to COUNT how many names there are for each age (COUNTA in Google Sheets). 

The pivot table will be sorted numerically (A-Z) by age. You could use this to create a chart to show the distribution of age (a histogram is best for this), among other things. But the first question you can answer this this is:

* The organisers promised that a quarter of places would go to people aged 25 and under. Did they fulfil that promise?

By changing the pivot table to focus on other aspects of the data, and sorting in different ways, see if you can also answer these questions:

* How many torchbearers were there from each town/city? Which areas had the most?
* Which locations have the most torchbearers running in them? 
* Do any names appear more than once? How could you tell if they're the same person or different people?

### Using a formula to add more information

Your spreadsheet now has two sheets: the pivot table sheet, and the sheet containing the original data. Switch back to the sheet containing the original data (7000 torchbearers).

We are going to add a new column which tells us if a nomination story contains a particular word - specifically, "Adidas", one of the major sponsors of the Olympics.

Insert a new column between columns A and B - the best way to do this is to click on the 'B' for column B and then select *Insert > Columns* (or right-click on the B and select it from the menu that appears).

A new empty column should now appear, which is now column B.

Give it a title of 'Adidas' in the first cell of that column (this cell is B1 - column B, row 1).

Underneath that (cell B2), type the following formula:

`=SEARCH("adidas",C2)`

Press Enter. You will get a `#VALUE!` error. That's fine - it just means that it didn't find the word you were looking for. That will be the case for most stories, but we're going to see some where it gives a different, more useful, result.

First, let's break that formula down.

1. An equals sign: `=`
2. The word `SEARCH`
3. Some parentheses
4. The word `"adidas"` in quotation marks (the quotation marks are important)
5. A comma
6. A cell reference: `C2`

Here's what each is doing:

* The equals sign tells the spreadsheet that we want it to do some work, rather than just store information that we are typing. If you want to use a formula in a spreadsheet always begin with `=`
* The word `SEARCH` is what's called a **function**. This is a quick way of asking a spreadsheet to perform a particular calculation or series of steps that is quite common. The best known functions are `AVERAGE` and `SUM` which tell the spreadsheet to calculate an average or add up a series of numbers, but there are hundreds of others to solve all sorts of common (and less common) problems. `SEARCH` is a function which will look for a particular word or phrase within a specified cell (both of which we're about to specify) and tells you where it is (i.e. what position it starts at, such as from the 5th character onwards)...
* A function is always followed by **parentheses**: these contain any ingredients that you need to specify, each ingredient separated by a **comma**. For `SEARCH` we need to first specify the word or phrase we want to search *for*, and second, the cell reference we want it to search *in*.
* The word we want to search for is `"adidas"`. This has to go in quotation marks to distinguish it as text rather than a function or cell reference (indeed, we could instead put the word *adidas* in another cell and use a cell reference instead). The `SEARCH` function is not case sensitive, so it doesn't matter whether `adidas` has a capital A or not.
* The cell we want to search in is `C2`. Note that this doesn't have quotation marks because it is a cell reference. Any cell references will be changed when we copy the formula elsewhere, as we'll see...

Now that you understand the formula, it's time to copy it into another cell to demonstrate something else.

So, **copy cell B2** (the cell that contains your formula) and **paste it into cell B3** underneath.

Now look at the formula in the new cell. Note that it has changed slightly to this: 

`=SEARCH("adidas",C3)`

The `C2` has changed to `C3`. This is because the spreadsheet assumes that you don't want to search C2 *again*, but instead want to *repeat* the formula for a new cell. Because you have copied the formula downwards it changes the cell reference *relative* to where it was: in other words, it is still searching the cell on the same row, and one column to the right.

Now that you know it does this, you can copy it down the whole column. One way to do this is to first select the cell with the formula in it, then hover over the bottom right corner until you see a black cross, and finally double-click on that cross. The formula will be copied all the way down until it hits a row where there is nothing in the cell to the left (for that reason this is best done where the column to the left is full). Alternatively you can click and drag that black cross down to manually copy the formula.

It might take a few moments because there's a lot of data here...

OK. You should now have a column full of the results of that formula. Most are errors because there is no match.

Now you need to **sort** the data to bring the matches to the top. Click on any of the cells in that column and then use the small A-Z sort button (normally in the Data tab) to sort the whole dataset by that column, from smallest to largest. This should bring the numbers to the top.

Once sorted, the first entry should be Joanne Moseley: the 'adidas' column for her should show the number `8`. This is because the word 'adidas' begins at the 8th character in cell C2: "One of adidas' key concepts..." (note that spaces are counted as characters too).

The second entry is Anthony Barron, who mentions adidas 13 characters into his nomination story. Notice anything odd about that nomination story?

Look at the others, see if you find anything worth looking into further. What can you find out with a quick bit of googling?

## Case study 3: Pest control in Coventry!

Now you're used to using pivot tables, it's time to use those skills on a dataset which can be analysed in a number of different ways. Rather than telling you what to do, this time you need to think about potential stories and how you might get them.

The data [is pest control requests to Coventry City Council](https://www.coventry.gov.uk/downloads/download/4823/pest_control_service_requests). These are split between a different dataset for each financial year, and are in CSV format, which is a very simple spreadsheet format that can be opened in any spreadsheet tool (it also keeps file size down).

But because I am nice I have already combined *all* those CSVs into one Excel spreadsheet, which [can be downloaded from here](https://github.com/paulbradshaw/pivot-tables/raw/master/Pest_Control_Service_Requests_2013_2017_dataonly.xlsx). 

In fact, I am even nicer than that: I have also added some new columns which show: the year for each report; the month; the postcode district (this is the first part of a postcode); and the ward (an area of the city which elects councillors to represent it at the local council). (see notes below)

Look at what data you have and think about different stories you might try to find in this data. Each column should give you different ideas. 

The next task is to try to get those stories (or at least the basis for them) using a pivot table.

### Notes on the extra data

The year, month and postcode district were all added using a particular spreadsheet function to extract it from the date column (DTRECD) and the postcode column (POSTCD). Use Google to try to find out how you could do that yourself.

The ward was a bit more complicated. You can convert postcodes to ward, constituency etc. using [Doogal's 'batch geocoding' tool](https://www.doogal.co.uk/BatchGeocoding.php). First, generate a list of all the postcodes by using a pivot table (put the postcodes in the 'row' box - no need to do anything else). Next, copy and paste that list into the box on Doogal. Tick the box that says *UK administrative info*. Then click **Geocode**. 

You may have to wait a while for the site to convert all the postcodes. Once it's finished, look at the results in the **Text** tab underneath (the other tabs are 'Map', 'KML' and 'FAQ') and click **Download text**. This will download a CSV spreadsheet which can be added as a new sheet in your existing spreadsheet.

This sheet of postcodes and the wards that they are in (as well as other info) can be used with a `VLOOKUP` function to grab the ward for each postcode in your original data. How do you use that function? Google it...

You can use the same function to bring in the populations for each ward (the ONS should have that) to create per capita figures.

### Some things to try

* Pivot by ward & count of reports to find out ward with most reports (but is that just the most populous ward?)
* Add filter to see rats only 
* Add filter to see 2017 only 
* Add columns to see month by month pattern 
* Remove 2017 filter to see over all years
* Replace months in columns with years to see annual change 
* Replace ward in rows with pest to see change by pest 

