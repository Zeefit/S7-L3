L'obiettivo di questo esercizio è sfruttare una macchina vulnerabile, in questo caso Metasploitable, utilizzando il framework Metasploit per ottenere accesso tramite un payload reverse TCP. In seguito, si cercheranno vulnerabilità locali per tentare di ottenere privilegi elevati.
mbiente

selezione del modulo PostgreSQL:

Viene utilizzato il modulo exploit/linux/postgres/postgres_payload per attaccare un server PostgreSQL. Questo modulo permette di bersagliare una sessione esistente o un host remoto (RHOST).
L'utente imposta l'host di destinazione (RHOST) su 192.168.1.231.
Visualizzazione delle opzioni del modulo:

Vengono mostrate le opzioni di configurazione, inclusi il database, la porta (RPORT), e le credenziali predefinite (USERNAME e PASSWORD), che sono postgres.
Il modulo utilizza il payload linux/x86/meterpreter/reverse_tcp, con la porta di ascolto (LPORT) impostata su 4444.
Impostazione dell'indirizzo di ascolto:

L'utente configura l'indirizzo di ascolto (LHOST) su 192.168.1.218.
Esecuzione dell'exploit:

Viene avviata la connessione TCP inversa sulla porta 4444.
L'exploit viene eseguito con successo contro un server PostgreSQL (versione 8.3.1), e il payload viene caricato come un file temporaneo su /tmp.
Una sessione Meterpreter viene aperta, indicando l'accesso ottenuto sul server di destinazione 192.168.1.231

Cambio del modulo:

L'utente passa dal modulo di exploit PostgreSQL al modulo post/multi/recon/local_exploit_suggester, che suggerisce exploit locali basati sulle vulnerabilità del sistema bersaglio.
Visualizzazione delle opzioni del modulo:

L'utente visualizza le opzioni di configurazione del modulo, che richiedono una sessione attiva (SESSION) per funzionare.
Il parametro SHOWDESCRIPTION è facoltativo e serve per mostrare una descrizione dettagliata degli exploit disponibili.
Errore durante l'esecuzione:

L'utente tenta di eseguire il modulo, ma riceve un errore perché non è stata specificata alcuna sessione (SESSION) valida.
Correzione e esecuzione:

L'utente imposta la SESSION su 1, facendo riferimento alla sessione Meterpreter aperta in precedenza.
Il modulo viene eseguito correttamente utilizzando la sessione specificata.

Cambio di Strategia (glibc_ld_audit_dso_load_priv_esc):

Hai scelto un secondo exploit, linux/local/glibc_ld_audit_dso_load_priv_esc, indicato per sfruttare vulnerabilità su file SUID (/bin/ping in questo caso).
Configurato con il payload linux/x64/meterpreter/reverse_tcp, ma il primo tentativo non ha avuto successo.
Hai quindi cambiato payload a linux/x86/meterpreter/reverse_tcp.
Successo:

L'exploit è stato eseguito con successo usando il payload linux/x86/meterpreter/reverse_tcp.
È stata aperta una nuova sessione Meterpreter con privilegi root, confermati con il comando getuid
