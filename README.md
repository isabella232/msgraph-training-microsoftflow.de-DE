# <a name="microsoft-graph-training-module---create-a-microsoft-graph-json-batch-custom-connector-for-microsoft-power-automate--azure-logic-apps"></a><span data-ttu-id="71154-101">Microsoft Graph-Schulungsmodul – Erstellen eines benutzerdefinierten Microsoft Graph-Connectors für Microsoft Power automatisieren & Azure Logic-apps</span><span class="sxs-lookup"><span data-stu-id="71154-101">Microsoft Graph Training Module - Create a Microsoft Graph JSON Batch Custom Connector for Microsoft Power Automate & Azure Logic Apps</span></span>

<span data-ttu-id="71154-102">In diesem Modul wird das Arbeiten mit der Microsoft Graph JSON-Batchverarbeitung-Rest-API zum Zugreifen auf Daten in Office 365 vorgestellt.</span><span class="sxs-lookup"><span data-stu-id="71154-102">This module will introduce you to working with the Microsoft Graph JSON Batching REST API to access data in Office 365.</span></span> <span data-ttu-id="71154-103">In diesem Artikel erfahren Sie, wie Sie einen benutzerdefinierten Connector für Microsoft Power Automation erstellen und konfigurieren, auf die Microsoft Graph JSON-Batch-API zugreifen und den benutzerdefinierten Connector in einem Flow zum Erstellen eines Microsoft-Teams verwenden.</span><span class="sxs-lookup"><span data-stu-id="71154-103">You will learn how to create and configure a custom connector for Microsoft Power Automate, access the the Microsoft Graph JSON Batch API, and use the custom connector in a flow to create a Microsoft Team.</span></span>

## <a name="lab---create-a-microsoft-graph-json-batch-custom-connector-for-microsoft-power-automate--azure-logic-apps"></a><span data-ttu-id="71154-104">Lab-erstellen Sie einen Microsoft Graph JSON-Batch-Connector für Microsoft Power automatisieren & Azure Logic-apps</span><span class="sxs-lookup"><span data-stu-id="71154-104">Lab - Create a Microsoft Graph JSON Batch Custom Connector for Microsoft Power Automate & Azure Logic Apps</span></span>

<span data-ttu-id="71154-105">In dieser Übungseinheit nutzen Sie die Microsoft Graph JSON-Batchverarbeitung-Rest-API, um eine benutzerdefinierte Anwendung für den Connector und den Fluss zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="71154-105">In this lab you will leverage the Microsoft Graph JSON Batching REST API to create a Custom Connector and flow application.</span></span>

