## Stored Procedures
Sammlung von wiederkehrenden SQL Anweisungen zusammengefasst in einer Prozedur
Ausführung auf dem DB Server – nicht auf dem Client

```SQL
CREATE PROCEDURE BestellungAufgeben(
    IN kundenID INT,
    IN produktID INT,
    IN menge INT,
    OUT erfolg BOOLEAN
)
BEGIN
    DECLARE lagerbestand INT;

    SELECT bestand INTO lagerbestand
    FROM produkte WHERE id = produktID;

    IF lagerbestand >= menge THEN
        INSERT INTO bestellungen (kunde_id, produkt_id, menge)
        VALUES (kundenID, produktID, menge);

        UPDATE produkte SET bestand = bestand - menge
        WHERE id = produktID;

        SET erfolg = TRUE;
    ELSE
        SET erfolg = FALSE;
    END IF;
END;
```


