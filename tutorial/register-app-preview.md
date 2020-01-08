<!-- markdownlint-disable MD002 MD041 -->

In dieser Übung erstellen Sie eine neue Azure Active Directory-Anwendung, die verwendet wird, um die Delegierten Berechtigungen für den benutzerdefinierten Connector bereitzustellen.

Öffnen Sie einen Browser, und navigieren Sie zu [Azure Active Directory Admin Center](https://aad.portal.azure.com). Klicken Sie im linken Navigationsmenü auf den Link **Azure Active Directory** , und wählen Sie dann den Eintrag **App-Registrierungen** im Abschnitt **Manage** des **Azure Active Directory** Blade aus.

![Ein Screenshot des Azure Active Directory Blade im Azure Active Directory Admin Center](./images/app-reg-preview1.png)

Wählen Sie das **neue Registrierungs** Menüelement oben auf dem Blatt **App-Registrierungen** aus.

![Ein Screenshot des Blatts "App-Registrierungen" im Azure Active Directory Admin Center](./images/app-reg-preview2.png)

Geben `MS Graph Batch App` Sie in das Feld **Name** ein. Wählen Sie im Abschnitt **unterstützte Kontotypen** die Option **Konten in einem beliebigen Organisations Verzeichnis**aus. Lassen Sie den Abschnitt **Umleitungs-URI** leer, und wählen Sie **registrieren**aus.

![Ein Screenshot des Registers eines Anwendungs Blatts im Azure Active Directory Admin Center](./images/app-reg-preview3.png)

Kopieren Sie auf dem Blatt **MS Graph-Batch-App** die **Anwendungs-ID (Client)**. Sie benötigen diese in der nächsten Übung.

![Ein Screenshot der registrierten Anwendungsseite](./images/app-reg-preview4.png)

Wählen Sie den Eintrag **API-Berechtigungen** im Abschnitt **Verwalten** des **MS Graph-Batch-App** -Blades aus. Wählen Sie **Hinzufügen einer Berechtigung** unter **API-Berechtigungen**aus.

![Ein Screenshot des API-Berechtigungs Blatts](./images/app-perms-preview1.png)

Wählen Sie im Blade **API-Berechtigungen anfordern** die Option **Microsoft Graph**und dann **Delegierte Berechtigungen**aus. Suchen Sie `group`nach, und wählen Sie dann die Delegierte Berechtigung **alle Gruppen lesen und schreiben** aus. Klicken Sie unten im Blade auf **Berechtigungen hinzufügen** .

 ![Ein Screenshot des Blades für Anforderungs-API-Berechtigungen](./images/app-perms-preview2.png)

Wählen Sie den Eintrag **Zertifikate und Geheimnisse** im Abschnitt **Verwalten** des **MS Graph-Batch-App** -Blades aus, und wählen Sie dann **neuer geheimer Client Schlüssel**aus. Geben `forever` Sie in die **Beschreibung** ein, und wählen Sie **nie** unter **Expires**aus. Wählen Sie **Hinzufügen** aus.

![Ein Screenshot des Blatts "Zertifikat und Geheimnisse"](./images/app-key-preview1.png)

Kopieren Sie den Schlüsselwert für den neuen Schlüssel. Sie benötigen diese in der nächsten Übung.

![Ein Screenshot des neuen geheimen Client Schlüssels](./images/app-key-preview2.png)

> [!IMPORTANT]
> Dieser Schritt ist wichtig, da auf den Schlüssel nicht zugegriffen werden kann, nachdem Sie dieses Blade geschlossen haben. Speichern Sie diesen Schlüssel in einem Text-Editor zur Verwendung in bevorstehenden Übungen.

Um die Verwaltung zusätzlicher Dienste zu ermöglichen, die über Microsoft Graph zugänglich sind, einschließlich der Teams-Eigenschaften, müssen Sie zusätzliche, geeignete Bereiche auswählen, um die Verwaltung bestimmter Dienste zu ermöglichen. Um beispielsweise unsere Lösung so zu erweitern, dass OneNote-Notizbücher oder Planner-Pläne, Buckets und Aufgaben erstellt werden, müssen Sie die erforderlichen Berechtigungs Bereiche für die entsprechenden APIs hinzufügen.
