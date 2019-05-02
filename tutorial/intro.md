<!-- markdownlint-disable MD002 MD041 -->

Es gibt mehr als 230 out-of-Box-Konnektoren für Microsoft Flow. Viele dieser Connectors verwenden Microsoft Graph für die Kommunikation mit bestimmten Endpunkten von Microsoft-Produkten, aber es gibt keinen Connector, der direkt mit Microsoft Graph kommuniziert, um die gesamte API abzudecken. Es gibt jedoch Szenarien, in denen es möglicherweise erforderlich ist, Microsoft Graph direkt aus dem Fluss mithilfe von grundlegenden Bausteinen des Diensts aufzurufen.

Zusätzlich zu den Adressierungs Szenarien für den direkten Aufruf von Microsoft Graph unterstützt eine Reihe von Microsoft Graph-API-Endpunkten nur [Delegierte Berechtigungen](https://docs.microsoft.com/graph/permissions-reference). Der HTTP-Connector in Microsoft Flow ermöglicht sehr flexible Integrationen, einschließlich Aufrufen von Microsoft Graph. Dem HTTP-Connector fehlt jedoch die Möglichkeit, die Anmeldeinformationen eines Benutzers zwischenzuspeichern, um bestimmte Delegierte Berechtigungs Szenarios zu aktivieren. In diesen Fällen kann ein benutzerdefinierter Konnektor erstellt werden, um einen Wrapper für die Microsoft Graph-API bereitzustellen und die Verwendung der API mit Delegierten Berechtigungen zu ermöglichen.

In diesem Lab werden die beiden obigen Herausforderungen behandelt. Zunächst erstellen Sie einen benutzerdefinierten Konnektor, um die Integration in Microsoft Graph zu ermöglichen, die [Delegierte Berechtigungen](https://docs.microsoft.com/graph/permissions-reference)erfordern. Zweitens verwenden Sie den $Batch- [Anforderungs Endpunkt](https://docs.microsoft.com/graph/json-batching), um den Zugriff auf die volle Leistungsfähigkeit von Microsoft Graph zu ermöglichen, während Sie die Delegierten Berechtigungen verwenden, die erfordern, dass eine APP einen angemeldeten Benutzer anbietet.

> [!NOTE]
> Dies ist ein Lernprogramm zum Erstellen eines benutzerdefinierten Konnektors zur Verwendung in Microsoft Flow und Azure LogicApps. In diesem Tutorial wird davon ausgegangen, dass Sie die [benutzerdefinierte Connector-Übersicht](https://docs.microsoft.com/connectors/custom-connectors/) gelesen haben, um den Prozess zu verstehen

## <a name="prerequisites"></a>Voraussetzungen

Um diese Übung in diesem Beitrag abzuschließen, benötigen Sie Folgendes:

- Administrator Zugriff auf einen Office 365-Mandanten. Wenn Sie noch keine haben, besuchen Sie das [Office 365-Entwicklerprogramm](https://developer.microsoft.com/office/dev-program) , um sich eines kostenlosen Entwickler Mandanten anzumelden.
- Zugriff auf [Microsoft Flow](https://flow.microsoft.com/).

## <a name="feedback"></a>Feedback

Feedback zu diesem Tutorial finden Sie im GitHub- [Repository](https://github.com/microsoftgraph/msgraph-training-microsoftflow).