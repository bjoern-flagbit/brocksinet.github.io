---
layout: post
title: Docker Befehle / Spickzettel
---
**Zeige alle Docker-Images**

	docker ps -a
	
**Baue oder aktualisiere deine Docker-Images**

	docker-compose build
	
**Starte deine Docker-Images**

	docker-compose up -d
		
**Stope deien Docker-Images**

	docker-compose stop
	
**Zeige Logs zu einem Docker-Image**

	docker logs docker_image_name		

**Verbinde dich per bash zu einem Docker-Image**

	docker exec -it docker_image_name bash
	
**Verbinde dich per bash zu einem Docker-Image als bestimmter User**

	docker exec -u www-data -it docker_image_name bash	

**Kopiere eine Datei von local zu deinem Docker-Image**

	docker cp src/datei_kopieren.zip docker_image_name:/ziel_pfad

**Kopiere eine Datei von deinem Docker-Image nach local**

	docker cp docker_image_name:/pfad_zur_datei/test.txt /local_pfad/ 
	
**Befehl in Docker-Image ausführen ohne auf das Image zu gehen**

    docker exec -u www-data docker_image_name bash -c 'cd /var/www/magento/src && ./bin/magento setup:static-content:deploy de_DE'

**IP-Adresse eines Docker-Images herausfinden**

    docker inspecht docker_image_name