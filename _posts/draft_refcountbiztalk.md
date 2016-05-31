Ref counts
Ref counts show that there are messages in the messagebox without any references, or the other way around. It's not a critical error unless the amount is high and impacting the performance for the environment.

The solution is simple, all you have to do is run the  Terminator tool and execute the "Repair Ref counts for all messages". This will resolve the issue you have.

Orphaned instances
I saw a few refrencing to orphaned messages, which is something else, orphaned messages are messages that are completed and finished the cycle in BizTalk however the tracking database (BizTalkDTADb) never received the information that this instance finished. This is also resolved by using the  Terminator tool.



