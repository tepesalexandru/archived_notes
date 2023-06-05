#azure 

KQL (Kusto Query Language) is a powerful tool to explore your data and discover patterns.

A Kusto query is a read-only request to process data and return results. Kusto queries are made of one or more query statemenets.

There are three kinds of query statements:
1. A tabular expression statement
2. A let statement
3. A set statement

All query statements are separated by a semicolon `;`

### Tabular Statements
The most common kind of query statement is a tabular expression statement, which means both its input and output consists of **tables** or tabular datasets.

Every statement starts with a tabular input and returns a tabular output, being chained together via the `|` pipe operator. The data flows from one operator to the next. The data is manipulated at each step and then fed into the following step.

It's like a funnel, where you start out with an entire data table, and at the end you're left with a refined output.

Let's look at an example query.

```KQL
StormEvents 
| where StartTime between (datetime(2007-11-01) .. datetime(2007-12-01)) 
| where State == "FLORIDA" 
| count
```

### Let Statements
You can create variables in KQL by using the `let` statement.

Using a `let` statement is useful for:
1. Breaking up a complex expression into multiple parts, each represented by a variable
2. Defining constants outside of the query body for readability
3. Defining a variable once and using it multiple times within a query

Let's take a look at a few `let` statements.

```KQL
let targetLocation = "New York";
let yesterday = ago(1d);

Events
| where city == targetLocation
	and date > yesterday
```

### Set Statements
You can use a `set` statements to set a query option for the duration of the query.

`Query options` control how a query executes and returns.

Query options can either be boolean or integers.

An example set statement is the following:

```KQL
set servertimeout=1d;
Onboarding
| summarize sum(Score)
```

### Learn KQL
A great resource to learn about KQL is https://detective.kusto.io/ , check it out!