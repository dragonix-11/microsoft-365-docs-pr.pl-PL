---
title: Krok nr 2. Użyj Microsoft Teams, aby utworzyć kanał zarządzania umowami
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
description: Dowiedz się, jak za Microsoft Teams utworzyć kanał zarządzania umowami przy użyciu Microsoft 365 rozwiązania.
ms.openlocfilehash: a5a42bedcb6acba4caf8f6f114812c63869ee92e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985460"
---
# <a name="step-2-use-microsoft-teams-to-create-your-contract-management-channel"></a>Krok nr 2. Użyj Microsoft Teams, aby utworzyć kanał zarządzania umowami

Podczas organizacji konfiguruje się rozwiązanie do zarządzania umowami, potrzebujesz centralnej lokalizacji, w której uczestnicy projektu mogą przeglądać umowy i zarządzać nimi. W tym celu możesz za pomocą Microsoft Teams [](/microsoftteams/) skonfigurować kanał Teams oraz korzystać z funkcji dostępnych w Teams:

- **Utwórz miejsce dla uczestników projektu, w którym z łatwością będą widzieć wszystkie umowy wymagające działania.** Na przykład w programie Teams można utworzyć kartę Umowy w  kanale Zarządzanie umowami, w której członkowie mogą wyświetlać użyteczny widok kafelków wszystkich umów, które wymagają zatwierdzenia. Można również skonfigurować widok tak, aby każda "karta" zawierała ważne dane (takie jak *Klient, Wykonawca* i *Kwota opłaty*). 

     ![Karta Umowy.](../media/content-understanding/tile-view.png)

- **W tym miejscu członkowie mogą wchodzić ze sobą w interakcje i widzieć ważne zdarzenia.** Na przykład w programie Teams na karcie Wpisy można  m.in. umożliwiać konwersacje, uzyskiwanie aktualizacji i wyświetlanie akcji (takich jak członek odrzucający umowę). Jeśli coś się stało (na przykład została przesłana do zatwierdzenia nowa umowa),  karta Wpisy może być używana nie tylko do jej ogłaszania, ale także do rejestrować jej informacje. A jeśli członkowie subskrybują powiadomienia, będą otrzymywać powiadomienia po każdej aktualizacji.

     ![Karta Wpisy.](../media/content-understanding/posts.png)

