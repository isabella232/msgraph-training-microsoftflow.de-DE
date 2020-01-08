<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="2a90d-101">In dieser Übung erstellen Sie einen neuen benutzerdefinierten Connector, der in Flow oder in Azure Logic-Apps verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="2a90d-101">In this exercise, you will create a new custom connector which can be used in Flow or in Azure Logic Apps.</span></span> <span data-ttu-id="2a90d-102">Die Open API-Definitionsdatei ist mit dem korrekten Pfad für den Microsoft Graph `$batch` -Endpunkt und zusätzlichen Einstellungen zum Aktivieren des einfachen Imports vordefiniert.</span><span class="sxs-lookup"><span data-stu-id="2a90d-102">The Open API definition file is prebuilt with the correct path for the Microsoft Graph `$batch` endpoint and additional settings to enable simple import.</span></span>

<span data-ttu-id="2a90d-103">Erstellen Sie mithilfe eines Text-Editors eine neue leere Datei `MSGraph-Delegate-Batch.swagger.json` mit dem Namen, und fügen Sie den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="2a90d-103">Using a text editor, create a new empty file named `MSGraph-Delegate-Batch.swagger.json` and add the following code.</span></span>

[!code-json[](../LabFiles/MSGraph-Delegate-Batch.swagger.json)]

