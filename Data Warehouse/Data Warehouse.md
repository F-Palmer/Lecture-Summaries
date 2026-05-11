ETL: 
die Daten **vor** dem Laden ins Warehouse transformiert

ELT: 
ELT landen die Rohdaten **zuerst** im Warehouse, die Transformation erfolgt dort mit der nativen Rechenleistung

Data Federation:
- multiple DMBS can be exposed as one DBMS 
- only has Meta Data, eg. table definitions
- Only use in small usecases
![[Pasted image 20260509155928.png|]]

Data Structure: 
structured: table 
sem-structured: JSON
un-structured: free text

Pull vs Push: 
pull: target (=DW) initiates the data transfer
push: source initiates the data transfer

Delta Loads: 
- initial data load 
- only changes and additions are loaded
with timestamps
- transaction time is part of the table
appends 
- System never changes or deletes rows, it only appends them

| ID  | Value | updated_at                                     |
| --- | ----- | ---------------------------------------------- |
| 1   | 100   | 2026-05-01   ← original                        |
| 1   | 150   | 2026-05-08   ← "update" = new row with same ID |

or change data capture (CDC)
Automatically detect changes in the source system and update the DW accordingly
Possible with triggers
![[Pasted image 20260509162604.png]]

![[Pasted image 20260509162705.png]]

A star schema is a way to organise (model) tables in a data warehouse so that the data can be
analysed and with good performance.
Typically: 1 fact table + various dimension tables

Dimension tables describe the business entities of an enterprise, which usually
represent hierarchical, categorical information such as time, departments, locations,
and products. Dimension tables are sometimes called lookup or reference tables

Fact-tables are normalised
dimension tables are largely de-normalised