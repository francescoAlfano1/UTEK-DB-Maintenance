# UTEK_PULIZIA_LOG – Manutenzione Automatica Database SQL Server Business Cube

Soluzione di manutenzione automatica del database **SQL Server** del gestionale Business Cube per la ditta UTEK.

## 🛠️ Tecnologie
- T-SQL (Stored Procedure SQL Server)
- `sqlcmd`
- Windows Task Scheduler
- File `.bat`

## 📋 Descrizione
Risolve un problema di crescita incontrollata della tabella `actlog`, generata da un elevato volume di tracciature provenienti dal magazzino automatico Modula. Tramite due stored procedure schedulate in sequenza si esegue prima la pulizia delle righe di log e poi lo shrink del database per ricompattare lo spazio su disco.

## ✅ Funzionalità principali
- **RPISP_UtekCleanActLog:** elimina le righe di `actlog` provenienti dal Modula tramite pattern sul campo `al_key`
- **RPISP_UtekCleanActLog2:** esegue lo shrink del database per recuperare spazio su disco
- Esecuzione tramite `sqlcmd` con autenticazione SQL Server
- Schedulazione sequenziale tramite due `.bat` separati e Task Scheduler
- Gestione transazionale con `BEGIN TRANSACTION / ROLLBACK` in caso di errore

## 💡 Punti di forza
- Risoluzione di un problema concreto di performance su database produttivo
- Conoscenza di SQL Server: stored procedure, gestione transazioni, TRY/CATCH, RAISERROR
- Approccio cautelativo: le due operazioni sono separate e distanziate nel tempo per sicurezza

## 🏢 Contesto d'uso
Ambito DBA / manutenzione database — ottimizzazione database SQL Server di Business Cube con integrazione magazzino automatico Modula.

> **Nota:** Business Cube è un gestionale ERP diffuso in ambito manifatturiero italiano.
