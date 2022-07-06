---
title: Dowiedz się więcej o zarządzanie cyklem życia danych Microsoft Purview
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
description: Dowiedz się, jak zarządzanie cyklem życia danych Microsoft Purview pomaga zachować to, czego potrzebujesz, i usunąć to, czego nie potrzebujesz.
ms.openlocfilehash: d783ef7f97b45f21f6c90f2aa0230120634abd93
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624404"
---
# <a name="learn-about-data-lifecycle-management"></a>Dowiedz się więcej o zarządzaniu cyklem życia danych

>*[Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

zarządzanie cyklem życia danych Microsoft Purview (dawniej Microsoft Information Governance) udostępnia narzędzia i możliwości przechowywania zawartości, które należy przechowywać, oraz usuwania zawartości, której nie chcesz przechowywać. Przechowywanie i usuwanie zawartości jest często potrzebne do zapewnienia zgodności i wymagań prawnych, ale usunięcie zawartości, która nie ma już wartości biznesowej, pomaga również zarządzać ryzykiem i odpowiedzialnością. Na przykład zmniejsza to obszar ataków.

**Zasady przechowywania** są podstawą zarządzania cyklem życia danych. Użyj tych zasad dla obciążeń platformy Microsoft 365, które obejmują programy Exchange, SharePoint, OneDrive, Teams i Yammer. Skonfiguruj, czy zawartość tych usług musi być przechowywana przez czas nieokreślony, czy przez określony czas, jeśli użytkownicy ją edytują lub usuwają. Możesz też skonfigurować zasady do automatycznego trwałego usuwania zawartości po określonym okresie, jeśli nie została ona jeszcze usunięta. Można również połączyć te dwie akcje w celu zachowania, a następnie usunięcia, co jest bardzo typową konfiguracją. Na przykład zachowaj pocztę e-mail przez trzy lata, a następnie usuń ją.

Podczas konfigurowania zasad przechowywania można kierować wszystkie wystąpienia w organizacji (takie jak wszystkie skrzynki pocztowe i wszystkie witryny programu SharePoint) lub pojedyncze wystąpienia (takie jak tylko skrzynki pocztowe dla określonych działów lub regionów lub po prostu wybrane witryny programu SharePoint).

Jeśli potrzebujesz wyjątków dla poszczególnych wiadomości e-mail lub dokumentów, takich jak dłuższy okres przechowywania dokumentów prawnych, możesz to zrobić za pomocą **etykiet przechowywania** publikowanych w aplikacjach, aby użytkownicy mogli je zastosować lub automatycznie zastosować, sprawdzając zawartość.

Aby uzyskać więcej informacji na temat zasad przechowywania i etykiet przechowywania oraz sposobu działania przechowywania w usłudze Microsoft 365, zobacz [Informacje o zasadach przechowywania i etykietach przechowywania](retention.md). 

> [!NOTE]
> Jeśli musisz zarządzać elementami o wysokiej wartości dla wymagań biznesowych, prawnych lub regulacyjnych, użyj etykiet przechowywania z [zarządzaniem rekordami](records-management.md) , a nie etykietami przechowywania z zarządzaniem cyklem życia danych.

Inne możliwości zarządzania cyklem życia danych, które ułatwiają zachowanie potrzebnych danych i usuwanie tego, czego nie potrzebujesz:

- **Archiwizowanie skrzynek pocztowych** w celu zapewnienia użytkownikom dodatkowego miejsca do magazynowania skrzynki pocztowej oraz automatyczne rozszerzanie archiwizacji skrzynek pocztowych, które wymagają więcej niż 100 GB miejsca. Domyślne zasady archiwizacji automatycznie przenosi wiadomość e-mail do skrzynki pocztowej archiwum, a w razie potrzeby można dostosować te zasady. Aby uzyskać więcej informacji na temat archiwizacji skrzynek pocztowych, zobacz [Dowiedz się więcej o archiwalnych skrzynkach pocztowych](archive-mailboxes.md).
    
- **Nieaktywne skrzynki pocztowe** , które zachowują zawartość skrzynki pocztowej po opuszczeniu organizacji przez pracowników. Aby uzyskać więcej informacji na temat nieaktywnych skrzynek pocztowych, zobacz [Dowiedz się więcej o nieaktywnych skrzynkach pocztowych](inactive-mailboxes-in-office-365.md).

- **Zaimportuj usługę dla plików PST** przy użyciu przekazywania sieci lub wysyłania dysków. Aby uzyskać więcej informacji, zobacz [Temat Importowanie plików PST organizacji](importing-pst-files-to-office-365.md).

## <a name="deployment-guidance"></a>Wskazówki dotyczące wdrażania

Aby uzyskać wskazówki dotyczące wdrażania zarządzania cyklem życia danych, które obejmują zalecany plan wdrożenia, informacje o licencjonowaniu, uprawnienia, listę obsługiwanych scenariuszy i dokumentację użytkownika końcowego, zobacz [Wprowadzenie do zarządzania cyklem życia danych](get-started-with-information-governance.md).

Szukasz wskazówek dotyczących wdrażania w celu ochrony danych? Zobacz [Wdrażanie rozwiązania do ochrony informacji za pomocą usługi Microsoft Purview](information-protection-solution.md).

