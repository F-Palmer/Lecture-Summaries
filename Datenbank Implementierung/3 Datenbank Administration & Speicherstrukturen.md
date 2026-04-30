## Backupzyklus
1. Full-Backup der kompletten Datenbank (z.B. einmal am Wochenende)
2. Incremental-Backup der Veränderungen seit dem letzten Full oder Incremental backup (z.B. einmal Nachts)
3. Wegschreiben aller commited Transaktionen setzt auf IBCK oder letztem Logfile auf

- Backups nicht auf DB Platten ablegen
- Kreisförmiges Überschreiben der alten Sicherungsdateien (immer die letzten x Full-Backups aufheben)
- Incremental Backups mindestens bis zum nächsten Full-Backup aufheben
- Log Files min bis zum nächsten Incremental-Backup aufheben

## Restore
1. Letzten Full-Backup einspielen
2. Alle Incremental Backups seit letzten Full-Backup einspielen
3. Alle Logfiles seit letztem Incremental Backup einspielen

## Data Dictionary
Enthält:
- Informationen über das Datenbanken Schema
- Roles and Privilages
- usw.

Eigenschaften:
- Read-Only
 - strukturiert in Tabellen und Views
 - Liegt im Hauptspeicher oder Cache
 - Wird bei jedem DDL Statement geändert 

#TODO in Altklausuren schauen ob das ganze Oracle Zeug hier drankommt