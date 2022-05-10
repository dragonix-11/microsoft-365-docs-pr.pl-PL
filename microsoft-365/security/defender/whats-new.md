---
title: Co nowego w usłudze Microsoft 365 Defender
description: Wyświetla listę nowych funkcji i funkcji w Microsoft 365 Defender
keywords: co nowego w Microsoft 365 Defender, ga, ogólnie dostępne, możliwości, dostępne, nowe
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 3c11e531e8b4706128e1519b790046f800827d67
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285023"
---
# <a name="whats-new-in-microsoft-365-defender"></a>Co nowego w usłudze Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

>Następujące funkcje są dostępne w wersji zapoznawczej lub ogólnie dostępne w najnowszej wersji Microsoft 365 Defender.

Kanał informacyjny RSS: otrzymywanie powiadomień o aktualizacji tej strony przez skopiowanie i wklejenie następującego adresu URL do czytnika kanału informacyjnego:

```http
https://docs.microsoft.com/api/search/rss?search=%22Lists+the+new+features+and+functionality+in+Microsoft+365+defender%22&locale=en-us
```

Aby uzyskać więcej informacji na temat nowości w innych produktach zabezpieczeń usługi Microsoft Defender, zobacz:

- [Co nowego w ochronie usługi Office 365 w usłudze Microsoft Defender?](../office-365-security/whats-new-in-defender-for-office-365.md)
- [Co nowego w Ochrona punktu końcowego w usłudze Microsoft Defender](../defender-endpoint/whats-new-in-microsoft-defender-endpoint.md)
- [Co nowego w Microsoft Defender for Identity](/defender-for-identity/whats-new)
- [Co nowego w Microsoft Defender for Cloud Apps](/cloud-app-security/release-notes)

