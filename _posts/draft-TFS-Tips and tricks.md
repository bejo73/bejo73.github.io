

List checked out files in a WorkSpace

<code>tf status /server:<tfs-server> /u:<user account> /workspace:<name of workspace></code>

List WorkSpaces in TFS

<code>tf workspaces /owner:<user account> /computer:* /server:<tfs-server></code>


Remove checked out files from TFS:
The problem, another user has locked a file for checked






Lista utcheckade filer i ett WorkSpace i TFS
För att lista utcheckade filer i ett WorkSpace i TFS, Team Foundation Server, för en användare så kan man skriva så här på kommandoraden:

tf status /server:<tfs-server> /u:<anv-konto> /workspace:<workspace-namn>

Lista WorkSpaces i TFS
För att lista WorkSpaces i TFS, Team Foundation Server, med kommando så skriver man enligt följande:

tf workspaces /owner:<anv-konto> /computer:* /server:<tfs-server>

Resultat:

Server: TFS-Server-Name...
Ta bort utcheckade filer från TFS
The Problem
Another user has locked a file for checkout, but is no longer available to check the file back in and now you need that file.

Unlocking the file
First you will need to get a list of the workspaces for that user....

Problem med att ta bort eller ändra en mapp i TFS
Ibland kan man hamna i något konstigt läge i TFS, Source Control Explorer. Det är helt omöjligt att ta bort, ändra en mapp (directory). Mappen är dessutom utgråad i vyn. Problemet tycks vara att man lyckats sätta den aktuella mappen till att bli...
