---
title: Wprowadzenie do zarządzania rekordami w Microsoft 365
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Potrzebujesz rozwiązania do zarządzania rekordami dla klientów Microsoft 365 którym można zarządzać zawartością o wysokiej wartości w związku ze zobowiązaniami prawnymi, biznesowymi lub prawnymi, ale nie masz pewności, od czego zacząć? Aby rozpocząć, przeczytaj kilka praktycznych wskazówek.
ms.openlocfilehash: ba23aed20cbef05272bc33306df5fc1eebc6cb3f
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010624"
---
# <a name="get-started-with-records-management"></a>Wprowadzenie do zarządzania rekordami

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Wszystko gotowe do rozpoczęcia zarządzania cenną zawartością swojej organizacji na potrzeby wymogów prawnych, biznesowych lub prawnych przy użyciu rozwiązania do zarządzania rekordami w ramach Microsoft 365? Aby rozpocząć, skorzystaj z następujących wskazówek:

1. **Informacje na temat sposobu** przechowywania i usuwania w programie Microsoft 365 oraz określania, czy do uzupełnienia etykiet przechowywania, które zarządzają dokumentami i wiadomościami e-mail na poziomie elementów, należy używać zasad przechowywania. Dowiedz się więcej o zasadach przechowywania i etykietach [przechowywania](retention.md).
    
    W razie potrzeby [utwórz zasady przechowywania na](create-retention-policies.md) potrzeby podstawowego zarządzania danymi Microsoft 365 obciążeniami pracą.
    
2. **Opis rozwiązania do zarządzania rekordami** i sposobu, w jaki etykiety przechowywania mogą być używane do zezwalania na akcje lub blokowania akcji deklarowanych jako rekordy w dokumentach i wiadomościach e-mail: informacje [na temat zarządzania rekordami](records-management.md)

3. **Utwórz plan** przechowywania i akcji przechowywania oraz usuwania oraz czas oznaczania elementów jako rekordów przez zaimportowanie istniejącego planu lub utworzenie nowych etykiet [przechowywania: Tworzenie](file-plan-manager.md) etykiet przechowywania i zarządzanie nimi za pomocą planu ewidencji

4. **Publikowanie i stosowanie etykiet przechowywania**. Etykiety przechowywania to bloki konstrukcyjne wielokrotnego użytku, których można używać w wielu zasadach i które można uwzględniać w przepływach pracy użytkowników:

    - [Tworzenie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md)
    - [Automatyczne stosowanie etykiety przechowywania do zawartości](apply-retention-labels-automatically.md)

Niezależnie od tej **procedury użyj** łączników do importowania i archiwizowania danych innych firm, które obejmują dane z platform społecznościowych, platform wiadomości błyskawicznych i platform współpracy nad dokumentami. Gdy te dane są importowane do skrzynek pocztowych w trybie online, obsługuje ona nie tylko zarządzanie rekordami z witryny Microsoft 365 Compliance, ale także inne rozwiązania zgodności, takie jak zgodność komunikacji, zarządzanie ryzykiem niejawnego programu testów i zbierania elektronicznych materiałów dowodowych. Aby uzyskać więcej informacji, zobacz [Informacje o łącznikach dla danych innych firm](archiving-third-party-data.md).

## <a name="subscription-and-licensing-requirements"></a>Wymagania dotyczące subskrypcji i licencjonowania

Wiele różnych subskrypcji obsługuje zarządzanie rekordami, a wymagania licencyjne użytkowników zależą od tego, z których funkcji korzystasz.

Aby wyświetlić opcje licencjonowania użytkowników w celu skorzystania z funkcji zgodności Microsoft 365, zobacz wskazówki Microsoft 365 dotyczące licencjonowania w zakresie zabezpieczeń [& zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). Aby uzyskać informacje na temat zarządzania rekordami, zobacz [sekcję Zarządzanie](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#records-management) rekordami i powiązany plik PDF do pobrania, aby uzyskać informacje o wymaganiach licencyjnych na poziomie funkcji.

## <a name="permissions"></a>Uprawnienia

Członkowie Twojego zespołu zgodności, którzy są odpowiedzialni za zarządzanie rekordami, potrzebują uprawnień do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a>. Domyślnie administrator dzierżawy (administrator globalny) ma dostęp do tej lokalizacji i może udzielać służbom zgodności z przepisami i innym osobom dostępu bez nadawania im wszystkich uprawnień administratora dzierżawy. Aby przyznać uprawnienia dla tej ograniczonej administracji, zalecamy dodanie użytkowników do grupy ról  administratorów zarządzania rekordami, która udziela uprawnień dla wszystkich funkcji związanych z zarządzaniem rekordami, w tym recenzji i weryfikacji ich rozsyłania.[](disposition.md)

W przypadku roli tylko do odczytu możesz utworzyć nową grupę ról i dodać do tej grupy rolę **Zarządzanie** rekordami tylko do odczytu.

Aby uzyskać instrukcje dotyczące dodawania użytkowników do ról domyślnych lub tworzenia własnych grup ról, zobacz Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md).

