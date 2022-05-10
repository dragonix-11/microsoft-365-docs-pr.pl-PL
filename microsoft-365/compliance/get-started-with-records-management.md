---
title: Wprowadzenie z zarządzaniem rekordami w Microsoft 365
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
description: Potrzebujesz rozwiązania do zarządzania rekordami dla Microsoft 365, które zarządza zawartością o wysokiej wartości dla zobowiązań prawnych, biznesowych lub regulacyjnych, ale nie wiesz, od czego zacząć? Zapoznaj się z praktycznymi wskazówkami, aby rozpocząć pracę.
ms.openlocfilehash: 86d6f21963b33fde59cb498868b8ecec315e1ad8
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286785"
---
# <a name="get-started-with-records-management"></a>Wprowadzenie do zarządzania rekordami

>*[Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Chcesz rozpocząć zarządzanie zawartością o wysokiej wartości organizacji na potrzeby zobowiązań prawnych, biznesowych lub regulacyjnych przy użyciu rozwiązania do zarządzania rekordami w Microsoft 365? Aby rozpocząć pracę, skorzystaj z poniższych wskazówek:

1. **Dowiedz się, jak działa przechowywanie i usuwanie** w Microsoft 365 i określ, czy należy użyć zasad przechowywania w celu uzupełnienia etykiet przechowywania, które zarządzają dokumentami i wiadomościami e-mail na poziomie elementu: [Informacje o zasadach przechowywania i etykietach przechowywania](retention.md)
    
    W razie potrzeby [utwórz zasady przechowywania](create-retention-policies.md) dla podstawowego ładu danych w ramach obciążeń Microsoft 365.
    
2. **Omówienie rozwiązania do zarządzania rekordami** oraz sposobu, w jaki etykiety przechowywania mogą być używane do zezwalania na akcje lub blokowania, gdy dokumenty i wiadomości e-mail są deklarowane jako rekordy: [Informacje o zarządzaniu rekordami](records-management.md)

3. **Utwórz plan plików na potrzeby ustawień i akcji przechowywania i usuwania oraz określa, kiedy elementy powinny być oznaczone jako rekordy** , importując istniejący plan, jeśli go masz, lub utwórz nowe etykiety przechowywania: [Użyj planu pliku do tworzenia etykiet przechowywania i zarządzania nimi](file-plan-manager.md)

4. **Publikowanie i stosowanie etykiet przechowywania**. Etykiety przechowywania to bloki konstrukcyjne wielokrotnego użytku, które mogą być używane w wielu zasadach i mogą być włączone do przepływów pracy użytkowników:

    - [Publikowanie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md)
    - [Automatyczne stosowanie etykiety przechowywania do zawartości](apply-retention-labels-automatically.md)

## <a name="subscription-and-licensing-requirements"></a>Wymagania dotyczące subskrypcji i licencjonowania

Wiele różnych subskrypcji obsługuje zarządzanie rekordami, a wymagania licencyjne dla użytkowników zależą od używanych funkcji.

Aby wyświetlić opcje licencjonowania użytkowników w celu skorzystania z funkcji usługi Microsoft Purview, zobacz [wskazówki dotyczące licencjonowania Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). Aby uzyskać informacje na temat zarządzania rekordami, zobacz sekcję [Zarządzanie rekordami usługi Microsoft Purview](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-records-management) i powiązane pobieranie plików PDF, aby uzyskać informacje o wymaganiach dotyczących licencjonowania na poziomie funkcji.

## <a name="permissions"></a>Uprawnienia

Członkowie zespołu ds. zgodności odpowiedzialnego za zarządzanie rekordami potrzebują uprawnień do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portalu zgodności usługi Microsoft Purview</a>. Domyślnie administrator dzierżawy (administrator globalny) ma dostęp do tej lokalizacji i może udzielić urzędnikom zgodności i innym osobom dostępu bez udzielania im wszystkich uprawnień administratora dzierżawy. Aby udzielić uprawnień dla tej ograniczonej administracji, zalecamy dodanie użytkowników do grupy ról **administratora zarządzania rekordami** , która udziela uprawnień do wszystkich funkcji związanych z zarządzaniem rekordami, w tym [przeglądu dyspozycji i weryfikacji](disposition.md).

W przypadku roli tylko do odczytu można utworzyć nową grupę ról i dodać rolę **Zarządzanie rekordami tylko do widoku** do tej grupy.

Aby uzyskać instrukcje dotyczące dodawania użytkowników do ról domyślnych lub tworzenia własnych grup ról, zobacz [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md).

Te uprawnienia są wymagane tylko do tworzenia, konfigurowania i stosowania etykiet przechowywania, które deklarują rekordy i zarządzają dyspozycją. Osoba konfigurująca te etykiety nie wymaga dostępu do zawartości.

## <a name="common-scenarios"></a>Typowe scenariusze

Poniższa tabela ułatwia mapowanie wymagań biznesowych na scenariusze obsługiwane przez zarządzanie rekordami.

> [!TIP]
> Czy należy przestrzegać określonych przepisów branżowych? Zapoznaj się z [wymaganiami prawnymi dotyczącymi zarządzania cyklem życia danych i zarządzania rekordami](retention-regulatory-requirements.md) , aby uzyskać wskazówki specyficzne dla regulacji.

|Chcę...|Dokumentacji|
|----------------|---------------|
|Deklarowanie rekordu |[Deklaruj rekordy przy użyciu etykiet przechowywania](declare-records.md)|
|Aktualizowanie rekordu |[Aktualizowanie rekordów przechowywanych w SharePoint lub OneDrive przy użyciu wersji rekordów](record-versioning.md)|
|Zezwalaj administratorom i użytkownikom na ręczne stosowanie akcji zachowywania i usuwania dokumentów i wiadomości e-mail: <br />- SharePoint <br />- OneDrive <br />- Outlook i Outlook w sieci Web|[Publikowanie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md)|
|Zezwalaj administratorom witryny na ustawianie domyślnych akcji zachowywania i usuwania całej zawartości w bibliotece SharePoint, folderze lub zestawie dokumentów|[Publikowanie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md)|
|Zezwalaj użytkownikom na automatyczne stosowanie akcji zachowywania i usuwania wiadomości e-mail przy użyciu reguł Outlook|[Publikowanie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md)|
|Zezwalaj administratorom na stosowanie akcji zachowywania i usuwania do modelu interpretacji dokumentów, tak aby były one automatycznie stosowane do zidentyfikowanych dokumentów w bibliotece SharePoint|[Publikowanie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md)|
|Automatyczne stosowanie akcji zachowywania i usuwania do dokumentów i wiadomości e-mail |[Automatyczne stosowanie etykiety przechowywania do zawartości](apply-retention-labels-automatically.md)|
|Rozpocznij okres przechowywania, gdy wystąpi zdarzenie, na przykład:  <br />— Pracownicy opuszczają organizację <br />- Kontrakty wygasają <br />— Koniec okresu istnienia produktu| [Rozpocznij przechowywanie po wystąpieniu zdarzenia](event-driven-retention.md)|
|Ograniczanie zmian zasad w celu spełnienia wymagań prawnych lub ochrony przed nieautoryzowanymi administratorami| [Używanie blokady zachowania w celu ograniczenia zmian zasad przechowywania i zasad etykiet przechowywania](retention-preservation-lock.md)
|Zarządzanie cyklem życia różnych typów dokumentów w SharePoint| [Używanie etykiet przechowywania do zarządzania cyklem życia dokumentów przechowywanych w SharePoint](auto-apply-retention-labels-scenario.md)|
|Zastosuj etykietę przechowywania do pliku, gdy otrzymuję alert informujący o tym, że zawartość zawierająca dane osobowe jest przechowywana lub pozostaje nietknięta przez zbyt długi czas| [Badanie i korygowanie alertów w usłudze Privacy Risk Management](/privacy/priva/risk-management-alerts)|
|Upewnij się, że ktoś przegląda i zatwierdza zawartość, zanim zawartość zostanie usunięta po zakończeniu okresu przechowywania|[Przeglądy dyspozycji](disposition.md#disposition-reviews) |
|Posiadaj dowód dyspozycji dla zawartości, która została trwale usunięta po zakończeniu okresu przechowywania|[Dyspozycja rekordów](disposition.md#disposition-of-records) |
| Monitorowanie sposobu i miejsca stosowania ustawień zachowywania i usuwania do elementów | [Monitorowanie etykiet przechowywania](retention.md#monitoring-retention-labels) |

## <a name="end-user-documentation"></a>Dokumentacja użytkownika końcowego

Jeśli używasz zasad przechowywania na potrzeby nadzoru nad danymi według planu bazowego, zazwyczaj działają one dyskretnie w tle bez interakcji z użytkownikiem. W związku z tym użytkownicy potrzebują niewielkiej dokumentacji. Zasady przechowywania dla Teams informują użytkowników o usunięciu ich komunikatów za pomocą linku do [Teams komunikatów dotyczących zasad przechowywania](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

Dla porównania etykiety przechowywania mają interfejs użytkownika w aplikacjach Microsoft 365, dlatego przed wdrożeniem tych etykiet w sieci produkcyjnej należy podać wskazówki dla użytkowników końcowych i działu pomocy technicznej. Aby ułatwić użytkownikom stosowanie etykiet przechowywania w SharePoint i OneDrive oraz informacje dotyczące odblokowywania rekordów do edycji, zobacz [Stosowanie etykiet przechowywania do plików w SharePoint lub OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df).

Jednak najbardziej efektywną dokumentacją użytkownika końcowego będą dostosowane wskazówki i instrukcje podane dla wybranych nazw etykiet przechowywania i konfiguracji. Zobacz następującą stronę i pliki do pobrania, których możesz użyć, aby pomóc w szkoleniu użytkowników: [Szkolenie użytkowników końcowych dla etykiet przechowywania](https://microsoft.github.io/ComplianceCxE/enduser/retention/).