- **Miej miejsce, w którym członkowie mogą zobaczyć zatwierdzone umowy i wiedzieć, kiedy można ich przesłać o płatność.** W SharePoint musisz utworzyć listę do wypłat i dodać kolumny dla **klienta, wykonawcy** i kwoty **opłaty**, wybierając pojedynczy wiersz tekstu jako typ kolumny.  Musisz dodać listę Do wypłat jako kartę Teams w kanale Zarządzanie umowami, podobnie jak na karcie [**Umowy**](solution-manage-contracts-step2.md#attach-your-sharepoint-document-library-to-the-contracts-tab). Na **karcie Wypłaty** zostanie wyświetlona lista wszystkich umów, które muszą zostać przesłane do zapłaty. Możesz łatwo rozszerzyć to rozwiązanie, aby zamiast tego napisać te informacje bezpośrednio do innej aplikacji finansowej (na przykład Dynamics CRM). 


## <a name="attach-your-sharepoint-document-library-to-the-contracts-tab"></a>Dołączanie SharePoint dokumentów do karty Umowy

Po utworzeniu karty **Umowy** w kanale Zarządzanie umowami musisz dołączyć do niego własną SharePoint [dokumentów](https://support.microsoft.com/office/add-a-sharepoint-page-list-or-document-library-as-a-tab-in-teams-131edef1-455f-4c67-a8ce-efa2ebf25f0b). Biblioteka SharePoint dokumentów, do której chcesz dołączyć, to ta, do której zastosowano model SharePoint Syntex w poprzedniej sekcji.

Po dołączeniu SharePoint dokumentów będzie można wyświetlać wszystkie sklasyfikowane umowy za pomocą domyślnego widoku listy.

   ![Widok listy SharePoint biblioteki.](../media/content-understanding/list-view.png)

## <a name="customize-your-contracts-tab-tile-view"></a>Dostosowywanie widoku kafelka karty Umowy

> [!NOTE]
> Ta sekcja odwołuje się do przykładów kodu zawartych w pliku [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) , który znajduje się w repozytorium Rozwiązania do zarządzania [umowami](https://github.com/pnp/syntex-samples/tree/main/scenario%20assets/Contracts%20Management).

Chociaż Teams pozwala na wyświetlanie umów w widoku kafelków, możesz dostosować je tak, aby były wyświetlane dane kontraktu, które mają być widoczne na karcie umowy. Na przykład na karcie **Umowy** członkowie mogą zobaczyć klienta, wykonawcę i kwotę opłaty na karcie umowy. Wszystkie te pola zostały wyodrębnione z każdej umowy za pośrednictwem SharePoint Syntex dokumentów, który został zastosowany do biblioteki dokumentów. Chcesz również mieć możliwość zmiany kolorów paska nagłówka kafelków na różne dla poszczególnych stanów, aby członkowie mogli łatwo zobaczyć, gdzie umowa jest w procesie zatwierdzania. Na przykład wszystkie zatwierdzone umowy będą zawierały niebieski pasek nagłówka.

   ![Widok kafelka biblioteki SharePoint.](../media/content-understanding/tile.png)

Niestandardowy widok kafelków, który jest używany, wymaga zmiany w pliku JSON używanym do formatowania bieżącego widoku kafelków. Można odwołać się do pliku JSON użytego do utworzenia widoku karty, patrząc na plik [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) . W poniższych sekcjach zobaczysz konkretne sekcje kodu dla funkcji, które znajdują się na kartach umowy.

Jeśli chcesz wyświetlić lub wprowadzić zmiany w kodzie JSON widoku w kanale programu Teams, w kanale Teams wybierz menu rozwijane widok, a następnie wybierz polecenie Formatuj bieżący **widok.**

   ![Zrzut ekranu przedstawiający format json w Teams kanału.](../media/content-understanding/jason-format.png)

## <a name="card-size-and-shape"></a>Rozmiar i kształt karty

W pliku [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) w następnej sekcji przedstawiono kod formatowania rozmiaru i kształtu wizytówki.

```JSON
                  {
                    "elmType": "div",
                    "style": {
                      "background-color": "#f5f5f5",
                      "padding": "5px",
                      "width": "180px"
                    },
                    "children": [
                      {
                        "elmType": "img",
                        "attributes": {
                          "src": "@thumbnail.large"
                        },
                        "style": {
                          "width": "185px",
                          "height": "248px"
                        }
                      }
```

## <a name="contract-status"></a>Stan umowy

Poniższy kod pozwala zdefiniować stan każdej karty tytułowej. Pamiętaj, że każda wartość *stanu (Nowy**, W* recenzji, *Zatwierdzone* i Odrzucone *) będzie* wyświetlać inny kod koloru dla każdego z nich. W [pliku ContractTileFormatting.json przyjrzyj](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) się sekcji definiującej stan.

```JSON
          {
            "elmType": "div",
            "children": [
              {
                "elmType": "div",
                "style": {
                  "color": "white",
                  "background-color": "=if([$Status] == 'New', '#00b7c3', if([$Status] == 'In review', '#ffaa44', if([$Status] == 'Approved', '#0078d4', if([$Status] == 'Rejected', '#d13438', '#8378de'))))",
                  "padding": "5px 15px",
                  "height": "auto",
                  "text-transform": "uppercase",
                  "font-size": "12.5px"
                },
                "txtContent": "[$Status]"
              }
```

## <a name="extracted-fields"></a>Wyodrębnione pola

Na każdej karcie umowy będą wyświetlane trzy pola wyodrębnione dla każdej umowy (*Klient*, *Wykonawca* i *Kwota opłaty*). Ponadto chcesz wyświetlić również datę/godzinę klasyfikacji pliku przy SharePoint Syntex używanym do jego identyfikowania.

W pliku [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) poniższe sekcje określają każdy z nich.

### <a name="client"></a>Klient

Ta sekcja określa sposób wyświetlania informacji "Klient" na karcie i używa wartości określonej umowy.

```JSON
                      {
                        "elmType": "div",
                        "style": {
                          "color": "#767676",
                          "font-size": "12px"
                        },
                        "txtContent": "Client"
                      },
                      {
                        "elmType": "div",
                        "style": {
                          "margin-bottom": "12px",
                          "font-size": "16px",
                          "font-weight": "600"
                        },
                        "txtContent": "[$Client]"
                      },
```

### <a name="contractor"></a>Wykonawca

Ta sekcja określa sposób wyświetlania "Wykonawcy" na karcie i wykorzystuje wartość określonej umowy.

```JSON
                        {
                          "elmType": "div",
                          "txtContent": "Contractor",
                          "style": {
                            "color": "#767676",
                            "font-size": "12px",
                            "margin-bottom": "2px"
                          }
                        },
                        {
                          "elmType": "div",
                          "style": {
                            "margin-bottom": "12px",
                            "font-size": "14px"
                          },
                          "txtContent": "[$Contractor]"
                        },
```

### <a name="fee-amount"></a>Kwota opłaty

Ta sekcja określa sposób wyświetlania kwoty opłaty na karcie i używa wartości określonej umowy.

```JSON
                      {
                        "elmType": "div",
                        "txtContent": "Fee amount",
                        "style": {
                          "color": "#767676",
                          "font-size": "12px",
                          "margin-bottom": "2px"
                        }
                      },
                      {
                        "elmType": "div",
                        "style": {
                          "margin-bottom": "12px",
                          "font-size": "14px"
                        },
                        "txtContent": "[$FeeAmount]"
                      },
```

### <a name="classification-date"></a>Data klasyfikacji

Ta sekcja określa sposób wyświetlania na karcie informacji "Klasyfikacja" i używa wartości określonej umowy.

```JSON
                      {
                        "elmType": "div",
                        "txtContent": "Classified",
                        "style": {
                          "color": "#767676",
                          "font-size": "12px",
                          "margin-bottom": "2px"
                        }
                      },
                      {
                        "elmType": "div",
                        "style": {
                          "margin-bottom": "12px",
                          "font-size": "14px"
                        },
                        "txtContent": "[$PrimeLastClassified]"
                      }
```

## <a name="next-step"></a>Następny krok

[Krok 3. Przy Power Automate tworzenia przepływu pracy w celu przetwarzania umów](solution-manage-contracts-step3.md)
