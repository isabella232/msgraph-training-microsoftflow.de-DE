<!-- markdownlint-disable MD002 MD041 -->

In dieser Übung erstellen Sie eine neue Azure Active Directory-Anwendung, die verwendet wird, um die Delegierten Berechtigungen für den benutzerdefinierten Connector bereitzustellen.

Öffnen Sie einen Browser, und navigieren Sie zu [Azure Active Directory Admin Center](https://aad.portal.azure.com). Klicken Sie im linken Navigationsmenü auf den Link **Azure Active Directory** , und wählen Sie dann den Eintrag **App-Registrierungen** im Abschnitt **Manage** des **Azure Active Directory** Blade aus.

![Ein Screenshot des Azure Active Directory Blade im Azure Active Directory Admin Center](./images/app-reg1.png)

Klicken Sie auf das Menüelement **neue Anwendungsregistrierung** oben auf dem Blatt **App-Registrierungen** .

![Ein Screenshot des Blatts "App-Registrierungen" im Azure Active Directory Admin Center](./images/app-reg2.png)

Geben `MS Graph Batch App` Sie in das Feld **Name** und `https://localhost.com/$batch` in das Feld **Anmelde-URL** ein, und wählen Sie **Erstellen**aus.

![Ein Screenshot des Formulars zum Erstellen einer neuen App-Registrierung im Azure Active Directory Admin Center](./images/app-reg3.png)

Kopieren Sie auf der Seite **MS Graph Batch-App** die **Anwendungs-ID** der Anwendung. Sie benötigen diese in der nächsten Übung.

![Ein Screenshot der registrierten Anwendungsseite](./images/app-reg4.png)

Wählen Sie unter dem Anwendungsnamen das Zahnrad **Einstellungen** aus, und wählen Sie dann im Blade Einstellungen das Menüelement **erforderliche Berechtigungen** aus. Wählen Sie oben auf dem Blade **erforderliche Berechtigungen** die Option **Hinzufügen** aus.

![Ein Screenshot des Blades für erforderliche Berechtigungen](./images/app-perms1.png)

Wählen Sie die Option **API auswählen** im Blatt **API-Zugriff hinzufügen** aus, und wählen Sie dann das Element **Microsoft Graph** aus, und wählen **Sie** am unteren Rand des Blades auswählen aus.

![Ein Screenshot des API-Blades auswählen](./images/app-perms2.png)

Scrollen Sie auf dem Blade **Zugriffs Blatt aktivieren** zum Abschnitt **Delegierte Berechtigungen** . Wählen Sie die Berechtigung **alle Gruppen delegieren lesen und schreiben** aus, und wählen Sie dann am unteren Rand des Blades **auswählen** aus. Wählen Sie am unteren Rand des **Add API Access-** Blades **Fertig** .

 ![Ein Screenshot des Zugriffs Blatts aktivieren](./images/app-perms3.png)

Klicken Sie auf dem Blade **Einstellungen** auf das Menü **Schlüssel** . Geben `forever` Sie in die **Schlüssel Beschreibung** ein, und wählen Sie **nie ablaufen** im Dropdownmenü **Dauer** aus. Wählen Sie oben im Blatt **Schlüssel** die Option **Speichern** aus. Kopieren Sie den Schlüsselwert für den neuen Schlüssel. Sie benötigen diese in der nächsten Übung.

![Ein Screenshot des Tasten Blatts](./images/app-key1.png)

> [!IMPORTANT]
> Dieser Schritt ist wichtig, da auf den Schlüssel nicht zugegriffen werden kann, nachdem Sie dieses Blade geschlossen haben. Speichern Sie diesen Schlüssel in einem Text-Editor zur Verwendung in bevorstehenden Übungen.

Um die Verwaltung zusätzlicher Dienste zu ermöglichen, die über Microsoft Graph zugänglich sind, einschließlich der Teams-Eigenschaften, müssen Sie zusätzliche, geeignete Bereiche auswählen, um die Verwaltung bestimmter Dienste zu ermöglichen. Um beispielsweise unsere Lösung so zu erweitern, dass OneNote-Notizbücher oder Planner-Pläne, Buckets und Aufgaben erstellt werden, müssen Sie die erforderlichen Berechtigungs Bereiche für die entsprechenden APIs hinzufügen.
