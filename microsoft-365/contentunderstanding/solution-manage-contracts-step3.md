---
title: Krok nr 3. Przy Power Automate tworzenia przepływu pracy w celu przetwarzania umów
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.localizationpriority: medium
ROBOTS: ''
description: Dowiedz się, jak Power Automate przepływu pracy w celu przetwarzania umów przy użyciu Microsoft 365 rozwiązania.
ms.openlocfilehash: d83fb6e5ca911cbafc6f064c615ab15ae0f570c7
ms.sourcegitcommit: f3c912780bbcf5a5b47de192202adb3afbd5952b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2022
ms.locfileid: "63010610"
---
# <a name="step-3-use-power-automate-to-create-the-flow-to-process-your-contracts"></a>Krok nr 3. Przy Power Automate tworzenia przepływu pracy w celu przetwarzania umów

Utworzono kanał zarządzania umowami i dołączono SharePoint dokumentów. Następnym krokiem jest utworzenie przepływu Power Automate przetwarzania umów, które twój SharePoint Syntex identyfikowany i klasyfikuje. Ten krok można wykonać, [tworząc przepływ Power Automate dokumentów w SharePoint dokumentów](https://support.microsoft.com/office/create-a-flow-for-a-list-or-library-in-sharepoint-or-onedrive-a9c3e03b-0654-46af-a254-20252e580d01).

W przypadku rozwiązania do zarządzania umowami chcesz utworzyć przepływ Power Automate w celu:

-  Po klasyfikowaniu umowy przez Twój SharePoint Syntex zmień stan umowy na **W przeglądzie**.
- Umowa jest sprawdzana i zostaje zatwierdzona lub odrzucona.
- W przypadku zatwierdzonych umów informacje o umowie są publikowane na karcie przetwarzania płatności.
- W przypadku odrzuconych umów zespół jest powiadamiany o dalszej analizie. 

Na poniższym diagramie przedstawiono przepływ Power Automate rozwiązania do zarządzania umowami.

![Flow diagram przedstawiający całe rozwiązanie.](../media/content-understanding/flow-entire-process.png)

## <a name="prepare-your-contract-for-review"></a>Przygotowywanie umowy do przeglądu

Gdy umowa zostanie zidentyfikowana i sklasyfikowana przez SharePoint Syntex zrozumienia dokumentu, przepływ Power Automate najpierw zmieni stan na **W przeglądzie**.

![Aktualizowanie stanu.](../media/content-understanding/flow-overview.png)

Po wyencjonowyniu pliku zmień wartość stanu na **W trakcie sprawdzania**.

![W stanie przeglądu.](../media/content-understanding/in-review.png)

Następnym krokiem jest utworzenie adaptacyjnej karty informujący, że umowa oczekuje na sprawdzenie i opublikowanie jej w kanale Zarządzanie umowami.

![Wpis przeglądu umowy.](../media/content-understanding/contract-approval-post.png)


![Utwórz kartę adaptacyjną do przeglądania.](../media/content-understanding/adaptive-card.png)

Poniższy kod to JSON użyty w tym kroku w przepływie Power Automate danych.

```JSON
{
"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
"type": "AdaptiveCard",
"version": "1.0",
"body": [
    {
    "type": "TextBlock",
    "text": "Contract approval request",
    "size": "large",
    "weight": "bolder",
     "wrap": true
    },
        {
            "type": "Container",
            "items": [
                {
                    "type": "FactSet",
                    "spacing": "Large",
                    "facts": [
                        {
                            "title": "Client",
                            "value": "@{triggerOutputs()?['body/Client']}"
                        },
                        {
                            "title": "Contractor",
                            "value": "@{triggerOutputs()?['body/Contractor']}"
                        },
                        {
                            "title": "Fee amount",
                            "value": "@{triggerOutputs()?['body/FeeAmount']}"
                        },
                        {
                            "title": "Date created",
                            "value": "@{triggerOutputs()?['body/Modified']} "
                        },
                        {
                            "title": "Link",
                            "value": "[@{triggerOutputs()?['body/{FilenameWithExtension}']}](@{triggerOutputs()?['body/{Link}']})"
                        }
                    ]
                }
            ]
         },
    {
    "type": "TextBlock",
    "text": "Comment:"
    },
        {
            "type": "Input.Text",
            "placeholder": "Enter comments",
            "id": "acComments"
        }
],
"actions": [
    {
    "type": "Action.Submit",
    "title": "Approve",
    "data": {
        "x": "Approve"
    }
    },
    {
    "type": "Action.Submit",
    "title": "Reject",
    "data": {
        "x": "Reject"
    }
    }
]
}
```


## <a name="conditional-context"></a>Kontekst warunkowy

Następnie w przepływie musisz utworzyć warunek, w którym Twoja umowa zostanie zatwierdzona lub [odrzucona](#if-the-contract-is-rejected).[](#if-the-contract-is-approved)

![Warunkowe.](../media/content-understanding/condition.png)

## <a name="if-the-contract-is-approved"></a>Jeśli umowa została zatwierdzona

Po zatwierdzeniu umowy występują następujące zdarzenia:

- Na karcie **Umowy** stan na karcie umowa zmieni się **na Zatwierdzony.**

   ![Zatwierdzono stan karty.](../media/content-understanding/approved-contracts-tab.png)

- W twoim przepływie stan zmienia się na **Zatwierdzony**.

   ![Flow zatwierdzonego statusu.](../media/content-understanding/status-approved.png)

- W przypadku tego rozwiązania dane dotyczące umowy zostaną dodane do karty **Wypłaty** , aby można było zarządzać wypłatami. Ten proces można rozszerzyć, aby umożliwić przepływowi przesyłanie kontraktów na płatności przez aplikację finansową innej firmy (na przykład Dynamics CRM).

   ![Umowa została przeniesiona do płatności.](../media/content-understanding/for-payout.png)

- W przepływie możesz utworzyć następujący element, aby przenieść zatwierdzone umowy na **kartę Wypłaty** .

   ![Flow element, aby przejść do pozycji Zapłać.](../media/content-understanding/ready-for-payout.png)

    Aby uzyskać wyrażenia dla potrzebnych informacji z Teams danych, użyj wartości pokazanych w poniższej tabeli.
 
    |Name (Nazwa)     |Expression |
    |---------|-----------|
    | Stan zatwierdzenia  | body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')? ['submitActionId']         |
    | Zatwierdzone przez     | body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')? ['odpowiadanie'] ['nazwa_wyświetlana']        |
    | Data zatwierdzenia     | body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')? ['czas odpowiedzi']         |
    | Komentowanie     | body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')? ['dane']? ['acComments']         |
    
    W poniższym przykładzie pokazano, jak za pomocą pola formuły Power Automate napisać wyrażenie.

   ![Zrzut ekranu Power Automate przedstawiający formułę wyrażenia.](../media/content-understanding/expression-formula-power-automate.png)    

- Adaptacyjna karta z informacją, że zatwierdzono umowę, jest tworzona i publikowana w kanale zarządzania umowami.

   ![Opublikowane zatwierdzenie umowy.](../media/content-understanding/adaptive-card-approval.png)

   ![Adaptacyjne zatwierdzanie kart.](../media/content-understanding/adaptive-card.png)


   Poniższy kod to JSON użyty w tym kroku w przepływie Power Automate danych.

```JSON
{ 
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "Container",
            "style": "emphasis",
            "items": [
                {
                    "type": "ColumnSet",
                    "columns": [
                        {
                            "type": "Column",
                            "items": [
                                {
                                    "type": "TextBlock",
                                    "size": "Large",
                                    "weight": "Bolder",
                                    "text": "CONTRACT APPROVED"
                                }
                            ],
                            "width": "stretch"
                        }
                    ]
                }
            ],
            "bleed": true
        },
        {
            "type": "Container",
            "items": [
                {
                    "type": "FactSet",
                    "spacing": "Large",
                    "facts": [
                        {
                            "title": "Client",
                            "value": "@{triggerOutputs()?['body/Client']}"
                        },
                        {
                            "title": "Contractor",
                            "value": "@{triggerOutputs()?['body/Contractor']}"
                        },
                        {
                            "title": "Fee amount",
                            "value": "@{triggerOutputs()?['body/FeeAmount']}"
                        },
                        {
                            "title": "Approval by",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responder']['displayName']}"
                        },
                        {
                            "title": "Approved date",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responseTime']}"
                        },
                        {
                            "title": "Approval comment",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['data']?['acComments']}"
                        },
                        {
                            "title": " ",
                            "value": " "
                        },
                        {
                            "title": "Status",
                            "value": "Ready for payout"
                        }
                    ]
                }
            ]
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2",
    "fallbackText": "This card requires Adaptive Cards v1.2 support to be rendered properly."
}
```

## <a name="if-the-contract-is-rejected"></a>Jeśli umowa zostanie odrzucona

Po odrzuceniu umowy występują następujące zdarzenia:

- Na karcie **Umowy** stan na karcie umowa zmieni się na **Odrzucone**.

   ![Odrzucono stan karty.](../media/content-understanding/rejected-contracts-tab.png)

- W przepływie możesz wyewidencjonać plik umowy, zmienić stan na **Odrzucony**, a następnie zaewidencjonać plik z powrotem.

   ![Flow w pliku umowy.](../media/content-understanding/reject-flow.png)

- W przepływie tworzysz kartę adaptacyjną z informacją, że umowa została odrzucona.

   ![Flow jest na karcie adaptacyjnej jest przedstawiany stan odrzucony.](../media/content-understanding/reject-flow-item.png)

Poniższy kod to JSON użyty w tym kroku w przepływie Power Automate danych.

```JSON
{ 
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "Container",
            "style": "attention",
            "items": [
                {
                    "type": "ColumnSet",
                    "columns": [
                        {
                            "type": "Column",
                            "items": [
                                {
                                    "type": "TextBlock",
                                    "size": "Large",
                                    "weight": "Bolder",
                                    "text": "CONTRACT REJECTED"
                                }
                            ],
                            "width": "stretch"
                        }
                    ]
                }
            ],
            "bleed": true
        },
        {
            "type": "Container",
            "items": [
                {
                    "type": "FactSet",
                    "spacing": "Large",
                    "facts": [
                        {
                            "title": "Client",
                            "value": "@{triggerOutputs()?['body/Client']}"
                        },
                        {
                            "title": "Contractor",
                            "value": "@{triggerOutputs()?['body/Contractor']}"
                        },
                        {
                            "title": "Fee amount",
                            "value": "@{triggerOutputs()?['body/FeeAmount']}"
                        },
                        {
                            "title": "Rejected by",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responder']['displayName']}"
                        },
                        {
                            "title": "Rejected date",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responseTime']}"
                        },
                        {
                            "title": "Comment",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['data']?['acComments']}"
                        },
                        {
                            "title": " ",
                            "value": " "
                        },
                        {
                            "title": "Status",
                            "value": "Needs review"
                        }
                    ]
                }
            ]
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2",
    "fallbackText": "This card requires Adaptive Cards v1.2 support to be rendered properly."
}
```

- Karta zostanie opublikowana w kanale Zarządzanie umowami.

   ![Flow kartę adaptacyjną, aby odrzucić.](../media/content-understanding/rejected.png)
