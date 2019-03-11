<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="26df8-101">In dieser Übung erstellen Sie einen neuen benutzerdefinierten Connector, der in Flow oder in Azure Logic-Apps verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="26df8-101">In this exercise, you will create a new custom connector which can be used in Flow or in Azure Logic Apps.</span></span> <span data-ttu-id="26df8-102">Die Definitionsdatei für die Open-API ist mit dem korrekten Pfad für den `$batch` Microsoft Graph-Endpunkt und zusätzlichen Einstellungen für den einfachen Import vordefiniert.</span><span class="sxs-lookup"><span data-stu-id="26df8-102">The Open API definition file is prebuilt with the correct path for the Microsoft Graph `$batch` endpoint and additional settings to enable simple import.</span></span>

<span data-ttu-id="26df8-103">Erstellen Sie mit einem Text-Editor eine neue leere Datei `MSGraph-Delegate-Batch.swagger.json` mit dem Namen, und fügen Sie den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="26df8-103">Using a text editor, create a new empty file named `MSGraph-Delegate-Batch.swagger.json` and add the following code.</span></span>

[!code-json[](../LabFiles/MSGraph-Delegate-Batch.swagger.json)]

<span data-ttu-id="26df8-104">Öffnen Sie einen Browser, und navigieren Sie zu [Microsoft Flow](https://flow.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="26df8-104">Open a browser and navigate to [Microsoft Flow](https://flow.microsoft.com).</span></span> <span data-ttu-id="26df8-105">Melden Sie sich mit Ihrem Office 365-mandantenadministrator Konto an.</span><span class="sxs-lookup"><span data-stu-id="26df8-105">Sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="26df8-106">Klicken Sie oben rechts auf das Zahnradsymbol, und wählen Sie im Dropdownmenü das Element **benutzerdefinierte Verbinder** aus.</span><span class="sxs-lookup"><span data-stu-id="26df8-106">Choose the gear icon in the upper right, and select the **Custom Connectors** item in the drop-down menu.</span></span>

![Screenshot des Dropdownmenüs in Microsoft Flow](./images/flow-conn1.png)

<span data-ttu-id="26df8-108">Wählen Sie auf der Seite **benutzerdefinierte Connectors** den Link **benutzerdefinierten Verbinder erstellen** oben rechts aus, und wählen Sie dann im Dropdownmenü das Element **eine geöffnete API-Datei importieren** aus.</span><span class="sxs-lookup"><span data-stu-id="26df8-108">On the **Custom Connectors** page choose the **Create custom connector** link in the top right, then select the **Import an Open API file** item in the drop-down menu.</span></span>

 ![Ein Screenshot des Dropdownmenüs benutzerdefinierte Verbindung erstellen in Microsoft Flow](./images/flow-conn2.png)

<span data-ttu-id="26df8-110">Geben `MS Graph Batch Connector` Sie in das Textfeld **benutzerdefiniertEr Connectorname** ein.</span><span class="sxs-lookup"><span data-stu-id="26df8-110">Enter `MS Graph Batch Connector` in the **Custom connector name** text box.</span></span> <span data-ttu-id="26df8-111">Klicken Sie auf das Ordnersymbol, um die geöffnete API-Datei hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="26df8-111">Choose the folder icon to upload the Open API file.</span></span> <span data-ttu-id="26df8-112">Navigieren Sie zu `MSGraph-Delegate-Batch.swagger.json` der Datei, die Sie erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="26df8-112">Browse to the `MSGraph-Delegate-Batch.swagger.json` file you created.</span></span> <span data-ttu-id="26df8-113">Wählen Sie **weiter** , um die offene API-Datei hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="26df8-113">Choose **Continue** to upload the Open API file.</span></span>

 ![Screenshot des Dialogfelds "benutzerdefinierten Connector erstellen"](./images/flow-conn3.png)

<span data-ttu-id="26df8-115">Klicken Sie auf der Seite Connector-Konfiguration im Navigationsmenü auf den Link **Sicherheit** .</span><span class="sxs-lookup"><span data-stu-id="26df8-115">On the connector configuration page, choose the **Security** link in the navigation menu.</span></span> <span data-ttu-id="26df8-116">Füllen Sie die Felder wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="26df8-116">Fill in the fields as follows.</span></span>

- <span data-ttu-id="26df8-117">**Wählen Sie aus, welche Authentifizierung von ihrer API implementiert wird**:`OAuth 2.0`</span><span class="sxs-lookup"><span data-stu-id="26df8-117">**Choose what authentication is implemented by your API**: `OAuth 2.0`</span></span>
- <span data-ttu-id="26df8-118">**Identitätsanbieter**:`Azure Active Directory`</span><span class="sxs-lookup"><span data-stu-id="26df8-118">**Identity Provider**: `Azure Active Directory`</span></span>
- <span data-ttu-id="26df8-119">**Client-ID**: die Anwendungs-ID, die Sie in der vorherigen Übung erstellt haben</span><span class="sxs-lookup"><span data-stu-id="26df8-119">**Client id**: the application ID you created in the previous exercise</span></span>
- <span data-ttu-id="26df8-120">**GeheimEr Client**Schlüssel: die Taste, die Sie in der vorherigen Übung erstellt haben</span><span class="sxs-lookup"><span data-stu-id="26df8-120">**Client secret**: the key you created in the previous exercise</span></span>
- <span data-ttu-id="26df8-121">**Anmelde-URL**:`https://login.windows.net`</span><span class="sxs-lookup"><span data-stu-id="26df8-121">**Login url**: `https://login.windows.net`</span></span>
- <span data-ttu-id="26df8-122">**MandantEN-ID**:`common`</span><span class="sxs-lookup"><span data-stu-id="26df8-122">**Tenant ID**: `common`</span></span>
- <span data-ttu-id="26df8-123">**Ressourcen**-URL `https://graph.microsoft.com` : (keine Nachverfolgung/)</span><span class="sxs-lookup"><span data-stu-id="26df8-123">**Resource URL**: `https://graph.microsoft.com` (no trailing /)</span></span>
- <span data-ttu-id="26df8-124">**Bereich**: leer lassen</span><span class="sxs-lookup"><span data-stu-id="26df8-124">**Scope**: Leave blank</span></span>

<span data-ttu-id="26df8-125">Klicken Sie oben rechts auf **Verbinder erstellen** .</span><span class="sxs-lookup"><span data-stu-id="26df8-125">Choose **Create Connector** on the top-right</span></span>

![Screenshot der Registerkarte "Sicherheit" in der Connector-Konfiguration](./images/flow-conn4.png)

<span data-ttu-id="26df8-127">Kopieren Sie nach der Erstellung des Connectors die generierte umLeitungs- **URL**.</span><span class="sxs-lookup"><span data-stu-id="26df8-127">After the connector has been created, copy the generated **Redirect URL**.</span></span>

![Screenshot der generierten umLeitungs-URL](./images/flow-conn5.png)

<span data-ttu-id="26df8-129">Kehren Sie zur registrierten Anwendung im [Azure-Portal](https://aad.portal.azure.com) zurück, das Sie in der vorherigen Übung erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="26df8-129">Go back to the registered application in the [Azure Portal](https://aad.portal.azure.com) you created in the previous exercise.</span></span> <span data-ttu-id="26df8-130">Wählen Sie im **Microsoft Graph-Batch-App** -Blatt **Übersicht** aus, und wählen Sie dann einen Umleitungs- **URI hinzufügen**aus.</span><span class="sxs-lookup"><span data-stu-id="26df8-130">Select **Overview** on the **MS Graph Batch App** blade, then select **Add a Redirect URI**.</span></span> <span data-ttu-id="26df8-131">Fügen Sie im Feld umLeitungs- **URI** die kopierte Umleitungs- **URL** hinzu, und wählen Sie **Speichern**aus.</span><span class="sxs-lookup"><span data-stu-id="26df8-131">Add the **Redirect URL** you copied in the **Redirect URI** field and choose **Save**.</span></span>

![Screenshot des Blatts "Antwort-URLs" im Azure-Portal](./images/flow-conn-preview6.png)