- [<span data-ttu-id="71154-106">Power Automatisieren von Microsoft Graph Tutorial</span><span class="sxs-lookup"><span data-stu-id="71154-106">Power Automate Microsoft Graph tutorial</span></span>](https://docs.microsoft.com/graph/tutorials/powerautomate)

## <a name="contributors"></a><span data-ttu-id="71154-107">Mitwirkende</span><span class="sxs-lookup"><span data-stu-id="71154-107">Contributors</span></span>

| <span data-ttu-id="71154-108">Rollen</span><span class="sxs-lookup"><span data-stu-id="71154-108">Roles</span></span>       | <span data-ttu-id="71154-109">Autor (en)</span><span class="sxs-lookup"><span data-stu-id="71154-109">Author(s)</span></span>                                            |
|-------------|------------------------------------------------------|
| <span data-ttu-id="71154-110">Lab-Handbücher</span><span class="sxs-lookup"><span data-stu-id="71154-110">Lab Manuals</span></span> | <span data-ttu-id="71154-111">John Liu (Microsoft MVP, SharePointGurus) @johnnliu</span><span class="sxs-lookup"><span data-stu-id="71154-111">John Liu (Microsoft MVP, SharePointGurus) @johnnliu</span></span>  |
| <span data-ttu-id="71154-112">Lab-Handbücher</span><span class="sxs-lookup"><span data-stu-id="71154-112">Lab Manuals</span></span> | <span data-ttu-id="71154-113">Pete Skelly (ThreeWill) @pskelly</span><span class="sxs-lookup"><span data-stu-id="71154-113">Pete Skelly (ThreeWill) @pskelly</span></span>                     |
| <span data-ttu-id="71154-114">Lab-Handbücher</span><span class="sxs-lookup"><span data-stu-id="71154-114">Lab Manuals</span></span> | <span data-ttu-id="71154-115">Ayca Bas (Microsoft) @aycabas</span><span class="sxs-lookup"><span data-stu-id="71154-115">Ayca Bas (Microsoft) @aycabas</span></span>                        |

## <a name="version-history"></a><span data-ttu-id="71154-116">Versionsverlauf</span><span class="sxs-lookup"><span data-stu-id="71154-116">Version history</span></span>

| <span data-ttu-id="71154-117">Version</span><span class="sxs-lookup"><span data-stu-id="71154-117">Version</span></span> | <span data-ttu-id="71154-118">Datum</span><span class="sxs-lookup"><span data-stu-id="71154-118">Date</span></span>              | <span data-ttu-id="71154-119">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="71154-119">Comments</span></span>                                             |
|---------|-------------------|------------------------------------------------------|
| <span data-ttu-id="71154-120">1.3</span><span class="sxs-lookup"><span data-stu-id="71154-120">1.3</span></span>     | <span data-ttu-id="71154-121">24. August 2020</span><span class="sxs-lookup"><span data-stu-id="71154-121">August 24, 2020</span></span>   | <span data-ttu-id="71154-122">Aktualisierung auf Power Automation</span><span class="sxs-lookup"><span data-stu-id="71154-122">Updated to Power Automate</span></span>                            |
| <span data-ttu-id="71154-123">1.2</span><span class="sxs-lookup"><span data-stu-id="71154-123">1.2</span></span>     | <span data-ttu-id="71154-124">27. November 2018</span><span class="sxs-lookup"><span data-stu-id="71154-124">November 27, 2018</span></span> | <span data-ttu-id="71154-125">Onboarding zu docs.Microsoft.com/Graph</span><span class="sxs-lookup"><span data-stu-id="71154-125">Onboarded to docs.microsoft.com/graph</span></span>                |
| <span data-ttu-id="71154-126">1.1</span><span class="sxs-lookup"><span data-stu-id="71154-126">1.1</span></span>     | <span data-ttu-id="71154-127">November 07, 2018</span><span class="sxs-lookup"><span data-stu-id="71154-127">November 07, 2018</span></span> | <span data-ttu-id="71154-128">Schritt 6-Inhalt zum Aufrufen mehrerer Vorgänge hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="71154-128">Added step 6 content for calling multiple operations</span></span> |
| <span data-ttu-id="71154-129">1.0</span><span class="sxs-lookup"><span data-stu-id="71154-129">1.0</span></span>     | <span data-ttu-id="71154-130">22. Oktober 2018</span><span class="sxs-lookup"><span data-stu-id="71154-130">October 22, 2018</span></span>  | <span data-ttu-id="71154-131">Hinzufügen von Microsoft Graph-bezogenen Produkt Ausbrüchen.</span><span class="sxs-lookup"><span data-stu-id="71154-131">Add Microsoft Graph related product breakouts.</span></span>       |

## <a name="disclaimer"></a><span data-ttu-id="71154-132">Haftungsausschluss</span><span class="sxs-lookup"><span data-stu-id="71154-132">Disclaimer</span></span>

<span data-ttu-id="71154-133">**Dieser Code wird ohne jegliche ausdrückliche oder implizite *Gewährleistung bereit* gestellt, einschließlich impliziter Garantien für die Eignung für einen bestimmten Zweck, die Marktgängigkeit oder die Nichtverletzung.**</span><span class="sxs-lookup"><span data-stu-id="71154-133">**THIS CODE IS PROVIDED *AS IS* WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING ANY IMPLIED WARRANTIES OF FITNESS FOR A PARTICULAR PURPOSE, MERCHANTABILITY, OR NON-INFRINGEMENT.**</span></span>
