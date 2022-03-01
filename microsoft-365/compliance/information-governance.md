---
title: Informacje na temat zarządzania informacjami w programie Microsoft 365
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
- m365initiative-compliance
description: Dowiedz się, co to oznacza, aby zarządzać danymi organizacji za pomocą Microsoft 365.
ms.openlocfilehash: c9661aadcef5d70b4099cb44e0fa054ab27e5562
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009555"
---
# <a name="learn-about-information-governance"></a>Informacje na temat zarządzania informacjami

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

W ramach zarządzania informacjami firmy [Microsoft](manage-information-governance.md), który [](records-management.md) obejmuje również łączniki zarządzania rekordami i [danymi, zarządzanie](archiving-third-party-data.md) informacjami z programu Microsoft 365 zapewnia narzędzia i możliwości zachowywania zawartości, która jest zachowywana i usuwana. Zachowywanie i usuwanie zawartości jest często potrzebne na potrzeby wymogów zgodności z przepisami, ale usuwanie zawartości, która nie ma już wartości biznesowej, ułatwia również zarządzanie ryzykiem i odpowiedzialnością. Na przykład ogranicza on powierzchnię ataków.

**Zasady przechowywania są** podstawowym elementem zarządzania informacjami. Są one Microsoft 365 obciążeniami pracą, które obejmują Exchange, SharePoint, OneDrive, Teams i Yammer. Skonfiguruj, czy zawartość tych usług ma być zachowywana przez nieograniczony czas, czy przez określony czas, jeśli użytkownicy ją edytują lub usuwają. Można też skonfigurować zasady w taki sposób, aby po upływie określonego okresu zawartość była automatycznie usuwana, o ile nie została jeszcze usunięta. Te dwie akcje można także połączyć, aby zachować, a następnie usunąć, co jest bardzo typową konfiguracją. Na przykład zachowaj wiadomość e-mail przez trzy lata, a następnie usuń ją.

Konfigurując zasady przechowywania, możesz kierować wszystkie wystąpienia w organizacji (na przykład wszystkie skrzynki pocztowe i wszystkie witryny SharePoint) lub pojedyncze wystąpienia (na przykład tylko skrzynki pocztowe dla określonych działów lub regionów lub tylko wybrane witryny SharePoint).

Jeśli potrzebujesz wyjątków dla poszczególnych wiadomości e-mail lub dokumentów, takich jak dłuższy okres przechowywania dokumentów prawnych, możesz to zrobić  za pomocą etykiet przechowywania publikowanych w aplikacjach, aby użytkownicy mogą je stosować, lub automatycznie stosować je przez sprawdzenie zawartości.

Aby uzyskać więcej informacji na temat zasad przechowywania i etykiet przechowywania oraz sposobu działania przechowywania w aplikacji Microsoft 365, zobacz Informacje o zasadach przechowywania [i etykietach przechowywania](retention.md). 

> [!NOTE]
> Jeśli potrzebujesz zarządzania cyklem życia elementów o wysokiej wartości w przypadku wymogów przechowywania rekordów biznesowych, prawnych lub prawnych, użyj etykiet przechowywania z zarządzaniem rekordami, a nie etykiet przechowywania za pomocą zarządzania informacjami.[](records-management.md)

Inne funkcje zarządzania informacjami, które ułatwiają zachowanie tego, czego potrzebujesz, oraz usuwanie tego, czego nie potrzebujesz:

- **Archiwizowanie skrzynek** pocztowych w celu zapewnienia użytkownikom dodatkowego miejsca do magazynowania skrzynek pocztowych oraz automatyczne rozszerzanie archiwizacji dla skrzynek pocztowych, które wymagają więcej niż 100 GB miejsca do magazynowania. Domyślne zasady archiwizacji automatycznie przesuną wiadomości e-mail do archiwalnej skrzynki pocztowej i w razie potrzeby możesz dostosować te zasady. Aby uzyskać więcej informacji na temat archiwizowania skrzynek pocztowych, zobacz [Informacje o archiwalnych skrzynkach pocztowych](archive-mailboxes.md).
    
- **Nieaktywne skrzynki** pocztowe, które zachowują zawartość skrzynki pocztowej po opuszczeniu organizacji przez pracowników. Aby uzyskać więcej informacji o nieaktywnych skrzynkach pocztowych, zobacz [Informacje o nieaktywnych skrzynkach pocztowych](inactive-mailboxes-in-office-365.md).

- **Usługa importowania plików PST przy** użyciu przekazywania sieciowego lub wysyłki dysków. Aby uzyskać więcej informacji, zobacz [Informacje o importowaniu plików PST organizacji](importing-pst-files-to-office-365.md).

## <a name="deployment-guidance"></a>Wskazówki dotyczące wdrażania

Aby uzyskać wskazówki dotyczące wdrażania dotyczące zarządzania informacjami, w tym plan wdrażania, informacje o licencjonowaniu, uprawnienia, listę obsługiwanych scenariuszy i dokumentację dla użytkowników końcowych, zobacz Wprowadzenie [do zarządzania informacjami](get-started-with-information-governance.md).

Szukasz wskazówek dotyczących wdrażania w celu ochrony danych? Zobacz [Wdrażanie Microsoft Information Protection rozwiązania](information-protection-solution.md).

