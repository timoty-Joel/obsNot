## Organize Data for More Effective Analysis

Analysis ⇒ Process used to make sense of the data collected
Goal      ⇒ To identify trends and relationships within the data so that you can accurately
answer the question you're asking

![[4phases_analysis.png]]
**The 4 phases of analysis:**
1. Organize data
2. Format and adjust data ⇒ An analyst sorts and filters data during the format and adjust analysis phase.
3. Get input from others ⇒ Getting input involves soliciting information from other sources to inform your decisions.
4. Transform data ⇒ Involves identifying relationships and patterns in the data, and making calculations.

### Organize Data to Begin the Analyze

It's super important that you keep your data organized throughout your analysis. How your data is classified and structured will impact your findings, whether you're working in a spreadsheet or a database.

Most of the data you'll use in your analysis will be organized in tables. Tables help you organize similar kinds of data into categories and subject areas that you can focus on as you analyze.

-  For an example :
	![[ex_table.png]]
    
    The structure above is a structure from a database that has tables like: Car dealerships, Product details, and Repair parts.
    
    Each table then has several fields of data, like branch owner and the cost of repair parts. You can use these tables and fields to help you decide how to move forward with your analysis. The structure of this database can help you decide which data you need to pull to meet your objectives. For example, the total number of a particular brand of car sold, or a repair part for a specific make and model of a car at a certain branch.

Database organization(the structure of the database) enables analysts to make decisions about which data is relevant to pull for a specific analysis. It also helps them decide which data types and variables are appropriate.

If you're performing your analysis in a spreadsheet, you want to make sure that the columns and rows are effectively organized. You can hide columns that you won't need for analysis or that show duplicate information. Once you have the data organized and formatted, you'll be ready to sort and filter it to find the data you need.

### Keep Data Organized by Sorting and Filtering

We can use sorting and filtering methods to organize, format, and adjust data. For example, a filter can help you find errors or outliers so you can fix or flag them before your analysis.

Outliers ⇒ data points that are very different from similarly collected data and might not be reliable values.

The benefit of filtering the data is that after you fix errors or identify outliers, you can remove the filter and return the data to its original organization.

**Sorting** ⇒ Process of arranging data into a meaningful order to make it easier to understand, analyze, and visualize. It ranks your data based on a specific metric you choose. You can sort data in spreadsheets, SQL databases (when your dataset is too large for spreadsheets), and tables in documents.
To rank items or create chronological lists, you can sort by ascending or descending order. Sorting arranges the data in a meaningful way and it gives you immediate insights and helps you to group similar data by classification.

**Filter** ⇒ Used to show only the data that meets a specified criteria while hiding the rest. Filtering is useful when you have lots of data. You can save time by zeroing in on the data that’s important for your current analysis or the data that contains errors. 
Most spreadsheets and SQL databases allow you to filter your data in a variety of ways. Filtering gives you the ability to find what you are looking for without too much effort.

**Pivot table** ⇒ A data summarization tool used to sort, reorganize, group, count, total, or average data. Items in the row and column areas of a pivot table are sorted in ascending order by any custom list first.

To filter data with SQL, we can do it by using ‘WHERE' clause.