<!-- markdownlint-disable MD002 MD041 -->

In dieser Übung erstellen Sie einen neuen benutzerdefinierten Connector, der in Flow oder in Azure Logic-Apps verwendet werden kann. Die Open API-Definitionsdatei ist mit dem korrekten Pfad für den Microsoft Graph `$batch` -Endpunkt und zusätzlichen Einstellungen zum Aktivieren des einfachen Imports vordefiniert.

Erstellen Sie mithilfe eines Text-Editors eine neue leere Datei `MSGraph-Delegate-Batch.swagger.json` mit dem Namen, und fügen Sie den folgenden Code hinzu.

[!code-json[](../LabFiles/MSGraph-Delegate-Batch.swagger.json)]

Öffnen Sie einen Browser, und navigieren Sie zu [Microsoft Flow](https://flow.microsoft.com). Melden Sie sich mit Ihrem Office 365 mandantenadministrator Konto an. Wählen Sie das Zahnradsymbol in der oberen rechten Ecke aus, und wählen Sie im Dropdownmenü das Element **benutzerdefinierte Verbinder** aus.

![Ein Screenshot des Dropdownmenüs in Microsoft Flow](./images/flow-conn1.png)

Klicken Sie auf der Seite **benutzerdefinierte Connectors** auf den Link **benutzerdefinierten Verbinder erstellen** in der oberen rechten Ecke, und wählen Sie dann im Dropdownmenü das Element **Open API-Datei importieren** aus.

 ![Ein Screenshot des Dropdownmenüs zum Erstellen eines benutzerdefinierten Connectors in Microsoft Flow](./images/flow-conn2.png)

Geben `MS Graph Batch Connector` Sie in das Textfeld **Name des benutzerdefinierten Connectors** ein. Wählen Sie das Ordnersymbol aus, um die geöffnete API-Datei hochzuladen. Wechseln Sie zu `MSGraph-Delegate-Batch.swagger.json` der Datei, die Sie erstellt haben. Wählen Sie **weiter** aus, um die geöffnete API-Datei hochzuladen.

 ![Ein Screenshot des Dialogfelds "benutzerdefinierten Connector erstellen"](./images/flow-conn3.png)

Klicken Sie auf der Seite Connector-Konfiguration im Navigationsmenü auf den Link **Sicherheit** . Füllen Sie die Felder wie folgt aus.

- **Wählen Sie aus, welche Authentifizierung von ihrer API implementiert wird**:`OAuth 2.0`
- **Identitätsanbieter**:`Azure Active Directory`
- **Client-ID**: die Anwendungs-ID, die Sie in der vorherigen Übung erstellt haben
- **Geheimer Client**Schlüssel: der Schlüssel, den Sie in der vorherigen Übung erstellt haben
- **Anmelde-URL**:`https://login.windows.net`
- **Mandanten-ID**:`common`
- **Ressourcen**-URL `https://graph.microsoft.com` : (kein Trailing/)
- **Bereich**: leer lassen

Wählen Sie in der oberen rechten Ecke **Create Connector** aus.

![Ein Screenshot der Registerkarte "Sicherheit" in der Connector-Konfiguration](./images/flow-conn4.png)

Nachdem der Connector erstellt wurde, kopieren Sie die generierte **Umleitungs-URL**.

![Ein Screenshot der generierten Umleitungs-URL](./images/flow-conn5.png)

Kehren Sie zur registrierten Anwendung im [Azure-Portal](https://aad.portal.azure.com) zurück, das Sie in der vorherigen Übung erstellt haben. Wählen Sie **Antwort-URLs** im Blade **Einstellungen** aus. Fügen Sie die **Umleitungs-URL** ein, die Sie als zusätzliche **Antwort-URL**kopiert haben. Speichern Sie die Anwendung im Azure Active Directory-Portal.

![Ein Screenshot des Blatts "Antwort-URLs" im Azure-Portal](./images/flow-conn6.png)