<span data-ttu-id="2a90d-104">Öffnen Sie einen Browser, und navigieren Sie zu [Microsoft Flow](https://flow.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="2a90d-104">Open a browser and navigate to [Microsoft Flow](https://flow.microsoft.com).</span></span> <span data-ttu-id="2a90d-105">Melden Sie sich mit Ihrem Office 365 mandantenadministrator Konto an.</span><span class="sxs-lookup"><span data-stu-id="2a90d-105">Sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="2a90d-106">Wählen Sie das Zahnradsymbol in der oberen rechten Ecke aus, und wählen Sie im Dropdownmenü das Element **benutzerdefinierte Verbinder** aus.</span><span class="sxs-lookup"><span data-stu-id="2a90d-106">Choose the gear icon in the upper right, and select the **Custom Connectors** item in the drop-down menu.</span></span>

![Ein Screenshot des Dropdownmenüs in Microsoft Flow](./images/flow-conn1.png)

<span data-ttu-id="2a90d-108">Klicken Sie auf der Seite **benutzerdefinierte Connectors** auf den Link **benutzerdefinierten Verbinder erstellen** in der oberen rechten Ecke, und wählen Sie dann im Dropdownmenü das Element **Open API-Datei importieren** aus.</span><span class="sxs-lookup"><span data-stu-id="2a90d-108">On the **Custom Connectors** page choose the **Create custom connector** link in the top right, then select the **Import an Open API file** item in the drop-down menu.</span></span>

 ![Ein Screenshot des Dropdownmenüs zum Erstellen eines benutzerdefinierten Connectors in Microsoft Flow](./images/flow-conn2.png)

<span data-ttu-id="2a90d-110">Geben `MS Graph Batch Connector` Sie in das Textfeld **Name des benutzerdefinierten Connectors** ein.</span><span class="sxs-lookup"><span data-stu-id="2a90d-110">Enter `MS Graph Batch Connector` in the **Custom connector name** text box.</span></span> <span data-ttu-id="2a90d-111">Wählen Sie das Ordnersymbol aus, um die geöffnete API-Datei hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="2a90d-111">Choose the folder icon to upload the Open API file.</span></span> <span data-ttu-id="2a90d-112">Wechseln Sie zu `MSGraph-Delegate-Batch.swagger.json` der Datei, die Sie erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="2a90d-112">Browse to the `MSGraph-Delegate-Batch.swagger.json` file you created.</span></span> <span data-ttu-id="2a90d-113">Wählen Sie **weiter** aus, um die geöffnete API-Datei hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="2a90d-113">Choose **Continue** to upload the Open API file.</span></span>

 ![Ein Screenshot des Dialogfelds "benutzerdefinierten Connector erstellen"](./images/flow-conn3.png)

<span data-ttu-id="2a90d-115">Klicken Sie auf der Seite Connector-Konfiguration im Navigationsmenü auf den Link **Sicherheit** .</span><span class="sxs-lookup"><span data-stu-id="2a90d-115">On the connector configuration page, choose the **Security** link in the navigation menu.</span></span> <span data-ttu-id="2a90d-116">Füllen Sie die Felder wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="2a90d-116">Fill in the fields as follows.</span></span>

- <span data-ttu-id="2a90d-117">**Wählen Sie aus, welche Authentifizierung von ihrer API implementiert wird**:`OAuth 2.0`</span><span class="sxs-lookup"><span data-stu-id="2a90d-117">**Choose what authentication is implemented by your API**: `OAuth 2.0`</span></span>
- <span data-ttu-id="2a90d-118">**Identitätsanbieter**:`Azure Active Directory`</span><span class="sxs-lookup"><span data-stu-id="2a90d-118">**Identity Provider**: `Azure Active Directory`</span></span>
- <span data-ttu-id="2a90d-119">**Client-ID**: die Anwendungs-ID, die Sie in der vorherigen Übung erstellt haben</span><span class="sxs-lookup"><span data-stu-id="2a90d-119">**Client id**: the application ID you created in the previous exercise</span></span>
- <span data-ttu-id="2a90d-120">**Geheimer Client**Schlüssel: der Schlüssel, den Sie in der vorherigen Übung erstellt haben</span><span class="sxs-lookup"><span data-stu-id="2a90d-120">**Client secret**: the key you created in the previous exercise</span></span>
- <span data-ttu-id="2a90d-121">**Anmelde-URL**:`https://login.windows.net`</span><span class="sxs-lookup"><span data-stu-id="2a90d-121">**Login url**: `https://login.windows.net`</span></span>
- <span data-ttu-id="2a90d-122">**Mandanten-ID**:`common`</span><span class="sxs-lookup"><span data-stu-id="2a90d-122">**Tenant ID**: `common`</span></span>
- <span data-ttu-id="2a90d-123">**Ressourcen**-URL `https://graph.microsoft.com` : (kein Trailing/)</span><span class="sxs-lookup"><span data-stu-id="2a90d-123">**Resource URL**: `https://graph.microsoft.com` (no trailing /)</span></span>
- <span data-ttu-id="2a90d-124">**Bereich**: leer lassen</span><span class="sxs-lookup"><span data-stu-id="2a90d-124">**Scope**: Leave blank</span></span>

<span data-ttu-id="2a90d-125">Wählen Sie in der oberen rechten Ecke **Create Connector** aus.</span><span class="sxs-lookup"><span data-stu-id="2a90d-125">Choose **Create Connector** on the top-right</span></span>

![Ein Screenshot der Registerkarte "Sicherheit" in der Connector-Konfiguration](./images/flow-conn4.png)

<span data-ttu-id="2a90d-127">Nachdem der Connector erstellt wurde, kopieren Sie die generierte **Umleitungs-URL**.</span><span class="sxs-lookup"><span data-stu-id="2a90d-127">After the connector has been created, copy the generated **Redirect URL**.</span></span>

![Ein Screenshot der generierten Umleitungs-URL](./images/flow-conn5.png)

<span data-ttu-id="2a90d-129">Kehren Sie zur registrierten Anwendung im [Azure-Portal](https://aad.portal.azure.com) zurück, das Sie in der vorherigen Übung erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="2a90d-129">Go back to the registered application in the [Azure Portal](https://aad.portal.azure.com) you created in the previous exercise.</span></span> <span data-ttu-id="2a90d-130">Wählen Sie **Antwort-URLs** im Blade **Einstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="2a90d-130">Select **Reply URLs** in the **Settings** blade.</span></span> <span data-ttu-id="2a90d-131">Fügen Sie die **Umleitungs-URL** ein, die Sie als zusätzliche **Antwort-URL**kopiert haben.</span><span class="sxs-lookup"><span data-stu-id="2a90d-131">Add the **Redirect URL** you copied as an additional **Reply URL**.</span></span> <span data-ttu-id="2a90d-132">Speichern Sie die Anwendung im Azure Active Directory-Portal.</span><span class="sxs-lookup"><span data-stu-id="2a90d-132">Save the application in Azure Active Directory portal.</span></span>

![Ein Screenshot des Blatts "Antwort-URLs" im Azure-Portal](./images/flow-conn6.png)
