# SPL Breakdown

### Comparison Operators

<figure><img src="../../../../.gitbook/assets/681a126a98263612b87def7014583ffb.png" alt=""><figcaption></figcaption></figure>

| <p>Field Name<br></p>               | <p>Operator<br></p> | <p>Example<br></p>                  | <p>Explanation<br></p>                                                                                                                                                        |
| ----------------------------------- | ------------------- | ----------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>Equal<br></p>                    | <p>=<br></p>        | UserName=Mark                       | <p>This operator is used to match values against the field. In this example, it will look for all the events, where the value of the field UserName is equal to Mark.<br></p> |
| <p>Not Equal to<br></p>             | <p>!=<br></p>       | UserName!=Mark                      | <p>This operator returns all the events where the UserName value does not match Mark.<br></p>                                                                                 |
| <p>Less than<br></p>                | <p>&#x3C;<br></p>   | Age < 10                            | <p>Showing all the events with the value of Age less than 10.<br></p>                                                                                                         |
| <p>Less than or Equal to<br></p>    | <p>&#x3C;=<br></p>  | Age <= 10                           | Showing all the events with the value of Age less than or equal to 10.                                                                                                        |
| <p>Greater than<br></p>             | <p>><br></p>        | <p>Outbound_traffic > 50 MB<br></p> | <p>This will return all the events where the Outbound traffic value is over 50 MB.<br></p>                                                                                    |
| <p>Greater Than or Equal to<br></p> | <p>>=<br></p>       | Outbound\_traffic >= 50 MB          | This will return all the events where the Outbound traffic value is greater or equal to 50 MB.                                                                                |



### Boolean Operators

<figure><img src="../../../../.gitbook/assets/42c8963dccbd05128f52665c38877f47.png" alt=""><figcaption></figcaption></figure>

| <p>Operator<br></p> | <p>Syntax<br></p>                           | <p>Explanation<br></p>                                                                  |
| ------------------- | ------------------------------------------- | --------------------------------------------------------------------------------------- |
| <p>NOT<br></p>      | <p>field_A NOT value<br></p>                | <p>Ignore the events from the result where field_A contain the specified value.<br></p> |
| <p>OR<br></p>       | <p>field_A=value1 OR field_A=value2<br></p> | <p>Return all the events in which field_A contains either value1 or value2.<br></p>     |
| <p>AND<br></p>      | field\_A=value1 AND field\_B=value2         | Return all the events in which field\_A contains value1 and field\_B contains value2.   |



### Wild Card

<figure><img src="../../../../.gitbook/assets/5530cae0739755e6a682641f5057b1a5.png" alt=""><figcaption></figcaption></figure>

| Wildcard symbol  | <p>Example   <br></p> | <p>Explanation         <br></p>                                                                 |
| ---------------- | --------------------- | ----------------------------------------------------------------------------------------------- |
| <p>*<br><br></p> | status=fail\*         | <p>It will return all the results with values like</p><p>status=failed</p><p>status=failure</p> |



### Fields

<figure><img src="../../../../.gitbook/assets/dd77983b5fccf5eacfa73aacbeb7a314.png" alt=""><figcaption></figcaption></figure>



### Search

<figure><img src="../../../../.gitbook/assets/02d2ece97e7f977e32b4c11fd86e41eb.png" alt=""><figcaption></figcaption></figure>



### Dedup

The command used to remove duplicate fields from the search results. We often get the results with various fields getting the same results. These commands remove the duplicates to show the unique values.

<figure><img src="../../../../.gitbook/assets/47bb3fb904c84acdbe7cb89dda535ac1.png" alt=""><figcaption></figcaption></figure>



### Rename

<figure><img src="../../../../.gitbook/assets/61e56df15649aa12b4be7c91d8cc91ce.png" alt=""><figcaption></figcaption></figure>



### Table

<figure><img src="../../../../.gitbook/assets/643f5cc127276645eb0fd7fdb339cb29.png" alt=""><figcaption></figcaption></figure>



### Head

The head command returns the first 10 events if no number is specified.

<figure><img src="../../../../.gitbook/assets/3a9df7382d1f5e2e3302750dc5016809.png" alt=""><figcaption></figcaption></figure>



### Tail

The Tail command returns the last 10 events if no number is specified.

<figure><img src="../../../../.gitbook/assets/917811648cc95bd3f34c820a473b9c1b.png" alt=""><figcaption></figcaption></figure>



### Sort

<figure><img src="../../../../.gitbook/assets/9589d101b5a07f69fc4771a6c1e54e14.png" alt=""><figcaption></figcaption></figure>



### Reverse

The reverse command simply reverses the order of the events.

<figure><img src="../../../../.gitbook/assets/0de4064ec74ee5f64a399e0a7bed9200.png" alt=""><figcaption></figcaption></figure>



### Top

This command returns frequent values for the top 10 events.

<figure><img src="../../../../.gitbook/assets/ffef6c0a6ce0159e6d970de2c32921a3.png" alt=""><figcaption></figcaption></figure>



### Rare

This command does the opposite of top command as it returns the least frequent values or bottom 10 results.

<figure><img src="../../../../.gitbook/assets/8123e0932c169514d9842fbba8f5898c.png" alt=""><figcaption></figcaption></figure>

### Highlight

The highlight command shows the results in raw events mode with fields highlighted.

<figure><img src="../../../../.gitbook/assets/61ad47b204639fa0f75b278bec21abac.gif" alt=""><figcaption></figcaption></figure>



### Stats

| <p>Command<br></p> | <p>Explanation<br></p>                                            | <p>Syntax<br></p>                  | <p>Example<br></p>                 |
| ------------------ | ----------------------------------------------------------------- | ---------------------------------- | ---------------------------------- |
| <p>Average<br></p> | This command is used to calculate the average of the given field. | stats avg(field\_name)             | stats avg(product\_price)          |
| <p>Max<br></p>     | It will return the maximum value from the specific field.         | stats max(field\_name)             | stats max(user\_age)               |
| <p>Min<br></p>     | It will return the minimum value from the specific field.         | stats min(field\_name)             | stats min(product\_price)          |
| <p>Sum<br></p>     | It will return the sum of the fields in a specific value.         | stats sum(field\_name)             | <p>stats sum(product_cost)<br></p> |
| <p>Count<br></p>   | The count command returns the number of data occurrences.         | stats count(function) AS new\_NAME | stats count(source\_IP)            |





### Chart

The chart command is used to transform the data into tables or visualizations.

<figure><img src="../../../../.gitbook/assets/a954b0a1d37542650df294461d756c61.gif" alt=""><figcaption></figcaption></figure>



### Timechart

The timechart command returns the time series chart covering the field following the function mentioned. Often combined with STATS commands.

<figure><img src="../../../../.gitbook/assets/bc7f90e4f40be4c047d250d5e3ee44c8.gif" alt=""><figcaption></figcaption></figure>
