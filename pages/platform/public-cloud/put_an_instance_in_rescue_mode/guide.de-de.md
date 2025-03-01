---
title: Umstellen einer Instanz auf den Rescue-Modus
slug: umstellung_einer_instanz_auf_den_rescue-modus
excerpt: Erfahren Sie hier, wie Sie den Rescue-Modus für Ihre Public Cloud Instanz aktivieren
section: Verwaltung im OVHcloud Kundencenter
---

**Letzte Aktualisierung am 04.01.2023**

## Ziel

Ihre Instanz kann unter Umständen nicht mehr zugänglich sein, etwa aufgrund eines verlorenen SSH-Schlüssels oder einer Fehlkonfiguration.
In diesem Fall können Sie Ihre Instanz mithilfe des Rescue-Modus neu konfigurieren oder den Zugang zu Ihren Daten wiederherstellen. 

**Diese Anleitung erklärt, wie Sie Ihre OVHcloud Public Cloud Instanz in den Rescue-Modus setzen und Datenzugriff erhalten.**

## Voraussetzungen

- Sie verfügen über eine [Public Cloud Instanz](https://www.ovhcloud.com/de/public-cloud).
- Sie haben Zugriff auf Ihr [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de).
- Sie haben administrativen Zugriff (Root) auf Ihre Instanz über SSH.

## In der praktischen Anwendung

> [!alert]
>
> Der Rescue-Modus für Metal Instanzen ist derzeit nicht über das OVHcloud Kundencenter verfügbar. Weitere Informationen finden Sie in unserer Anleitung zum [Rescue-Modus für Metal-Instanzen](https://docs.ovh.com/de/public-cloud/metal-instance-rescue-mode/).

### Schritt 1: Rescue-Modus aktivieren

Loggen Sie sich in Ihrem [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de) ein. Klicken Sie oben auf der Seite auf `Public Cloud`{.action} und wählen Sie anschließend Ihr Projekt aus. Klicken Sie im linken Menü auf `Instances`{.action}.

Klicken Sie im Interface für die Instanzen auf `...`{.action} rechts neben der Instanz und wählen Sie `Neustart im Rescue-Modus`{.action}.

![control panel](images/rescue2022.png){.thumbnail}

Sie sehen nun den Dialog "Neustart im Rescue-Modus". Klicken Sie auf die Dropdown-Liste, um die Distribution auszuwählen, die Sie im Rescue-Modus verwenden möchten, und klicken Sie dann auf `Neu starten`{.action}.

![control panel](images/rescue2.png){.thumbnail}

Nach dem Neustart Ihrer Instanz im Rescue-Modus zeigt ein Hinweisfeld die verfügbaren Zugriffsmöglichkeiten an. Ihr temporäres **Passwort für den Rescue-Modus** wird nur in der VNC-Konsole angezeigt. Klicken Sie auf Ihre Instanz in der Tabelle und anschließend auf `VNC-Konsole`{.action}, um es abzurufen.

![control panel](images/rescuedata.png){.thumbnail}


### Schritt 2: Auf Ihre Daten zugreifen

Sobald der Rescue-Modus aktiviert wurde, werden die Daten Ihrer Instanz als zusätzliche Festplatte angehängt. Sie muss noch gemountet werden, indem Sie die folgenden Schritte ausführen.

Stellen Sie zuerst eine SSH-Verbindung zu Ihrer Instanz her. Wenn Sie verbunden sind, überprüfen Sie die verfügbaren Festplatten mit diesem Befehl:

```
root@instance:/home/admin# lsblk

NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
vda 253:0 0 1G 0 Festplatte
└─vda1 253:1 0 1023M 0 Teil /
vdb 253:16 0 10G 0 Festplatte
└─vdb1 253:17 0 10G 0 Teil
```

Als Nächstes mounten Sie die Partition:

```
root@instance:/home/admin# mount /dev/vdb1 /mnt
```

Ihre Daten sind jetzt über den Ordner /mnt abrufbar.

### Schritt 3: Rescue-Modus deaktivieren

Sobald Sie Ihre Maßnahmen beendet haben, können Sie den Rescue-Modus deaktivieren, indem Sie Ihre Instanz in der Instanzenverwaltung neu starten. Klicken Sie dazu auf `...`{.action} und wählen Sie `Rescue-Modus verlassen`{.action}.

![control panel](images/rescueexit2022.png){.thumbnail}

> [!warning]
> Falls die Option `Den Rescue-Modus verlassen`{.action} nicht im Menü angezeigt wird, sobald die Instanz im Rescue-Modus ist, aktualisieren Sie den Tab über die entsprechende Browser-Funktion.
>

### Den Rescue-Modus mit der OpenStack API aktivieren

Sie können den Rescue-Modus auch über die OpenStack API mit dem folgenden Befehl aktivieren:

```
# root@server:~# nova rescue INSTANCE_ID
```

Um den Rescue-Modus zu beenden, verwenden Sie den folgenden Befehl:

```
# root@server:~# nova unrescue INSTANCE_ID
```

## Weiterführende Informationen

Für den Austausch mit unserer User Community gehen Sie auf <https://community.ovh.com/en/>.