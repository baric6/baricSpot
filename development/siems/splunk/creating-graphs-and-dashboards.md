# Creating Graphs and Dashboards

## To make a basic graph like pie, bar or line

1. in the search find what kind of data you are looking for
2. you will find the data is setup like a json file

#### Example:

{ category: first, eventData: \[ location: Denver, IP:169.254.0.0 ] }

{ category: first, eventData: \[ location: Denver, IP:169.254.0.0 ] }

{ category: first, eventData: \[ location: New York, IP:169.254.0.1 ] }

3. We can group this data by any of the data by adding the `stats` command to the search

#### Example:

\<your query > |  stats count by location

4. this should count all the same locations and group them by like names. In this example&#x20;

Denver  |  2

New York | 1

5. you should be able to click over to the visualization tab to see a graph

<figure><img src="../../../.gitbook/assets/image (386).png" alt=""><figcaption></figcaption></figure>

6. you should see something like this:
   1. it could be a bar, pie, ect.. depending on what you got selected
   2. you can select a chart by in this example clicking on the pie chart name in the top left corner of the image

<figure><img src="../../../.gitbook/assets/image (387).png" alt=""><figcaption></figcaption></figure>

## Adding graph to A Dashboard

1. in the top right of the page where you are viewing the graph you should see:

<figure><img src="../../../.gitbook/assets/image (388).png" alt=""><figcaption></figcaption></figure>

2. under the save as you have the option to&#x20;
   1. create a report&#x20;
   2. create a alert&#x20;
   3. add to a existing dashboard&#x20;
   4. create a new dashboard&#x20;
3. for this we will be selecting New Dashboard
4. when a new popup opens

<figure><img src="../../../.gitbook/assets/image (389).png" alt=""><figcaption></figcaption></figure>

5. fill in dashboard title, select dashboard studio, select grid, under panel title name the graph  and save to dashboard and you have a new dashboard with the data

## Saving graph to Existing Dashboard

1. after creating a graph select save as
2. when selecting existing dashboard choose a dashboard you have previously made&#x20;
3. fill in the panel title to name the graph
4. save to dashboard
