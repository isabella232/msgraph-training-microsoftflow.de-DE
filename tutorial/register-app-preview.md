<!-- markdownlint-disable MD002 MD041 -->

In dieser Übung erstellen Sie eine neue Azure Active Directory-Anwendung, die zum Bereitstellen der Delegierten Berechtigungen für den benutzerdefinierten Connector verwendet wird.

Öffnen Sie einen Browser, und navigieren Sie zu [Azure Active Directory Admin Center](https://aad.portal.azure.com). Klicken Sie im linken Navigationsmenü auf den Link **Azure Active Directory** , und wählen Sie dann im Abschnitt **Verwalten** des **Azure Active Directory** -Blades den Eintrag **App Registrations** aus.

![Ein Screenshot des Azure Active Directory-Blades im Azure Active Directory Admin Center](./images/app-reg-preview1.png)

Wählen Sie das Menüelement **neue Registrierung** oben auf dem Blatt **App** -Registrierungen aus.

![Ein Screenshot des Blades "App-Registrierungen" im Azure Active Directory Admin Center](./images/app-reg-preview2.png)

Geben `MS Graph Batch App` Sie in das Feld **Name** ein. Wählen Sie im Abschnitt **unterstützte Kontotypen** **Konten in einem beliebigen Organisations Verzeichnis**aus. Lassen Sie den Abschnitt Umleitungs- **URI** leer, und wählen Sie **registrieren**.

![Screenshot des Registers "Application Blade" im Azure Active Directory Admin Center](./images/app-reg-preview3.png)

Kopieren Sie auf dem Blade- **Batch-APP von MS Graph** die **Anwendungs-ID (Client)**. Sie benötigen dies in der nächsten Übung.

![Screenshot der registrierten Anwendungsseite](./images/app-reg-preview4.png)

Wählen Sie den Eintrag **API-Berechtigungen** im Abschnitt **Verwalten** des Batch-App-Blatts **MS Graph** aus. Wählen Sie **Berechtigung hinzufügen** unter **API-Berechtigungen**aus.

![Screenshot des API-Berechtigungs Blatts](./images/app-perms-preview1.png)

Klicken Sie im Blatt **API-Berechtigungen anfordern** auf **Microsoft Graph**, und wählen Sie dann **Delegierte Berechtigungen**aus. Suchen `group`, und wählen Sie dann die Berechtigung **alle Gruppen mit Berechtigungen Lesen und schreiben** aus. Wählen Sie am unteren Rand des Blades **Berechtigungen hinzufügen** aus.

 ![Screenshot des Zugriffs Blatts für Anforderungs-API-Berechtigungen](./images/app-perms-preview2.png)

Wählen Sie den Eintrag **Zertifikate und** geheimen im Abschnitt **Verwalten** des Batch-App-Blatts **MS Graph** aus, und wählen Sie dann **neuer Client Schlüssel**aus. Geben `forever` Sie in die **Beschreibung** ein, und wählen Sie **nie** unter **Expires**aus. Wählen Sie **Hinzufügen** aus.

![Ein Screenshot des "Certificate and Secrets"-Blatts](./images/app-key-preview1.png)

Kopieren Sie den Schlüsselwert für den neuen Schlüssel. Sie benötigen dies in der nächsten Übung.

![Screenshot des neuen geheimen Clients](./images/app-key-preview2.png)

> [!IMPORTANT]
> Dieser Schritt ist wichtig, da der Schlüssel nicht zugegriffen werden kann, nachdem Sie dieses Blade geschlossen haben. Speichern Sie diesen Schlüssel in einem Text-Editor für die nächsten Übungen.

Um die Verwaltung zusätzlicher Dienste, auf die über Microsoft Graph zugegriffen werden kann, einschließlich der Teams-Eigenschaften, zu ermöglichen, müssen Sie zusätzliche, geeignete Bereiche auswählen, um die Verwaltung bestimmter Dienste zu ermöglichen. Wenn Sie beispielsweise unsere Lösung erweitern möchten, um die Erstellung von OneNote-Notizbüchern oder Plan Plänen, Buckets und Aufgaben zu ermöglichen, müssen Sie die erforderlichen Berechtigungs Bereiche für die relevanten APIs hinzufügen.