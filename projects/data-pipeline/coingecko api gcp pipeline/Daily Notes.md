### **What I worked on today June 25, 2025**

- Updated Python Script to include all data from the coin/marketlist api call. Included 100 rows of coins now instead of 10. Not sure if this is all or a limitation from using the demo api.
- Created Bronze Table in Snowflake.
- ![[Pasted image 20250625165151.png]]
- Copied Parquet file data from crypto-raw/bronze bucket into new table.
- ![[Pasted image 20250625165259.png]] 
### **Improvements to make**

- Clean up python script. Including formatting, commenting, and removing any redundant or unnecessary code.
- Improve workflow for kanban board. There is a plugin in obsidian so maybe could integrate that with git plugin to track everything in github. To remove the need for Notion.

### **Next Steps**

- Create Silver layer Table in Snowflake (silver ddl).
- Decide what transformations we need to make for data.
- Perform transformations on the data.
- Create some more architecture of the flow of data 