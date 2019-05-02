<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="e2968-101">In dieser Übung erstellen Sie einen neuen benutzerdefinierten Connector, der in Flow oder in Azure Logic-Apps verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="e2968-101">In this exercise, you will create a new custom connector which can be used in Flow or in Azure Logic Apps.</span></span> <span data-ttu-id="e2968-102">Die Definitionsdatei für die Open-API ist mit dem korrekten Pfad für den `$batch` Microsoft Graph-Endpunkt und zusätzlichen Einstellungen für den einfachen Import vordefiniert.</span><span class="sxs-lookup"><span data-stu-id="e2968-102">The Open API definition file is prebuilt with the correct path for the Microsoft Graph `$batch` endpoint and additional settings to enable simple import.</span></span>

<span data-ttu-id="e2968-103">Erstellen Sie mit einem Text-Editor eine neue leere Datei `MSGraph-Delegate-Batch.swagger.json` mit dem Namen, und fügen Sie den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="e2968-103">Using a text editor, create a new empty file named `MSGraph-Delegate-Batch.swagger.json` and add the following code.</span></span>

[!code-json[](../LabFiles/MSGraph-Delegate-Batch.swagger.json)]

<span data-ttu-id="e2968-104">Öffnen Sie einen Browser, und navigieren Sie zu [Microsoft Flow](https://flow.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="e2968-104">Open a browser and navigate to [Microsoft Flow](https://flow.microsoft.com).</span></span> <span data-ttu-id="e2968-105">Melden Sie sich mit Ihrem Office 365-mandantenadministrator Konto an.</span><span class="sxs-lookup"><span data-stu-id="e2968-105">Sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="e2968-106">Klicken Sie oben rechts auf das Zahnradsymbol, und wählen Sie im Dropdownmenü das Element **benutzerdefinierte Verbinder** aus.</span><span class="sxs-lookup"><span data-stu-id="e2968-106">Choose the gear icon in the upper right, and select the **Custom Connectors** item in the drop-down menu.</span></span>

![Screenshot des Dropdownmenüs in Microsoft Flow](./images/flow-conn1.png)

<span data-ttu-id="e2968-108">Wählen Sie auf der Seite **benutzerdefinierte Connectors** den Link **benutzerdefinierten Verbinder erstellen** oben rechts aus, und wählen Sie dann im Dropdownmenü das Element **eine geöffnete API-Datei importieren** aus.</span><span class="sxs-lookup"><span data-stu-id="e2968-108">On the **Custom Connectors** page choose the **Create custom connector** link in the top right, then select the **Import an Open API file** item in the drop-down menu.</span></span>

 ![Ein Screenshot des Dropdownmenüs benutzerdefinierte Verbindung erstellen in Microsoft Flow](./images/flow-conn2.png)

<span data-ttu-id="e2968-110">Geben `MS Graph Batch Connector` Sie in das Textfeld **benutzerdefinierter Connectorname** ein.</span><span class="sxs-lookup"><span data-stu-id="e2968-110">Enter `MS Graph Batch Connector` in the **Custom connector name** text box.</span></span> <span data-ttu-id="e2968-111">Klicken Sie auf das Ordnersymbol, um die geöffnete API-Datei hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="e2968-111">Choose the folder icon to upload the Open API file.</span></span> <span data-ttu-id="e2968-112">Navigieren Sie zu `MSGraph-Delegate-Batch.swagger.json` der Datei, die Sie erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="e2968-112">Browse to the `MSGraph-Delegate-Batch.swagger.json` file you created.</span></span> <span data-ttu-id="e2968-113">Wählen Sie **weiter** , um die offene API-Datei hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="e2968-113">Choose **Continue** to upload the Open API file.</span></span>

 ![Screenshot des Dialogfelds "benutzerdefinierten Connector erstellen"](./images/flow-conn3.png)

<span data-ttu-id="e2968-115">Klicken Sie auf der Seite Connector-Konfiguration im Navigationsmenü auf den Link **Sicherheit** .</span><span class="sxs-lookup"><span data-stu-id="e2968-115">On the connector configuration page, choose the **Security** link in the navigation menu.</span></span> <span data-ttu-id="e2968-116">Füllen Sie die Felder wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="e2968-116">Fill in the fields as follows.</span></span>

- <span data-ttu-id="e2968-117">**Wählen Sie aus, welche Authentifizierung von ihrer API implementiert wird**:`OAuth 2.0`</span><span class="sxs-lookup"><span data-stu-id="e2968-117">**Choose what authentication is implemented by your API**: `OAuth 2.0`</span></span>
- <span data-ttu-id="e2968-118">**Identitätsanbieter**:`Azure Active Directory`</span><span class="sxs-lookup"><span data-stu-id="e2968-118">**Identity Provider**: `Azure Active Directory`</span></span>
- <span data-ttu-id="e2968-119">**Client-ID**: die Anwendungs-ID, die Sie in der vorherigen Übung erstellt haben</span><span class="sxs-lookup"><span data-stu-id="e2968-119">**Client id**: the application ID you created in the previous exercise</span></span>
- <span data-ttu-id="e2968-120">**Geheimer Client**Schlüssel: die Taste, die Sie in der vorherigen Übung erstellt haben</span><span class="sxs-lookup"><span data-stu-id="e2968-120">**Client secret**: the key you created in the previous exercise</span></span>
- <span data-ttu-id="e2968-121">**Anmelde-URL**:`https://login.windows.net`</span><span class="sxs-lookup"><span data-stu-id="e2968-121">**Login url**: `https://login.windows.net`</span></span>
- <span data-ttu-id="e2968-122">**Mandanten-ID**:`common`</span><span class="sxs-lookup"><span data-stu-id="e2968-122">**Tenant ID**: `common`</span></span>
- <span data-ttu-id="e2968-123">**Ressourcen**-URL `https://graph.microsoft.com` : (keine Nachverfolgung/)</span><span class="sxs-lookup"><span data-stu-id="e2968-123">**Resource URL**: `https://graph.microsoft.com` (no trailing /)</span></span>
- <span data-ttu-id="e2968-124">**Bereich**: leer lassen</span><span class="sxs-lookup"><span data-stu-id="e2968-124">**Scope**: Leave blank</span></span>

<span data-ttu-id="e2968-125">Klicken Sie oben rechts auf **Verbinder erstellen** .</span><span class="sxs-lookup"><span data-stu-id="e2968-125">Choose **Create Connector** on the top-right</span></span>

![Screenshot der Registerkarte "Sicherheit" in der Connector-Konfiguration](./images/flow-conn4.png)

<span data-ttu-id="e2968-127">Kopieren Sie nach der Erstellung des Connectors die generierte Umleitungs- **URL**.</span><span class="sxs-lookup"><span data-stu-id="e2968-127">After the connector has been created, copy the generated **Redirect URL**.</span></span>

![Screenshot der generierten Umleitungs-URL](./images/flow-conn5.png)

<span data-ttu-id="e2968-129">Kehren Sie zur registrierten Anwendung im [Azure-Portal](https://aad.portal.azure.com) zurück, das Sie in der vorherigen Übung erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="e2968-129">Go back to the registered application in the [Azure Portal](https://aad.portal.azure.com) you created in the previous exercise.</span></span> <span data-ttu-id="e2968-130">Wählen Sie im Blatt **Einstellungen** die Option **Reply URLs** aus.</span><span class="sxs-lookup"><span data-stu-id="e2968-130">Select **Reply URLs** in the **Settings** blade.</span></span> <span data-ttu-id="e2968-131">Fügen Sie die Umleitungs- **URL** hinzu, die Sie als zusätzliche **Antwort-URL**kopiert haben.</span><span class="sxs-lookup"><span data-stu-id="e2968-131">Add the **Redirect URL** you copied as an additional **Reply URL**.</span></span> <span data-ttu-id="e2968-132">Speichern Sie die Anwendung in Azure Active Directory-Portal.</span><span class="sxs-lookup"><span data-stu-id="e2968-132">Save the application in Azure Active Directory portal.</span></span>

![Screenshot des Blatts "Antwort-URLs" im Azure-Portal](./images/flow-conn6.png)