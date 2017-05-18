Introduction
------------

Please include introduction here.

Loading of data
---------------

Let's load up our data. We have two main CSV files given from the Kaggle website:

Taking a peek at the data
-------------------------

Let's first look at the data we have by looking at the first few rows.

### train.csv

### store.csv

Cleaning of data
----------------

Let's clean up the data. First, let us review the data types of each column.

Looks like we are dealing with a mix of int and chr data types. Here are some quick takeaways:

-   dt\_train
    -   Date is currently a chr data type. We will change it to DATE type.
    -   StateHoliday is categorical (4 categories)
    -   SchoolHoliday is binary
    -   When Open == 0, then Sales == 0 (as expected)
    -   No NA's are found
-   dt\_store
    -   StoreType is categorical (4 categories)
    -   Assortment is categorical (3 categories)
    -   Promo2 is binary
    -   PromoInterval describes the consecutive intervals Promo2 is started.

First, change Date column to DATE type, and also add columns for Year,Month and Week.

Understanding our data
----------------------

We will be looking at our data this time per column. First of all, let us note how much data we are dealing with.

Let us check dt\_store to make sure that each store ID has one row.

As it is TRUE, then the unique number of Store ID's match the number of rows. Therefore, there is no duplicate Store ID.

#### Store

This seems to be the store ID that we can use to match dt\_store with dt\_train. We can use this to join the two data sets.

#### DayOfWeek

The number represents the day of the week

#### Date

Calendar date of the reported sales

#### Sales

The sales recorded (if store is Open).

#### Customers

The number of customers of that Date

Let's see if there are any stores that were Open and had 0 Customers

Ah! There are 52 instances. Let's break it down later.

#### Open

0 -&gt; closed; 1 -&gt; open. If 0, then Sales = 0.

Let's rank the stores by the number of days they were Open

Were all of the stores open since day 1 of our data set?

Well that isn't much. Probably because of New Year.

That looks better.

Let's plot the % of stores open across the time period without including StateHoliday, SchoolHoliday, and Sundays (for all stores):

#### Promo

Indicates whether a store is running a promo on that day.

Did the company run store-specific sales (i.e. only certain stores ran the promo)? Let's try to find out. Let's take the percentage of the total number of Rows with Promo == 1 by the total number of Rows, and do it per Date. Let's look at the number of rows that is between 0 and 100%.

Ah there is none. How about looking at the values? First, let's see how many Dates have Promos being run, but not as many as the total number of stores (1115)

Oh. There are 74 Dates. Let's take a look at one and see what's happening. First, let's make two temporary data.tables and set their keys to Date. Then let us query dt\_train with Dates of those 74 instances.

We see that it only happened between 2014-07-01 to 2014-12-19. We also note that are stores that are closed, but it has been recorded that there is a Promo. Let's take a look:

We have to just keep this in mind that having a Promo does not mean the store was Open, even when there were no holidays.

#### StateHoliday

a -&gt; public holiday b -&gt; Easter holiday c -&gt; Christmas 0 -&gt; None

Let's check the integrity of the StateHoliday. We want to make sure that at a given StateHoliday, all of the stores have the StateHoliday field correctly identified. For example, during Christmas (StateHoliday = c), are there any stores that do have StateHoliday != c?

Let us investigate Public Holiday. Can we find the dates where StateHoliday is not only a?

Let's look at one of these dates and see the percentage of stores that were still open:

Later on, let's try to find out what may have cause these stores to be open still. Could public holiday just be limited to certain areas?