Te uprawnienia są wymagane tylko do tworzenia, konfigurowania i stosowania etykiet przechowywania, które deklarują rekordy i zarządzają nimi. Osoba konfigurująca te etykiety nie wymaga dostępu do zawartości.

## <a name="common-scenarios"></a>Typowe scenariusze

Skorzystaj z poniższej tabeli, aby ułatwić zamapowanie wymagań biznesowych na scenariusze obsługiwane przez zarządzanie rekordami.

> [!TIP]
> Chcesz przestrzegać konkretnego rozporządzenia branżowego? Aby [uzyskać wskazówki dotyczące poszczególnych przepisów,](retention-regulatory-requirements.md) należy sprawdzić wymagania prawne dotyczące zarządzania informacjami i zarządzania rekordami.

|Chcę...|Dokumentacja|
|----------------|---------------|
|Deklarowanie rekordu |[Deklarowanie rekordów przy użyciu etykiet przechowywania](declare-records.md)|
|Aktualizowanie rekordu |[Używanie przechowywania wersji rekordów do aktualizowania rekordów przechowywanych w SharePoint lub OneDrive](record-versioning.md)|
|Pozwól administratorom i użytkownikom na ręczne stosowanie akcji zachowywania i usuwania w dokumentach i wiadomościach e-mail: <br />— SharePoint <br />— OneDrive <br />— Outlook i Outlook w sieci Web|[Tworzenie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md)|
|Umożliwianie administratorom witryny ustawienia domyślnego zachowywania i usuwania akcji dla całej zawartości SharePoint, folderu lub zestawu dokumentów|[Tworzenie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md)|
|Umożliwianie użytkownikom automatycznego stosowania akcji zachowywania i usuwania do wiadomości e-mail przy użyciu Outlook e-mail|[Tworzenie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md)|
|Pozwól administratorom na zachowywanie i usuwanie akcji w modelu zrozumienia dokumentu, aby były one automatycznie stosowane do dokumentów oznaczonych w bibliotece dokumentów SharePoint dokumentach|[Tworzenie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md)|
|Automatyczne stosowanie akcji zachowywania i usuwania do dokumentów i wiadomości e-mail |[Automatyczne stosowanie etykiety przechowywania do zawartości](apply-retention-labels-automatically.md)|
|Okres przechowywania rozpoczyna się w przypadku wystąpienia zdarzenia, takiego jak:  <br />- Pracownicy opuszczają organizację <br />- Wygasają umowy <br />- Koniec okresu ważności produktu| [Rozpoczynanie przechowywania w przypadku wystąpienia zdarzenia](event-driven-retention.md)|
|Ograniczanie zmian do zasad w celu spełnienia wymagań prawnych lub zabezpieczenia przed administratorami zbędnych| [Używanie blokady zachowywania w celu ograniczenia zmian zasad przechowywania i zasad etykiet przechowywania](retention-preservation-lock.md)
|Zarządzanie cyklem życia różnych typów dokumentów w programie SharePoint| [Używanie etykiet przechowywania do zarządzania cyklem życia dokumentów przechowywanych w SharePoint](auto-apply-retention-labels-scenario.md)|
|Upewniaj się, że ktoś przegląda i zatwierdza przed usunięciem zawartości po zakończeniu okresu przechowywania|[Recenzje rozsyłania](disposition.md#disposition-reviews) |
|Mają dowód usunięcia zawartości, która jest trwale usuwana po zakończeniu okresu przechowywania|[Disposition of records](disposition.md#disposition-of-records) |
| Monitorowanie sposobu oraz miejsca stosowania ustawień zachowywania i usuwania do elementów | [Monitorowanie etykiet przechowywania](retention.md#monitoring-retention-labels) |

## <a name="end-user-documentation"></a>Dokumentacja użytkownika końcowego

Jeśli używasz zasad przechowywania na potrzeby zarządzania danymi bazowymi, zwykle działają one w tle w dyskretny sposób, bez interakcji z użytkownikami. W wyniku tego potrzebują oni małej dokumentacji dla użytkowników. Zasady przechowywania dla Teams informują użytkowników o usunięciu ich wiadomości oraz link [Teams dotyczące zasad przechowywania](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

Dla porównania etykiety przechowywania zawierają informacje o interfejsie użytkownika w aplikacjach pakietu Microsoft 365, dlatego przed wdrożeniem tych etykiet w sieci produkcyjnej należy podać wskazówki dla użytkowników końcowych i pomocy technicznej. Aby ułatwić użytkownikom stosowanie etykiet przechowywania w SharePoint i OneDrive, a także informacje o odblokowywaniu rekordów do edycji, zobacz Stosowanie etykiet przechowywania do plików w SharePoint lub [OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df).

Jednak najbardziej skuteczną dokumentacją użytkownika końcowego będą dostosowane wskazówki i instrukcje dotyczące wybieranych nazw etykiet przechowywania i konfiguracji. Zobacz następującą stronę i materiały do pobrania, których możesz użyć w celu przeszkolenia użytkowników: Szkolenia dla użytkowników [końcowych dotyczące etykiet przechowywania](https://microsoft.github.io/ComplianceCxE/enduser/retention/).
