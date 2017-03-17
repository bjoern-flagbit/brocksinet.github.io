---
layout: post
title: Git Befehle / Spickzettel
---
**Neuen Branch erstellen und wechseln**

	git checkout -b TASK-123

**Branch wechseln**

	git checkout branchname

**Commit mit Kommentar hinzufügen**

	git commit -m '[Task-123] Kommentar ...'

**Git merge (vorher Checkout master)**

	git merge --no-ff Task-123

**Branch pushen**

	git push origin Task-123

**Zeige welche Dateien in dem Branch zum Master verändert wurden**

	git diff --name-status maser Task-123

**Git Head zurücksetzen**

	git reset --hard HEAD

**Git Remote Branch löschen**

	git push origin :BRANCH-123

**Git Local Branch löschen**

	git branch -d BRANCH-123

**oder**

	git branch -D BRANCH-123

**Git Cherry Pick**

	git cherry-pick COMMIT-NUMMER

**Git GET all remote branches**

	for remote in `git branch -r `; do git branch --track $remote; done

**Git UPDATE all remote branches**

	for remote in `git branch -r `; do git checkout $remote ; git pull; done