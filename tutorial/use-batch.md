<!-- markdownlint-disable MD002 MD041 -->

Der in der vorherigen Übung erstellte Fluss verwendet die `$batch` API, um zwei einzelne Anforderungen an Microsoft Graph zu stellen. Das Aufrufen `$batch` des Endpunkts auf diese Weise bietet einige Vorteile und Flexibilität, aber die `$batch` wahre Leistungsfähigkeit des Endpunkts kommt beim Ausführen mehrerer Anforderungen `$batch` an Microsoft Graph in einem einzelnen Aufruf. In dieser Übung erweitern Sie das Beispiel für das Erstellen einer einheitlichen Gruppe und das Zuordnen eines Teams zum Erstellen mehrerer Standardkanäle für das Team in einer einzigen `$batch` Anforderung.

Öffnen Sie [Microsoft Flow](https://flow.microsoft.com) in Ihrem Browser, und melden Sie sich mit Ihrem Office 365-mandantenadministrator Konto an. Wählen Sie den Flow aus, den Sie im vorherigen Schritt erstellt haben, und klicken Sie auf **Bearbeiten**.

Wählen Sie **neuer Schritt** aus `Batch` , und geben Sie in das Suchfeld ein. Fügen Sie die Batch-Konnektor-Aktion **MS Graph** hinzu. Wählen Sie die Auslassungspunkte aus, `Batch POST-channels`und benennen Sie diese Aktion in um.

Fügen Sie den folgenden Code in **** das Textfeld Text der Aktion ein.

```json
{
  "requests": [
    {
      "id": 1,
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "Marketing Collateral",
        "description": "Marketing collateral and documentation."
      }
    },
    {
      "id": 2,
      "dependsOn": [
        "1"
      ],
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "Vendor Contracts",
        "description": "Vendor documents, contracts, agreements and schedules."
      }
    },
    {
      "id": 3,
      "dependsOn": [
        "2"
      ],
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "General Client Agreements",
        "description": "General Client documents and agreements."
      }
    }
  ]
}
```

Beachten Sie, dass die drei obigen Anforderungen die [dependsOn](https://docs.microsoft.com/graph/json-batching#sequencing-requests-with-the-dependson-property) -Eigenschaft verwenden, um eine Sequenzreihenfolge anzugeben, und jede eine Post-Anforderung ausführt, um einen neuen Kanal im neuen Team zu erstellen.

Wählen Sie die `REPLACE` einzelnen Instanzen des Platzhalters aus, und wählen Sie dann im dynamischen Inhaltsbereich **Ausdruck** aus. Fügen Sie die folgende Formel in den **Ausdruck**ein.

```js
body('Batch_PUT-team').responses[0].body.id
```

![Ein Screenshot des Ausdrucks im dynamischen Inhaltsbereich](./images/flow-channel1.png)

Klicken Sie auf **Speichern**, und wählen Sie dann **Testen** aus, um den Fluss auszuführen. Aktivieren Sie das Optionsfeld **Ich werde den Auslöser ausführen** , und wählen Sie dann **& Test speichern**aus. Geben Sie im Feld **Name** einen eindeutigen Gruppennamen ohne Leerzeichen ein, und wählen Sie **Flow ausführen** aus, um den Fluss auszuführen.

![Screenshot des Dialogfelds "Run Flow"](./images/flow-channel3.png)

Nachdem der Fluss gestartet wurde, wählen Sie den Link **Fluss Laufaktivität anzeigen** aus, und wählen Sie dann den ausgeführten Fluss aus, um das Aktivitätsprotokoll anzuzeigen.

Nach Abschluss des Flusses hat die endgültige Ausgabe für die `Batch POST-channels` Aktion eine 201 HTTP-Status Antwort für jeden erstellten Kanal.

![Ein Screenshot des erfolgreichen Ablauf Aktivitätsprotokolls](./images/flow-channel2.png)

Wechseln Sie zu [Microsoft Teams](https://teams.microsoft.com) , und melden Sie sich mit Ihrem Office 365-mandantenadministrator Konto an. Stellen Sie sicher, dass das soeben erstellte Team angezeigt wird und die drei von der `$batch` Anforderung erstellten Kanäle enthält.

![Ein Screenshot der Teams-App mit dem neuen Team und den Kanälen](./images/team-channels.png)

Während die obige `Batch POST-channels` Aktion in diesem Lernprogramm als separate Aktion implementiert wurde, konnten die Aufrufe zum Erstellen der Kanäle als zusätzliche Aufrufe in der `Batch PUT-team` Aktion hinzugefügt worden sein. Dies hätte das Team und alle Kanäle in einem einzigen Batch Aufruf erstellt. Probieren Sie es selbst aus.

Denken Sie daran, dass [JSON-Batch](https://docs.microsoft.com/graph/json-batching) Aufrufe einen HTTP-Statuscode für jede Anforderung zurückgeben. In einem Produktionsprozess kann es sinnvoll sein, die Nachbearbeitung der Ergebnisse mit einer [`Apply to each`](https://docs.microsoft.com/flow/apply-to-each) Aktion zu kombinieren und jede einzelne Antwort mit einem 201-Statuscode zu validieren oder andere Statuscodes zu kompensieren.