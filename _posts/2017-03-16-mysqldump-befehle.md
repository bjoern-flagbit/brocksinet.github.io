---
layout: post
title: mysqldump Befehle / Spickzettel
---
**Datenbank dump als sql erstellen**

	mysqldump -u user_db -p -h host_db  name_db > datenbank_dump_20170316.sql

**Datenbank dump als gzip speichern**

	mysqldump -u user_db -p -h host_db  name_db | gzip -c  > datenbank_dump_20170316.sql.gz

**Datenbank dump von sql einspielen**

	mysql -u user_db -p -h host_db name_db < datenbank_dump_20170316.sql
	
**Datenbank dump von gzip einspielen**

	zcat  datenbank_dump_20170316.sql.gz | mysql -u user_db -p -h host_db name_db	

**Verbindung zu mysql aufbauen ohne Host**

	mysql -u user_db -p name_db

**Verbindung zu mysql aufbauen mit Host**

	mysql -u user_db -p -h host_db name_db