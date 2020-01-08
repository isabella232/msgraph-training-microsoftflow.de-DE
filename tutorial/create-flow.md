<!-- markdownlint-disable MD002 MD041 -->

In dieser Übung erstellen Sie einen Fluss für die Verwendung des benutzerdefinierten Konnektors, den Sie in den vorherigen Übungen erstellt haben, um ein Microsoft-Team zu erstellen und zu konfigurieren. Der Fluss verwendet den benutzerdefinierten Connector zum Senden einer POST-Anforderung, um eine Office 365 Unified Group zu erstellen, wird für eine Verzögerung angehalten, während die Gruppenerstellung abgeschlossen wird, und sendet dann eine PUT-Anforderung, um die Gruppe einem Microsoft-Team zuzuordnen.

Am Ende sieht der Fluss ähnlich wie in der folgenden Abbildung aus:

![Ein Screenshot des abgeschlossenen Flusses](./images/flow-team1.png)

Öffnen Sie [Microsoft Flow](https://flow.microsoft.com) in Ihrem Browser, und melden Sie sich mit Ihrem Office 365 mandantenadministrator Konto an. Wählen Sie **meine Flows** in der linken Navigationsleiste aus. Wählen Sie **neu**und dann **sofort--von leer aus**. Geben `Create Team` Sie für den **Flussnamen**ein, und wählen Sie dann unter Wählen Sie aus **, wie dieser Fluss ausgelöst**wird **einen Fluss manuell auslösen** aus. Klicken Sie auf **Erstellen**.

Wählen Sie das **manuelle Auslösen eines Fluss** Elements aus, wählen Sie dann **Eingabe hinzufügen**aus, `Name` wählen Sie **Text** aus, und geben Sie als Titel ein.

![Ein Screenshot des manuellen Triggers eines Fluss Auslösers](./images/flow-team6.png)

Wählen Sie **neuer Schritt** aus `Batch` , und geben Sie das Suchfeld ein. Fügen Sie die **MS Graph Batch Connector** -Aktion hinzu. Wählen Sie die Auslassungspunkte aus, `Batch POST-groups`und benennen Sie diese Aktion um.

Fügen **Sie den folgenden Code in das Feld** Text der Aktion ein.

```json
{
  "requests": [
    {
      "url": "/groups",
      "method": "POST",
      "id": 1,
      "headers": { "Content-Type": "application/json" },
      "body": {
        "description": "REPLACE",
        "displayName": "REPLACE",
        "groupTypes": ["Unified"],
        "mailEnabled": true,
        "mailNickname": "REPLACE",
        "securityEnabled": false
      }
    }
  ]
}
```

Ersetzen Sie `REPLACE` die einzelnen Platzhalter `Name` durch Auswählen des Werts aus dem manuellen Auslöser aus dem Menü **dynamischer Inhalt hinzufügen** .

![Ein Screenshot des Menüs für dynamische Inhalte in Microsoft Flow](./images/flow-team2.png)

Wählen Sie **neuer Schritt**aus, `delay` suchen Sie nach einer **Verzögerungs** Aktion, und konfigurieren Sie Sie für 1 Minute.

Wählen Sie **neuer Schritt** aus `Batch` , und geben Sie das Suchfeld ein. Fügen Sie die **MS Graph Batch Connector** -Aktion hinzu. Wählen Sie die Auslassungspunkte aus, `Batch PUT-team`und benennen Sie diese Aktion um.

Fügen **Sie den folgenden Code in das Feld** Text der Aktion ein.

```json
{
  "requests": [
    {
      "id": 1,
      "url": "/groups/REPLACE/team",
      "method": "PUT",
      "headers": {
        "Content-Type": "application/json"
      },
      "body": {
        "memberSettings": {
          "allowCreateUpdateChannels": true
        },
        "messagingSettings": {
          "allowUserEditMessages": true,
          "allowUserDeleteMessages": true
        },
        "funSettings": {
          "allowGiphy": true,
          "giphyContentRating": "strict"
        }
      }
    }
  ]
}
```

Wählen Sie `REPLACE` den Platzhalter aus, und wählen Sie dann im Bereich dynamischer Inhalt den **Begriff Ausdruck** aus. Fügen Sie die folgende Formel in den **Ausdruck**ein.

```js
body('Batch_POST-groups').responses[0].body.id
```

![Ein Screenshot des Ausdrucks im Bereich "dynamischer Inhalt"](./images/flow-formula.png)

Diese Formel gibt an, dass die Gruppen-ID aus dem Ergebnis der ersten Aktion verwendet werden soll.

![Ein Screenshot des aktualisierten Aktions Texts](./images/flow-team3.png)

Wählen Sie **Speichern**aus, und wählen Sie dann **Test** aus, um den Fluss auszuführen.

> [!TIP]
> Wenn ein Fehler wie `The template validation failed: 'The action(s) 'Batch_POST-groups' referenced by 'inputs' in action 'Batch_2' are not defined in the template'`angezeigt wird, ist der Ausdruck falsch und verweist wahrscheinlich auf eine Fluss Aktion, die nicht gefunden werden kann. Stellen Sie sicher, dass der Name der Aktion, auf die verwiesen wird, genau übereinstimmt.

Wählen Sie das Optionsfeld **Ich werde das Trigger** -Aktion ausführen aus, und wählen Sie **#a0 Test speichern**aus. Wählen Sie im Dialogfeld **weiter** aus. Geben Sie einen Namen ohne Leerzeichen ein, und wählen Sie **Lauf Fluss** aus, um ein Team zu erstellen.

![Ein Screenshot des Dialogfelds "Ablaufsteuerung"](./images/flow-team4.png)

Klicken Sie abschließend auf **Fertig** , um das Aktivitätsprotokoll anzuzeigen. Nachdem der Fluss abgeschlossen ist, wurden Ihre Office 365 Gruppe und Ihr Team konfiguriert. Wählen Sie die Batch Aktionselemente aus, um die Ergebnisse der JSON-Batch Aufrufe anzuzeigen. Die `outputs` der `Batch PUT-team` Aktion sollte den Statuscode 201 für eine erfolgreiche Team Zuordnung ähnlich wie in der Abbildung unten haben.

![Ein Screenshot des erfolgreichen Ablauf Aktivitätsprotokolls](./images/flow-team5.png)
