---
title: Jak obsługiwane są aktualizacje w Microsoft Managed Desktop
description: Zapewnienie Microsoft Managed Desktop na bieżąco jest równoważną szybkością i stabilnością.
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: bf6ead692a82d485f6a8e3b3148bc05484c887a8
ms.sourcegitcommit: 9f0e84835121ce6228fdc69182c24be7ad1cb20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63014880"
---
# <a name="how-updates-are-handled-in-microsoft-managed-desktop"></a>Jak obsługiwane są aktualizacje w Microsoft Managed Desktop

<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/update-rings); do not delete.-->

<!--Update management -->

Microsoft Managed Desktop wszystkie urządzenia z nowoczesną infrastrukturą opartą na chmurze.

Zapewnienie Windows, Office, sterowników, oprogramowania układowego i Microsoft Store dla Firm oprogramowania układowego jest równoważyć szybkość i stabilność aplikacji. Grupy aktualizacji mają na celu zapewnienie bezpiecznego stosowania aktualizacji i zasad systemu operacyjnego. Aby uzyskać więcej informacji, zobacz klip wideo[, w Microsoft Managed Desktop Proces zmiany i wydania](https://www.microsoft.com/videoplayer/embed/RE4mWqP).

Aktualizacje wydane przez firmę Microsoft są zbiorcze i są klasyfikowane jako aktualizacje jakości lub funkcji. Aby uzyskać więcej informacji, [zobacz Windows: Typy aktualizacji dla firm](/windows/deployment/update/waas-manage-updates-wufb#update-types).

## <a name="update-groups"></a>Aktualizowanie grup

Microsoft Managed Desktop do zarządzania aktualizacjami są używane cztery grupy usługi Azure AD:

| Grupa | Opis |
| ------ | ------ |
| Test | Służy do sprawdzania Microsoft Managed Desktop zmian zasad, aktualizacji systemu operacyjnego, aktualizacji funkcji i innych zmian wypychanych do organizacji usługi Azure AD ("dzierżawa"). Grupa Test to: <br><ul><li>Najlepsze rozwiązanie do testowania lub dla użytkowników, którzy mogą przekazać wczesne opinie.</li><li>Wykluczona ze wszystkich ustalonych umów dotyczących poziomu usług i pomocy technicznej dla użytkowników.</li><li>Dostępne do sprawdzania zgodności aplikacji z nowymi zasadami lub zmianami systemu operacyjnego.</li></ul> |
| Pierwszy | Zawiera wczesnych użytkowników oprogramowania i urządzenia, które mogą podlegać aktualizacjom w wersji wstępnej. <br><br> Urządzenia w tej grupie mogą doświadczać awarii, jeśli istnieją scenariusze, które nie zostały uwzględnione podczas testowania w pierścieniu testowania. |
| Szybkie | Priorytetyzowanie szybkości nad stabilnością. Grupa Szybkie tempo to: <br><ul><li>Przydaje się do wykrywania problemów z jakością, zanim będą oferowane do grupy Broad.</li> <li>Następna warstwa sprawdzania poprawności, która jest zwykle bardziej stabilna niż grupy Test i Pierwsze.</li></ul> |
| Broad | Jest to ostatnia grupa, w przypadku których dostępne są aktualizacje funkcji i jakości. <br><br> Grupa Broad zawiera większość użytkowników w organizacji usługi Azure AD i dlatego ma przysługę stabilności nad szybkością wdrażania. W tej grupie należy testować aplikacje, ponieważ środowisko jest najbardziej stabilne. |

### <a name="moving-devices-between-update-groups"></a>Przenoszenie urządzeń między grupami aktualizacji

Być może chcesz, aby niektóre urządzenia otrzymywać aktualizacje jako ostatnie, a jeszcze inne, które najpierw chcesz otrzymywać. Aby przenieść te urządzenia do odpowiedniej grupy aktualizacji, zobacz [Przypisywanie urządzeń do grupy wdrażania](../working-with-managed-desktop/assign-deployment-group.md).

Aby uzyskać więcej informacji na temat ról i obowiązków w tych grupach wdrożeniowych, [zobacz Microsoft Managed Desktop Role i obowiązki.](../intro/roles-and-responsibilities.md)

### <a name="using-microsoft-managed-desktop-update-groups"></a>Korzystanie Microsoft Managed Desktop grup aktualizacji

Istnieją części usługi, które zarządzasz, takie jak wdrażanie aplikacji, w przypadku których może być konieczne kierowanie wszystkich urządzeń zarządzanych.

## <a name="update-deployment"></a>Aktualizowanie wdrożenia

Poniżej opisano działanie wdrażania aktualizacji.

| Krok | Opis |
| ------ | ------ |
| Krok 1 | Microsoft Managed Desktop nowej funkcji lub aktualizacji jakości zgodnie z harmonogramem określonym w poniższej tabeli.|
| Krok 2 | Podczas wdrażania Microsoft Managed Desktop monitory pod kątem znaków awarii lub zakłóceń w pracy ze względu na dane diagnostyczne i system pomocy technicznej użytkownika. Jeśli zostaną wykryte jakiekolwiek zmiany, natychmiast wstrzymamy wdrożenie dla wszystkich bieżących i przyszłych grup.<br><br> Jeśli na przykład zostanie wykryty problem podczas wdrażania aktualizacji jakości w pierwszej grupie, wówczas należy wstrzymać wdrażanie do grup Pierwsze, Szybkie i Ogólne, dopóki problem nie zostanie zminimalizowany. <br><br> Problemy ze zgodnością można zgłaszać, zgłaszac zgłoszenie w portalu Microsoft Managed Desktop administracyjnego. <br><br> Aktualizacje funkcji i jakości są wstrzymywane niezależnie. Wstrzymanie jest domyślnie włączone przez 35 dni. Jednak można go zmniejszyć lub rozszerzyć w zależności od tego, czy problem został zminimalizowany. |
| Krok 3 | Gdy grupy nie zostaną przywrócone, wdrożenie zostanie wznowione zgodnie z harmonogramem w tabeli. |
| Krok 4| Użytkownicy mogą odpowiadać na powiadomienia o ponownym uruchomieniu przez określony czas. Ten okres jest nazywany terminem ostatecznego i jest mierzony w mierzony sposób od czasu, w którym aktualizacja jest oferowana dla urządzenia. <br><br> W tym czasie urządzenie będzie automatycznie ponownie uruchamiane tylko poza godzinami aktywnego działania. Po upływie tego okresu termin ostateczny zostanie osiągnięty i urządzenie zostanie uruchomione ponownie przy następnej dostępnej szansie sprzedaży, niezależnie od godzin aktywnego działania. <br><br> Termin aktualizacji jakości wynosi trzy dni. aktualizacje funkcji za pięć dni. |

> [!NOTE]
> Ten proces wdrażania dotyczy aktualizacji funkcji i jakości, ale osie czasu różnią się w zależności od nich.

## <a name="deployment-settings"></a>Ustawienia wdrożenia

Zaktualizuj ustawienia wdrażania wymienione poniżej:

| Typ aktualizacji | Test | Pierwszy | Szybkie | Broad |
| ------ | ------ | ------ | ------ | ------ |
| Aktualizacje jakości dla systemu operacyjnego | Zero dni | Zero dni | Zero dni | Siedem dni |
| Aktualizacje funkcji systemu operacyjnego | Zero dni | 30 dni | 60 dni | 90 dni |
| Sterowniki/oprogramowanie układowe | Jest zgodny z harmonogramem aktualizacji jakości. | Jest zgodny z harmonogramem aktualizacji jakości. | Jest zgodny z harmonogramem aktualizacji jakości. | Jest zgodny z harmonogramem aktualizacji jakości. |
| Definicja oprogramowania antywirusowego | Zaktualizowano przy każdym skanie. | Zaktualizowano przy każdym skanie. | Zaktualizowano przy każdym skanie. | Zaktualizowano przy każdym skanie. |
| Aplikacje Microsoft 365 dla Enterprise | [Dowiedz się więcej](../get-started/m365-apps.md#updates-to-microsoft-365-apps) | [Dowiedz się więcej](../get-started/m365-apps.md#updates-to-microsoft-365-apps) | [Dowiedz się więcej](../get-started/m365-apps.md#updates-to-microsoft-365-apps) | [Dowiedz się więcej](../get-started/m365-apps.md#updates-to-microsoft-365-apps) |
| Microsoft Edge | [Dowiedz się więcej](../get-started/edge-browser-app.md#updates-to-microsoft-edge) | [Dowiedz się więcej](../get-started/edge-browser-app.md#updates-to-microsoft-edge) | [Dowiedz się więcej](../get-started/edge-browser-app.md#updates-to-microsoft-edge) | [Dowiedz się więcej](../get-started/edge-browser-app.md#updates-to-microsoft-edge) |
| Microsoft Teams | [Dowiedz się więcej](../get-started/teams.md#updates) | [Dowiedz się więcej](../get-started/teams.md#updates) | [Dowiedz się więcej](../get-started/teams.md#updates) | [Dowiedz się więcej](../get-started/teams.md#updates) |

>[!NOTE]
>Te okresy odroczenia są celowo zaprojektowane w celu zapewnienia wszystkim użytkownikom najwyższych standardów zabezpieczeń i wydajności.<br><br> Na podstawie danych zebranych ze wszystkich urządzeń pakietu Microsoft Managed Desktop i różnych zakresów i wpływu aktualizacji program Microsoft Managed Desktop zastrzega sobie elastyczność modyfikowania czasu trwania powyższych okresów odroczenia dla wszystkich grup wdrożeniowych w sposób doraźny.
>
>Microsoft Managed Desktop przeprowadza niezależną ocenę każdej wersji funkcji Windows, aby ocenić jej konieczność i przydatność dla zarządzanych dzierżaw. W rezultacie Microsoft Managed Desktop aktualizacje funkcji mogą być Windows lub nie.

## <a name="windows-insider-program"></a>Windows niejawnego programu testów

Microsoft Managed Desktop nie obsługuje urządzeń, które są częścią niejawnego Windows niejawnego programu testów.

Niejawny Windows testów służy do sprawdzania poprawności wersji wstępnej Windows oprogramowania. Jest przeznaczona dla urządzeń, które nie są krytyczne. Jest to ważna inicjatywa firmy Microsoft, ale nie jest przeznaczona do szerokiego wdrożenia w środowiskach produkcyjnych.

Wszystkie urządzenia z kompilacjami niejawnego programu Windows niejawnego programu testów mogą zostać wprowadzone do grupy Test. Te urządzenia będą wykluczone z umów dotyczących poziomu usług i obsługi użytkowników z Microsoft Managed Desktop.

## <a name="bandwidth-management"></a>Zarządzanie przepustowością

Używamy [optymalizacji dostarczania](/windows/deployment/update/waas-delivery-optimization) dla wszystkich aktualizacji systemu operacyjnego i sterowników. Optymalizacja dostarczania minimalizuje rozmiar pobierania z usługi Windows aktualizującej, szukając aktualizacji od współpracowników w sieci firmowej.
