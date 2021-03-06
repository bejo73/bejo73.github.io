---
layout: post
title: Use Azure Function trigger to avoid costly Logic Apps polling
---

The polling for files or messages in Logic Apps can be rather costly 
if the requirements are such that the file or message must be taken 
care of within shortly.

Polling every 10th second (one Logic App) for one month will generate
6 * 60 * 24 * 30 => 259200 actions. 

The monthly cost for this will be 250000 * 0,000675 + 9200 * 0,000338 = 171,8596 Euro
Actual prices 2017-08-11, See [Logic App Pricing](https://azure.microsoft.com/pricing/details/logic-apps){:target="_blank"}

Suppose we have at least 10 scenarios like this and the yearly cost will be
approximately 172 * 10 * 12 = 20640 Euro

One way to eliminate (almost) the polling cost is to let Azure Function triggers do the job.
The cost for that is almost nothing (less than one Euro), only cost for storage account and execution 
of function when the function is triggered.

So how do we do this?

In this example we want to take action when a new file is stored in a Dropbox folder.

Create a new Azure function and choose External File as input trigger. 
Select Dropbox as the API Connection.

![Azure Function Bindings](/images/blog/blog_2017-08-10-function_integrate.png)

Bindings:
![Azure Function Bindings](/images/blog/blog_2017-08-10-function_bindings.png)

Create a message to the Logic App containing data about the actual file.
The function will then call the Logic App.
Function:
![Azure Function Code](/images/blog/blog_2017-08-10-function_code.png)

The Logic App is triggered by the call from the Azure Function and the file can be processed.
![Logic Apps Designer](/images/blog/blog_2017-08-10-logicapps_designer.png)

![Logic Apps Codeview](/images/blog/blog_2017-08-10-logicapps_codeview.png)

Other blog posts addresses the Logic App polling case.

[Be careful of the Logic App Consumption Prizing model](https://peter.intheazuresky.com/2017/02/24/be-careful-of-the-logic-app-consumption-prizing-model/){:target="_blank"}

[Save costs by scheduling Logic Apps](https://www.codit.eu/blog/2017/03/23/save-costs-by-scheduling-logic-a
pps/){:target="_blank"}
