# How to read the results of a query in Power BI using Power Automate
- Make the query
- Insert a Analysis JSON form Data Operations
    - Use a template for First rows from the table
    - It will have the format [{"Value":234343}]
    - It is an array of objects
- Use a For each
- Insert inside a *Insert rows in Power BI dataset*
- You can use the Value from the previous step

# Streaming semantic model prerrequisite
- When creating a streaming semantic model use the option *Allow historic analysis*
- Number and date are important to keep the consistency of types.

# Migrate flows and solutions
- It is necessary to select *create new* for the flows

# Parse a CSV
- OneDrive get file
- Initialize an array variable with `chunk(split(replace(body('GetFile'),decodeUriComponent('%0D%0A'),','),','),4)`
- Loop with Apply to each
- Create a Sharepoint item atribute use `item()[0]`
