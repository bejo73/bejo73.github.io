

List checked out files in a WorkSpace

<code>tf status /server:<tfs-server> /u:<user account> /workspace:<name of workspace></code>

Lista utcheckade filer i ett WorkSpace i TFS
För att lista utcheckade filer i ett WorkSpace i TFS, Team Foundation Server, för en användare så kan man skriva så här på kommandoraden:

tf status /server:<tfs-server> /u:<anv-konto> /workspace:<workspace-namn>




List WorkSpaces in TFS

<code>tf workspaces /owner:<user account> /computer:* /server:<tfs-server></code>


Remove checked out files from TFS:
The problem, another user has locked a file for checked

Lista WorkSpaces i TFS
För att lista WorkSpaces i TFS, Team Foundation Server, med kommando så skriver man enligt följande:

tf workspaces /owner:<anv-konto> /computer:* /server:<tfs-server>

Resultat:

Server: TFS-Server-Name
Workspace       Owner      Computer        Comment
--------------- ---------- --------------- ----------------------------------------
VPCSRV000       user1      VPCSRV000
WIN-7DFJU2OP4QK user1      WIN-7DFJU2OP4QK







Ta bort utcheckade filer från TFS
The Problem
Another user has locked a file for checkout, but is no longer available to check the file back in and now you need that file.

Unlocking the file
First you will need to get a list of the workspaces for that user. This can be done with administrative rights from the command line as follows:

tf workspaces /owner:DOMAIN\TheirUserAccount /computer:*

The command will retrieve a list of all workspaces on all computers for that user.
You can now use the output information to undo the checkouts on the files you want:

tf undo /workspace:TheirWorkspace;DOMAIN\TheirUserAccount $/path/to/file

In the event the developer is no longer with the company or on the project, you can also delete the workspace which will also undo any pending changes using the following command:

tf workspace /delete TheirWorkspace;DOMAIN\TheirUserAccount /s:http://TFSSERVER:8080
tf undo [/workspace:workspacename[;workspaceowner]] [/server:servername] [/recursive] itemspec [/noprompt]

I was also faced with having to add my login info, so the exact command I used was as follows:

tf undo /workspace:WORKSPACE-NAME;User $/myProject/CheckedOutFile.cs /login:myusername,mypassword

I also found out that you can delete an entire workspace for a developer who is no longer on your project and maybe had some files checked out. That command is even easier, and will automatically undo any checkouts:

tf workspace /delete Workspace (add "/login:name,password" to end of command if not using AD)

Undo checkout av alla filer/dirs under en angiven sökväg i ett workspace:

tf undo /server: /workspace:WIN-7DFJU0OP9QK; $"" /recursive






Lista WorkSpaces i TFS
För att lista WorkSpaces i TFS, Team Foundation Server, med kommando så skriver man enligt följande:

tf workspaces /owner:<anv-konto> /computer:* /server:<tfs-server>

Resultat:

Server: TFS-Server-Name
Workspace       Owner      Computer        Comment
--------------- ---------- --------------- ----------------------------------------
VPCSRV000       user1      VPCSRV000
WIN-7DFJU2OP4QK user1      WIN-7DFJU2OP4QK




Problem med att ta bort eller ändra en mapp i TFS
Ibland kan man hamna i något konstigt läge i TFS, Source Control Explorer. Det är helt omöjligt att ta bort, ändra en mapp (directory). Mappen är dessutom utgråad i vyn. Problemet tycks vara att man lyckats sätta den aktuella mappen till att bli ett aktivt Workspace.

För att lösa problemet så får man i Visual Studio gå in under File/Source Control/Workspaces... och ta bort den aktuella mappen.

