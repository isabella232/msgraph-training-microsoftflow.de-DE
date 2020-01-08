<!-- markdownlint-disable MD002 MD041 -->

Der in der vorherigen Übung erstellte Fluss verwendet die `$batch` API, um zwei einzelne Anforderungen an Microsoft Graph zu stellen. Das Aufrufen `$batch` des Endpunkts auf diese Weise bietet einige Vorteile und Flexibilität, aber die `$batch` wahre Leistung des Endpunkts wird bei der Ausführung mehrerer Anforderungen `$batch` an Microsoft Graph in einem einzigen Aufruf erfüllt. In dieser Übung erweitern Sie das Beispiel zum Erstellen einer einheitlichen Gruppe und zum Verknüpfen eines Teams mit dem Erstellen mehrerer Standardkanäle für das Team in einer einzigen `$batch` Anforderung.

Öffnen Sie [Microsoft Flow](https://flow.microsoft.com) in Ihrem Browser, und melden Sie sich mit Ihrem Office 365 mandantenadministrator Konto an. Wählen Sie den Fluss aus, den Sie im vorherigen Schritt erstellt haben, und klicken Sie dann auf **Bearbeiten**.

Wählen Sie **neuer Schritt** aus `Batch` , und geben Sie das Suchfeld ein. Fügen Sie die **MS Graph Batch Connector** -Aktion hinzu. Wählen Sie die Auslassungspunkte aus, `Batch POST-channels`und benennen Sie diese Aktion um.

Fügen **Sie den folgenden Code in das Feld** Text der Aktion ein.

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

Beachten Sie, dass die drei obigen Anforderungen die [dependsOn](https://docs.microsoft.com/graph/json-batching#sequencing-requests-with-the-dependson-property) -Eigenschaft verwenden, um eine Sequenzreihenfolge anzugeben, und jeder wird eine Post-Anforderung ausführen, um einen neuen Kanal im neuen Team zu erstellen.

Wählen Sie jede Instanz des `REPLACE` Platzhalters aus, und wählen Sie dann im Bereich dynamischer Inhalt den **Begriff Ausdruck** aus. Fügen Sie die folgende Formel in den **Ausdruck**ein.

```js
body('Batch_PUT-team').responses[0].body.id
```

![Ein Screenshot des Ausdrucks im Bereich "dynamischer Inhalt"](./images/flow-channel1.png)

Wählen Sie **Speichern**aus, und wählen Sie dann **Test** aus, um den Fluss auszuführen. Aktivieren Sie das Optionsfeld **Ich werde das Auslösen der Aktion ausführen** , und wählen Sie dann **#a0 Test speichern**aus. Geben Sie einen eindeutigen Gruppennamen in das Feld **Name** ohne Leerzeichen ein, und wählen Sie **Run Flow** aus, um den Fluss auszuführen.

Nachdem der Fluss gestartet wurde, klicken Sie auf die Schaltfläche **Fertig** , um das Aktivitätsprotokoll anzuzeigen. Wenn der Fluss abgeschlossen ist, hat die endgültige Ausgabe `Batch POST-channels` für die Aktion eine 201-HTTP-Status Antwort für jeden erstellten Kanal.

![Ein Screenshot des erfolgreichen Ablauf Aktivitätsprotokolls](./images/flow-channel2.png)

Wechseln Sie zu [Microsoft Teams](https://teams.microsoft.com) , und melden Sie sich mit Ihrem Office 365 mandantenadministrator Konto an. Stellen Sie sicher, dass das soeben erstellte Team angezeigt wird und die drei von der `$batch` Anforderung erstellten Kanäle enthält.

![Ein Screenshot der Teams-App mit dem neuen Team und den Kanälen, die angezeigt werden](./images/team-channels.png)

Während die obige `Batch POST-channels` Aktion in diesem Lernprogramm als separate Aktion implementiert wurde, konnten die Aufrufe zum Erstellen der Kanäle als zusätzliche Aufrufe in der `Batch PUT-team` Aktion hinzugefügt werden. Dadurch hätte das Team und alle Kanäle in einem einzigen Batch Aufruf erstellt. Geben Sie dies auf eigene Faust.

Denken Sie schließlich daran, dass [JSON-Batch](https://docs.microsoft.com/graph/json-batching) Aufrufe einen HTTP-Statuscode für jede Anforderung zurückgeben. In einem Produktionsprozess empfiehlt es sich, die Nachbearbeitung der Ergebnisse mit einer [`Apply to each`](https://docs.microsoft.com/flow/apply-to-each) Aktion zu kombinieren und jede einzelne Antwort mit einem 201-Statuscode zu validieren oder andere erhaltene Statuscodes zu kompensieren.