Aktualizacje produktów i ważne powiadomienia można również uzyskać za pośrednictwem [centrum komunikatów](https://admin.microsoft.com/Adminportal/Home#/MessageCenter). 

## <a name="may-2022"></a>Maj 2022 r.
- (wersja zapoznawcza) Zgodnie z niedawno ogłoszonym rozszerzeniem do nowej kategorii usług o nazwie [Microsoft Security Experts](https://aka.ms/MicrosoftSecurityExperts) wprowadzamy dostępność ekspertów [usługi Microsoft Defender do wyszukiwania zagrożeń](defenderexpertsforhuntingprev.md) (Defender Experts for Hunting) w publicznej wersji zapoznawczej. Defender Experts for Hunting jest przeznaczony dla klientów, którzy mają niezawodne centrum operacji zabezpieczeń, ale chcą, aby firma Microsoft pomagała im aktywnie wyszukiwać zagrożenia w danych usługi Microsoft Defender, w tym punkty końcowe, Office 365, aplikacje w chmurze i tożsamość. 

## <a name="april-2022"></a>Kwiecień 2022 r.
- (wersja zapoznawcza) Teraz można wykonywać [akcje](advanced-hunting-take-action.md) dotyczące wiadomości e-mail bezpośrednio z wyników zapytania wyszukiwania zagrożeń. Wiadomości e-mail można przenosić do innych folderów lub trwale usuwać. 
- (wersja zapoznawcza) Nowa [`UrlClickEvents` tabela](advanced-hunting-urlclickevents-table.md) zaawansowanego wyszukiwania zagrożeń może służyć do wyszukiwania zagrożeń, takich jak kampanie phishingowe i podejrzane linki, na podstawie informacji pochodzących z kliknięć linków Sejf w wiadomościach e-mail, Microsoft Teams i aplikacjach Office 365.

## <a name="march-2022"></a>Marzec 2022 r.

- (wersja zapoznawcza) Kolejka zdarzeń została rozszerzona o kilka funkcji, które ułatwiają badanie. Ulepszenia obejmują funkcje, takie jak możliwość wyszukiwania zdarzeń według identyfikatora lub nazwy, określania niestandardowego zakresu czasu i innych.


## <a name="december-2021"></a>Grudzień 2021

- (OGÓLNA dostępność) Tabela `DeviceTvmSoftwareEvidenceBeta` została dodana krótkoterminowo w ramach zaawansowanego wyszukiwania zagrożeń, aby umożliwić wyświetlanie dowodów na to, gdzie wykryto określone oprogramowanie na urządzeniu.

## <a name="november-2021"></a>Listopad 2021

- (wersja zapoznawcza) Funkcja dodatku ładu aplikacji do aplikacji Defender dla Chmury Apps jest teraz dostępna w Microsoft 365 Defender. Zarządzanie aplikacjami zapewnia możliwość zarządzania zabezpieczeniami i zasadami przeznaczoną dla aplikacji z obsługą protokołu OAuth, które uzyskują dostęp Microsoft 365 danych za pośrednictwem interfejsów API Graph firmy Microsoft. Ład aplikacji zapewnia pełny wgląd, korygowanie i nadzór w zakresie sposobu, w jaki te aplikacje i ich użytkownicy uzyskują dostęp, używają i udostępniają poufne dane przechowywane w Microsoft 365 za pośrednictwem praktycznych szczegółowych informacji oraz zautomatyzowanych alertów i akcji zasad. [Dowiedz się więcej na temat ładu aplikacji](/cloud-app-security/app-governance-manage-app-governance).
- (wersja zapoznawcza) Zaawansowana strona [wyszukiwania zagrożeń](advanced-hunting-overview.md) ma teraz obsługę wielu kart, inteligentne przewijanie, usprawnione karty schematu, opcje szybkiej edycji zapytań, wskaźnik użycia zasobów zapytań i inne ulepszenia ułatwiające płynne i bardziej precyzyjne wykonywanie zapytań.
- (wersja zapoznawcza) Teraz możesz użyć [linku do funkcji zdarzenia](advanced-hunting-link-to-incident.md) , aby uwzględnić zdarzenia lub rekordy z zaawansowanych wyników zapytania wyszukiwania zagrożeń bezpośrednio do nowego lub istniejącego incydentu, który badasz.

## <a name="october-2021"></a>Październik 2021

- (OGÓLNA dostępność) W przypadku zaawansowanego wyszukiwania zagrożeń w tabeli [CloudAppEvents](advanced-hunting-cloudappevents-table.md) dodano więcej kolumn. Teraz możesz dołączyć `AccountType`do zapytań wartości , `IsExternalUser`, `IsImpersonated``IPTags`, `IPCategory`i `UserAgentTags` .

## <a name="september-2021"></a>Wrzesień 2021

- (OGÓLNA dostępność) Ochrona usługi Office 365 w usłudze Microsoft Defender dane zdarzeń są dostępne w interfejsie API przesyłania strumieniowego zdarzeń Microsoft 365 Defender. Dostępność i stan typów zdarzeń można wyświetlić w [obsługiwanych typach zdarzeń Microsoft 365 Defender w interfejsie API przesyłania strumieniowego](supported-event-types.md).
- (OGÓLNA dostępność) Ochrona usługi Office 365 w usłudze Microsoft Defender dane dostępne w ramach zaawansowanego wyszukiwania zagrożeń są teraz ogólnie dostępne.
- (OGÓLNA dostępność) Przypisywanie zdarzeń i alertów do kont użytkowników

  Zdarzenie i wszystkie skojarzone z nim alerty można przypisać do konta użytkownika z obszaru **Przypisz do:** w okienku **Zarządzanie zdarzeniem** zdarzenia lub w okienku **Zarządzanie alertem** alertu.

## <a name="august-2021"></a>Sierpień 2021

- (wersja zapoznawcza) Ochrona usługi Office 365 w usłudze Microsoft Defender danych dostępnych w ramach zaawansowanego wyszukiwania zagrożeń

  Nowe kolumny w tabelach wiadomości e-mail mogą zapewnić lepszy wgląd w zagrożenia oparte na wiadomościach e-mail w celu dokładniejszego zbadania przy użyciu zaawansowanego wyszukiwania zagrożeń. Teraz możesz dołączyć kolumnę `AuthenticationDetails` w [kolumnie EmailEvents](./advanced-hunting-emailevents-table.md), `FileSize` [EmailAttachmentInfo](./advanced-hunting-emailattachmentinfo-table.md) i `ThreatTypes` `DetectionMethods` w tabelach [EmailPostDeliveryEvents](./advanced-hunting-emailpostdeliveryevents-table.md) .

- (wersja zapoznawcza) Wykres zdarzeń

  Nowa karta **Graph** na karcie **Podsumowanie** incydentu pokazuje pełny zakres ataku, sposób rozprzestrzeniania się ataku przez sieć w czasie, miejsce jego rozpoczęcia i jak daleko posunęli się atakujący.

## <a name="july-2021"></a>Lipiec 2021

- [wykaz usług Professional](https://sip.security.microsoft.com/interoperability/professional_services)

  Zwiększ możliwości wykrywania, badania i analizy zagrożeń platformy przy użyciu obsługiwanych połączeń partnerskich.

## <a name="june-2021"></a>Czerwiec 2021

- (wersja zapoznawcza) [Wyświetlanie raportów na tagi zagrożeń](threat-analytics.md#view-reports-per-threat-tags)

  Tagi zagrożeń ułatwiają skoncentrowanie się na określonych kategoriach zagrożeń i przeglądanie najbardziej odpowiednich raportów.

- (wersja zapoznawcza) [Interfejs API przesyłania strumieniowego](../defender-endpoint/raw-data-export.md)

  Microsoft 365 Defender obsługuje przesyłanie strumieniowe wszystkich zdarzeń dostępnych za pośrednictwem zaawansowanego wyszukiwania zagrożeń do konta usługi Event Hubs i/lub usługi Azure Storage.

- (wersja zapoznawcza) [Podjęcie akcji w zaawansowanym polowaniu](advanced-hunting-take-action.md)

  Szybko zawierają zagrożenia lub usuwają zagrożone zasoby, które można znaleźć w [zaawansowanym wyszukiwaniu zagrożeń](advanced-hunting-overview.md).

- (wersja zapoznawcza) [Dokumentacja schematu w portalu](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)

  Uzyskaj informacje o zaawansowanych tabelach schematów wyszukiwania zagrożeń bezpośrednio w centrum zabezpieczeń. Oprócz opisów tabel i kolumn ta dokumentacja obejmuje obsługiwane typy zdarzeń (`ActionType` wartości) i przykładowe zapytania.

- (wersja zapoznawcza) [DeviceFromIP() , funkcja](advanced-hunting-devicefromip-function.md)

  Uzyskaj informacje o tym, które urządzenia zostały przypisane do określonego adresu IP lub adresów w danym zakresie czasu.

## <a name="may-2021"></a>Maj 2021

- [Nowa strona alertu w portalu Microsoft 365 Defender](https://techcommunity.microsoft.com/t5/microsoft-365-defender/easily-find-anomalies-in-incidents-and-alerts/ba-p/2339243)

  Udostępnia rozszerzone informacje o kontekście ataku. Możesz zobaczyć, który inny wyzwolony alert spowodował bieżący alert oraz wszystkie jednostki i działania, których dotyczy atak, w tym pliki, użytkownicy i skrzynki pocztowe. Aby uzyskać więcej informacji [, zobacz Badanie alertów](/microsoft-365/security/defender/investigate-alerts) .

- [Wykres trendów dla zdarzeń i alertów w portalu Microsoft 365 Defender](https://techcommunity.microsoft.com/t5/microsoft-365-defender/new-alert-page-for-microsoft-365-defender-incident-detections/ba-p/2350425)

  Ustal, czy istnieje kilka alertów dotyczących pojedynczego incydentu lub czy twoja organizacja jest atakowana przy użyciu kilku różnych zdarzeń. Aby uzyskać więcej informacji [, zobacz Określanie priorytetów zdarzeń](/microsoft-365/security/defender/incident-queue) .

## <a name="april-2021"></a>Kwiecień 2021

- Microsoft 365 Defender

  Ulepszony portal [Microsoft 365 Defender](https://security.microsoft.com) jest teraz dostępny. To nowe środowisko łączy usługę Defender for Endpoint, Ochrona usługi Office 365 w usłudze Defender, Defender for Identity i nie tylko w jeden portal. Jest to nowy dom do zarządzania mechanizmami kontroli zabezpieczeń. [Dowiedz się, co nowego](./microsoft-365-defender.md#the-microsoft-365-defender-portal).

- [Microsoft 365 Defender raport analizy zagrożeń](threat-analytics.md)

  Analiza zagrożeń pomaga reagować i minimalizować wpływ aktywnych ataków. Możesz również dowiedzieć się więcej o próbach ataku zablokowanych przez rozwiązania Microsoft 365 Defender i podjąć działania zapobiegawcze, które zmniejszają ryzyko dalszego narażenia i zwiększają odporność. W ramach ujednoliconego środowiska zabezpieczeń analiza zagrożeń jest teraz dostępna dla Ochrona punktu końcowego w usłudze Microsoft Defender i usługi Microsoft Defender dla posiadaczy licencji Office E5.

## <a name="march-2021"></a>Marzec 2021 r.

- [Tabela CloudAppEvents](advanced-hunting-cloudappevents-table.md)

  Znajdź informacje o zdarzeniach w różnych aplikacjach i usługach w chmurze objętych Microsoft Cloud App Security. Ta tabela zawiera również informacje wcześniej dostępne w `AppFileEvents` tabeli.

