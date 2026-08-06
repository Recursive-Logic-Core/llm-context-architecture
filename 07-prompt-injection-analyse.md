---
title: "Instruktions-Override und Kontext-Kaperei: Systemische Prävention von Prompt-Injection-Schwachstellen bei der Verarbeitung externer Textdaten"
author: "Recursive-Logic-Core"
date: "2026-08-01"
tags: ["ki-architecture", "llm-optimization", "prompt-injection", "security-layers", "methodology"]
status: "Konzeptionelle Architektur"
---

# Instruktions-Override und Kontext-Kaperei: Systemische Prävention von Prompt-Injection-Schwachstellen bei der Verarbeitung externer Textdaten

> **Abstract:** Large Language Models verarbeiten Steuerbefehle und Nutzdaten im selben tokenbasierten Strom. Ohne harte Kanaltrennung können eingeschleuste Textfragmente das Systemverhalten kapern und unautorisierte Aktionen auslösen ("Prompt Injection"). Dieses Dokument skizziert ein konzeptionelles Framework, um Datenströme durch vorgeschaltetes Sandboxing deterministisch zu isolieren.

---

## 1. Das Kernproblem: Die Analogie mit dem Einkaufszettel

Moderne LLMs besitzen standardmäßig keine native physikalische Trennung zwischen Befehlsschicht und reinen Nutzdaten auf Token-Ebene.

Um diese Limitation zu visualisieren:
* Stellen Sie sich vor, die Ehefrau schreibt einen Einkaufszettel. Während eines Telefonats kritzelt sie kurz ihre eigene Erinnerung „16:30 Uhr“ für ihren Friseurtermin auf denselben Zettel.
* Der Mann nimmt den Zettel und interpretiert die Zeit fälschlicherweise als direkten Befehl für seine eigene Aufgabe: Er nimmt das Auto und fährt so los, dass er punkt 16:30 Uhr im Supermarkt steht.
* Die Frau steht ohne Auto da, verpasst ihren Termin, und das Gesamtesystem endet im Fiasko – weil eine fremde Kontextnotiz als operative Handlungsanweisung missverstanden wurde.

Dem System fehlt nicht die Rechenleistung, sondern die strikte Kanaltrennung. Wenn Befehle und unkontrollierte Fremddaten vermischt werden, bricht die deterministische Steuerung sofort zusammen.

---

## 2. Das betriebliche Problem & Die unsichtbare Schranke

* **Das Problem:** Unternehmen verarbeiten ungesicherte externe Textdaten (z. B. Kundendokumente, E-Mails oder Web-Inhalte) direkt in LLM-Pipelines. Eingeschleuste Instruktionen können das Modell dazu bringen, Sicherheitsvorgaben zu umgehen und unkontrollierte Aktionen auszuführen.
* **Die unsichtbare Schranke (Black Box):** Ein System darf niemals rohe, ungeprüfte Fremddaten in die aktive Befehlsschicht einlesen. Die Textdaten müssen zwingend vorab isoliert und bereinigt werden, bevor sie das Modell erreichen.

---

## 3. Die architektonische Anforderung: Konsequente Kanaltrennung

Um Instruktions-Overrides und Prompt Injection vollständig auszuschließen, müssen harte Schnittstellen greifen:

1. **Die Kontroll-Prämisse:** Eine Vermischung von Befehlsschicht und Nutzdaten auf Token-Ebene muss durch externe Systemarchitektur architektonisch unmöglich gemacht werden.
2. **Die Sanierungs-Prüfung:** Vor der Übergabe an die Verarbeitungsschicht erfolgt eine konsequente Kanaltrennung durch vorgeschaltete Datensanierung (Sandboxing) und Bereinigung von Steuerzeichen.
3. **Das Prinzip der menschlichen Endprüfung:** Da automatisierte Filter allein keine absolute Sicherheit garantieren, obliegt die Definition der Sicherheitsgrenzen und der finalen Systemfreigabe ausnahmslos der menschlichen Kontrolle.

---

## Lizenz & Konzept
Dieses konzeptionelle Framework wird für die architektonische Diskussion und Systemanalyse veröffentlicht. Es gelten die im Hauptverzeichnis (README) hinterlegten Lizenzbedingungen der Creative Commons (CC BY-NC-ND 4.0). Jede nicht autorisierte kommerzielle Nutzung oder softwareseitige Implementierung ist untersagt.
