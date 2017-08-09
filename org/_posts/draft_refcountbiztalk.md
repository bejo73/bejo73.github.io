Ref counts
Ref counts show that there are messages in the messagebox without any references, or the other way around. It's not a critical error unless the amount is high and impacting the performance for the environment.

SELECT * FROM [OSLCLU001QMSG\MSGBOX].[BizTalkMsgBoxDb].[dbo].[MessageRefCountLogTotals] WHERE [snRefCount] < 0






Storing only a reference to any message on the host queues enables each message to be processed by multiple hosts but be stored only once. Each instance of a particular host will poll its main queue table (for example, the HostAq table in the figure), which contains the message reference. The message content itself will be accessed through the Spool, MessageParts, Parts, and Fragments tables.
When a message is routed only to one subscriber, once it has finished processing a reference will immediately be inserted into the MessageZeroSum table, which is used to mark the physical messages for clean up by a job running within SQL Server Agent. This means that these types of messages will be cleaned up very quickly from the MessageBox database.
 
For messages going to multiple subscribers, once the message finishes processing, the BizTalk service will not remove the message from the database or insert a reference in the MessageZeroSum table, because it does not know whether there are any more subscribers to the message (for example, if it is referenced in another queue). The reference counts (or number of subscribers) for these messages are maintained by a combination of the following tables: MessageRefCountLog1, MessageRefCountLog2, and MessageRefCountLogTotals. The ActiveRefCountLog table is also used as an auxiliary table.
A job running within SQL Server Agent is used to aggregate the reference counts in these tables and determine which messages can be deleted. The Message IDs that can be deleted are then inserted into the MessageZeroSum table, from which another SQL Server Agent job will clean them up.






The solution is simple, all you have to do is run the  Terminator tool and execute the "Repair Ref counts for all messages". This will resolve the issue you have.




Orphaned instances
I saw a few refrencing to orphaned messages, which is something else, orphaned messages are messages that are completed and finished the cycle in BizTalk however the tracking database (BizTalkDTADb) never received the information that this instance finished. This is also resolved by using the  Terminator tool.



