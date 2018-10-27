# pivot-to-excel


## Warm-up: Helpful Cleaning Functions

We'll start by using the Data Cleaning spreadsheet.

### YEAR(), MONTH(), DAY(), DATE() 
**YEAR()** returns the year of a date field
**MONTH()** returns a numeric month
**DAY()** returns a number between 1 and 31 to represent the day of the month

### DATEDIF()

### =IF(condition, true answer, false answer)

Hey, I want to calculate how old someone is. I have a DOB field. EASY. Combine DATEDIF with TODAY.

#### =DATEDIF(A2,TODAY(),"Y")

* This is a date calculation
* Use cell A2
* Calculate the difference between today's date and the date in cell A2
* Return the answer in years

### RANK

This is useful in elections, for salaries, etc.

Use RANK to order something. The dollar signs I've used here are anchors, meaning they tell Excel to keep the formula constant even if you move the fields containing the RANK function.

#### =RANK(A2,$A$2:$A$500)

### RIGHT, LEFT, MID

Let's say you have a name column with a First Name and a Last Name (or a combined City State) but you need those in their own columns. EASY.

The RIGHT function, as the name suggests, will extract a specified amount of text starting from the right side of the cell. Example: =RIGHT(A2,2) would extract the first two characters of a cell starting from the right.

The LEFT function, as the name suggests, will extract a specified amount of text starting from the right side of the cell. Example: =LEFT(A2,2) would extract the first two characters of a cell starting from the left.

MID, as you might expect, extracts the text beginning at a mid-point of a cell, but it needs a little more direction than RIGHT and LEFT. MID wants to know which cell, the numeric position in the cell, and how many characters to extract. Example: =MID(A2,3,1)

LEFT, RIGHT and MID are often used with other functions: SEARCH, FIND and LEN().

(Note: SEARCH and FIND are very similar, but SEARCH is not case-sensitive and also can accept wildcards.)

Apply this with our Name field cleaning example.

Try LEFT, with SEARCH. To retrieve the First Name from a Full Name column, or City Name in the combined City State example, make a new column and name it appropriately. Then, in your new, blank column: 

### =LEFT(A2,  SEARCH(" ",A2,1))

What we're telling Excel to do here is:
* Start from the left side of the cell
* We're talking about cell A2, specifically
* Scan the cell until you find the space, which we denote as " "
* We're still talking about cell A2 here
*  Account for the space

Try RIGHT, with LEN and SEARCH. To retrieve the Last Name from a Full Name column, or State Name in the combined City State example, make a new column and name it appropriately. Then, in your new, blank column:

### =RIGHT(A2,LEN(A2)-SEARCH(" ",A2,1))

You need the LEN function to tell Excel the total number of characters in the cell, and then you subtract the position of the space (" ").

Now you've taken it all apart. Need an all-in-one name field or need to combine other fields? Try CONCATENATE.

### =CONCATENATE(CELL1," ",CELL2)


## NOW WE PIVOT

Look, I'll be honest: Some of this will be trial and error. You'll need to get comfortable with how to set up your table. But we're looking at four basic steps here:

1. Highlight the data you want to pivot (Friends, highlight the whole dang table)
2. Go to Insert -> PivotTable -> PivotTable
3. Whoa! There's a box. Make sure New Worksheet is selected under "Choose where you want the PivotTable report to be placed" so you don't clobber your existing data. Click OK.
4. Build. That. Pivot.

### More on that.

If you followed the steps above, you should have a nice blank table with a box on the right that says "PivotTable Field List." That's where you're going to select your fields.

This is a drag-and-drop proposition. 

* Drag something into the "Row Labels" box. As the name implies, this will be what your rows are labeled. This is what your table will be organized by. (If you're counting the bushels of apples by farm, drag the farm into the Row Labels field.)
* Drag what you want to count/sum/average into the "Values" field.
* Click on the Values drop-down menu to select how you want to calculate.

Experiment with moving fields around, counting different things, and filtering until you're more comfortable. 

### Here are some things to know:

* You can sort within a PivotTable, just like anywhere else in Excel.
* You can calculate new fields. Want a field with percentage change? You can make it, and it's easy.
* Annoyed by the way Excel is subtotaling your rows field? Click into the header and uncheck the Subtotals feature.


_jrichards@chicagotribune.com   @jsmithrichards_
