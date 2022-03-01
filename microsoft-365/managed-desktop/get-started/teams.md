---
title: Microsoft Teams
description: Jak Teams na urządzeniach i później aktualizowane
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja, aplikacje, aplikacje biznesowe, aplikacje LOB
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: ITPro
ms.openlocfilehash: 21d69770fb16ac40b25cd9ff4fefd5ccf5b2f0fb
ms.sourcegitcommit: babc2dad1c0e08a9237dbe4956ffd21c0214db83
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2022
ms.locfileid: "63013822"
---
# <a name="microsoft-teams"></a>Microsoft Teams

[Teams](https://www.microsoft.com/microsoft-365/microsoft-teams/group-chat-software) to aplikacja [do](https://support.microsoft.com/office/microsoft-teams-basics-6d5f52e6-5306-4096-ac24-c3082b79eaf0) obsługi wiadomości, która również zapewnia obszar roboczy do współpracy i komunikacji w czasie rzeczywistym, spotkań oraz udostępniania plików i aplikacji.

## <a name="initial-deployment"></a>Wdrożenie początkowe

Większość dostawców sprzętu nie dołącza jeszcze Teams w ramach obrazów. Microsoft Managed Desktop wdraża Teams na Urządzeniach przy użyciu aplikacji Microsoft Intune. Wszystkie zarządzane urządzenia mają [zainstalowany Teams .msi pakietu usługi](/MicrosoftTeams/msi-deployment#how-the-microsoft-teams-msi-package-works). Pakiet .msi zapewnia, że wszyscy użytkownicy, którzy logują się na urządzeniu, Microsoft Teams są gotowi do użycia. Po zakończeniu instalacji pakietu pakiet Teams uruchamia się automatycznie i dodaje skrót do pulpitu.

### <a name="microsoft-intune-changes"></a>Microsoft Intune zmian

Microsoft Managed Desktop dwie aplikacje do Twojej organizacji usługi Azure AD na Microsoft Teams. Są one wdrażane w klientach 64-bitowych lub 32-bitowych, odpowiednio do urządzenia:  

- Nowoczesne miejsce pracy — Teams Instalatora komputera x64  
- Nowoczesne miejsce pracy — Teams Instalatora komputera x32

## <a name="updates"></a>Aktualizacje

Teams następuje osobna ścieżka aktualizacji od Aplikacje Microsoft 365 dla przedsiębiorstw. Klient klasyczny jest aktualizowany automatycznie. Teams sprawdza aktualizacje co kilka godzin, pobiera je, a następnie czeka na bezczynny komputer przed dyskretnym zainstalowaniem aktualizacji.  

Grupa Teams produktu nie zezwala administratorom na kontrolowanie aktualizacji, więc Microsoft Managed Desktop korzysta ze [standardowego kanału aktualizacji automatycznej](/microsoftteams/teams-client-update#can-admins-deploy-updates-instead-of-teams-auto-updating).

### <a name="manually-updating-teams"></a>Ręczne aktualizowanie Teams

Poszczegłoni użytkownicy mogą również pobierać aktualizacje. W prawym górnym rogu aplikacji z listy rozwijanej Profil wybierz pozycję Sprawdź **aktualizacje**. Jeśli aktualizacja jest dostępna, zostanie pobrana i zainstalowana dyskretnie, gdy komputer będzie bezczynny.

## <a name="delivery-optimization-of-updates"></a>Optymalizacja dostarczania aktualizacji

Optymalizacja dostarczania dla Teams jest domyślnie włączona i nie wymaga żadnych działań ze strony administratorów ani użytkowników.
