# The problems
Qlik Cloud connector to Jira:
- does not expose the relationship between epics and user story or task.

# The goal
To create two different tables in QS, one for epics and the other for stories and taks. Epics will be a FK at the US table.

# The solution
- Load script SUB stored on a qvs file.
- The SUB will query Jira connection for the epics and create the epics table.
- For each epic, the SUB will query Jira connection to get only US related to the epic. The response will be saved on a US table.
- A last call will be done to identify US or tasks that have no epic association. They will be saved on the US table as well.
- Both tables will be available for further manipulation on the continuing load script.
