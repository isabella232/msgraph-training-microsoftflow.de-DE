<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="d3776-101">In dieser Übung erstellen Sie einen Fluss zur Verwendung des benutzerdefinierten Konnektors, den Sie in den vorherigen Übungen erstellt haben, um ein Microsoft-Team zu erstellen und zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="d3776-101">In this exercise, you will create a Flow to use the custom connector you created in previous exercises to create and configure a Microsoft Team.</span></span> <span data-ttu-id="d3776-102">Der Fluss verwendet den benutzerdefinierten Connector, um eine POST-Anforderung zum Erstellen einer einheitlichen Office 365-Gruppe zu senden, hält während der Gruppenerstellung eine Verzögerung an und sendet dann eine PUT-Anforderung, um die Gruppe einem Microsoft-Team zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="d3776-102">The Flow will use the custom connector to send a POST request to create an Office 365 Unified Group, will pause for a delay while the group creation completes, and then will send a PUT request to associate the group with a Microsoft Team.</span></span>

<span data-ttu-id="d3776-103">Am Ende sieht ihr Ablauf wie in der folgenden Abbildung aus:</span><span class="sxs-lookup"><span data-stu-id="d3776-103">In the end your Flow will look similar to the following image:</span></span>

![Screenshot des abgeschlossenen Ablaufs](./images/flow-team1.png)

<span data-ttu-id="d3776-105">Öffnen Sie [Microsoft Flow](https://flow.microsoft.com) in Ihrem Browser, und melden Sie sich mit ihrem Office 365-mandantenadministrator Konto an.</span><span class="sxs-lookup"><span data-stu-id="d3776-105">Open [Microsoft Flow](https://flow.microsoft.com) in your browser and sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="d3776-106">Wählen Sie **meine Flows** in der linken Navigationsleiste aus.</span><span class="sxs-lookup"><span data-stu-id="d3776-106">Choose **My Flows** in the left-hand navigation.</span></span> <span data-ttu-id="d3776-107">Wählen Sie **neu**, und erstellen Sie dann **aus leer**.</span><span class="sxs-lookup"><span data-stu-id="d3776-107">Choose **New**, then **Create from blank**.</span></span> <span data-ttu-id="d3776-108">Wählen Sie **Create from Blank aus**.</span><span class="sxs-lookup"><span data-stu-id="d3776-108">Choose **Create from blank**.</span></span> <span data-ttu-id="d3776-109">Geben `Manual` Sie in das Suchfeld ein, und fügen Sie den Trigger **manuell Trigger a Flow** hinzu.</span><span class="sxs-lookup"><span data-stu-id="d3776-109">Enter `Manual` in the search box and add the **Manually trigger a flow** trigger.</span></span>

<span data-ttu-id="d3776-110">Wählen Sie Add a Input aus, wählen Sie `Name` **Text** aus, und geben Sie als Titel **ein**.</span><span class="sxs-lookup"><span data-stu-id="d3776-110">Choose **Add an input**, select **Text** and enter `Name` as the title.</span></span>

![Ein Screenshot des manuellen Auslösen eines Flow-Triggers](./images/flow-team6.png)

<span data-ttu-id="d3776-112">Wählen Sie **neuer Schritt** aus `Batch` , und geben Sie in das Suchfeld ein.</span><span class="sxs-lookup"><span data-stu-id="d3776-112">Choose **New step** and type `Batch` in the search box.</span></span> <span data-ttu-id="d3776-113">Fügen Sie die Batch-Konnektor-Aktion **MS Graph** hinzu.</span><span class="sxs-lookup"><span data-stu-id="d3776-113">Add the **MS Graph Batch Connector** action.</span></span> <span data-ttu-id="d3776-114">Wählen Sie die Auslassungspunkte aus, `Batch POST-groups`und benennen Sie diese Aktion in um.</span><span class="sxs-lookup"><span data-stu-id="d3776-114">Choose the ellipsis and rename this action to `Batch POST-groups`.</span></span>

<span data-ttu-id="d3776-115">Fügen Sie den folgenden Code in \*\*\*\* das Textfeld Text der Aktion ein.</span><span class="sxs-lookup"><span data-stu-id="d3776-115">Add the following code into the **body** text box of the action.</span></span>

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

<span data-ttu-id="d3776-116">Ersetzen Sie `REPLACE` die einzelnen Platzhalter `Name` , indem Sie im Menü dynamischer **Inhalt hinzufügen** den Wert aus dem manuellen Trigger auswählen.</span><span class="sxs-lookup"><span data-stu-id="d3776-116">Replace each `REPLACE` placeholder by selecting the `Name` value from the manual trigger from the **Add dynamic content** menu.</span></span>

![Ein Screenshot des Menüs für dynamische Inhalte in Microsoft Flow](./images/flow-team2.png)

<span data-ttu-id="d3776-118">Wählen Sie **neuer Schritt**, suchen `delay` Sie nach und fügen Sie eine **Verzögerungs** Aktion hinzu, und konfigurieren Sie Sie für 1 Minute.</span><span class="sxs-lookup"><span data-stu-id="d3776-118">Choose **New step**, search for `delay` and add a **Delay** action and configure for 1 minute.</span></span>

<span data-ttu-id="d3776-119">Wählen Sie **neuer Schritt** aus `Batch` , und geben Sie in das Suchfeld ein.</span><span class="sxs-lookup"><span data-stu-id="d3776-119">Choose **New step** and type `Batch` in the search box.</span></span> <span data-ttu-id="d3776-120">Fügen Sie die Batch-Konnektor-Aktion **MS Graph** hinzu.</span><span class="sxs-lookup"><span data-stu-id="d3776-120">Add the **MS Graph Batch Connector** action.</span></span> <span data-ttu-id="d3776-121">Wählen Sie die Auslassungspunkte aus, `Batch PUT-team`und benennen Sie diese Aktion in um.</span><span class="sxs-lookup"><span data-stu-id="d3776-121">Choose the ellipsis and rename this action to `Batch PUT-team`.</span></span>

<span data-ttu-id="d3776-122">Fügen Sie den folgenden Code in \*\*\*\* das Textfeld Text der Aktion ein.</span><span class="sxs-lookup"><span data-stu-id="d3776-122">Add the following code into the **body** text box of the action.</span></span>

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

<span data-ttu-id="d3776-123">Wählen Sie `REPLACE` den Platzhalter aus, und wählen Sie dann im dynamischen Inhaltsbereich **Ausdruck** aus.</span><span class="sxs-lookup"><span data-stu-id="d3776-123">Select the `REPLACE` placeholder, then select **Expression** in the dynamic content pane.</span></span> <span data-ttu-id="d3776-124">Fügen Sie die folgende Formel in den **Ausdruck**ein.</span><span class="sxs-lookup"><span data-stu-id="d3776-124">Add the following formula into the **Expression**.</span></span>

```js
body('Batch_POST-groups').responses[0].body.id
```

![Ein Screenshot des Ausdrucks im dynamischen Inhaltsbereich](./images/flow-formula.png)

<span data-ttu-id="d3776-126">Diese Formel gibt an, dass die Gruppen-ID aus dem Ergebnis der ersten Aktion verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="d3776-126">This formula specifies that we want to use the group ID from the result of the first action.</span></span>

![Screenshot des aktualisierten Aktions Texts](./images/flow-team3.png)

<span data-ttu-id="d3776-128">Wählen Sie **Speichern**und dann Flow aus, und wählen Sie **Test** aus, um den Fluss auszuführen.</span><span class="sxs-lookup"><span data-stu-id="d3776-128">Choose **Save**, then Flow and choose **Test** to execute the Flow.</span></span>

> [!TIP]
> <span data-ttu-id="d3776-129">Wenn Sie einen Fehler wie `The template validation failed: 'The action(s) 'Batch_POST-groups' referenced by 'inputs' in action 'Batch_2' are not defined in the template'`erhalten, ist der Ausdruck falsch und wahrscheinlich verweist auf eine Fluss Aktion, die nicht gefunden werden kann.</span><span class="sxs-lookup"><span data-stu-id="d3776-129">If you receive an error like `The template validation failed: 'The action(s) 'Batch_POST-groups' referenced by 'inputs' in action 'Batch_2' are not defined in the template'`, the expression is incorrect and likely references a Flow action it cannot find.</span></span> <span data-ttu-id="d3776-130">Stellen Sie sicher, dass der Name der Aktion, auf die Sie verweisen, genau übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="d3776-130">Ensure that the action name you are referencing matches exactly.</span></span>

<span data-ttu-id="d3776-131">Wählen Sie das Optionsfeld **Ich werde die Aktion Auslöser ausführen** , und wählen Sie **& testen**.</span><span class="sxs-lookup"><span data-stu-id="d3776-131">Choose the **I'll perform the trigger** action radio button and choose **Save & Test**.</span></span> <span data-ttu-id="d3776-132">Klicken Sie im Dialogfeld auf **weiter** .</span><span class="sxs-lookup"><span data-stu-id="d3776-132">Choose **Continue** in the dialog.</span></span> <span data-ttu-id="d3776-133">Geben Sie einen Namen ohne Leerzeichen, und wählen Sie **Flow ausführen** , um ein Team zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d3776-133">Provide a name without spaces, and choose **Run flow** to create a Team.</span></span>

![Screenshot des Dialogfelds "Run Flow"](./images/flow-team4.png)

<span data-ttu-id="d3776-135">Klicken Sie abschließend auf den Link **Fluss Laufaktivität anzeigen** , und wählen Sie dann den laufenden Ablauf aus, um das Aktivitätsprotokoll anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d3776-135">Finally, choose the **See flow run activity** link, then select the running Flow to see the activity log.</span></span>

> [!NOTE]
> <span data-ttu-id="d3776-136">Möglicherweise müssen Sie auf die laufende Fluss Instanz in der Liste Verlauf ausführen klicken, um die Ausführung des Flows anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d3776-136">You may have to click on your running Flow instance in the Run history list to view your Flow execution.</span></span>

<span data-ttu-id="d3776-137">Nach Abschluss des Ablaufs wurden Ihre Office 365-Gruppe und Ihr Team konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="d3776-137">Once the Flow completes, your Office 365 Group and Team have been configured.</span></span> <span data-ttu-id="d3776-138">Wählen Sie die Batch Aktionselemente aus, um die Ergebnisse der JSON-Batch Aufrufe anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d3776-138">Select the Batch action items to view the results of the JSON Batch calls.</span></span> <span data-ttu-id="d3776-139">Die `outputs` der `Batch PUT-team` Aktion sollte den Statuscode 201 für eine erfolgreiche Team Zuordnung aufweisen, die dem folgenden Bild ähnelt.</span><span class="sxs-lookup"><span data-stu-id="d3776-139">The `outputs` of the `Batch PUT-team` action should have a status code of 201 for a successful Team association similar to the image below.</span></span>

![Ein Screenshot des erfolgreichen Ablauf Aktivitätsprotokolls](./images/flow-team5.png)