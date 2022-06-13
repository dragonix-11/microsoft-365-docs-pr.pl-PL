---
title: Łączenie usługi Microsoft Defender dla Office 365 z usługą Microsoft Sentinel
description: Kroki nawiązywania połączenia Ochrona usługi Office 365 w usłudze Microsoft Defender z usługą Sentinel. Dodaj dane Ochrona usługi Office 365 w usłudze Microsoft Defender (*i* dane z pozostałej części pakietu Microsoft 365 Defender), w tym zdarzenia, do usługi Microsoft Sentinel w celu utworzenia jednego okienka szkła w zabezpieczeniach.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: dbdb4c93ea010959c8f2eae61f9add8ea853d2b1
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043749"
---
# <a name="connect-microsoft-defender-for-office-365-to-microsoft-sentinel"></a>Łączenie usługi Microsoft Defender dla Office 365 z usługą Microsoft Sentinel

Możesz pozyskiwać dane Ochrona usługi Office 365 w usłudze Microsoft Defender (*i* dane z pozostałej części pakietu Microsoft 365 Defender), w tym zdarzenia, do usługi Microsoft Sentinel.

Korzystaj z zaawansowanego zarządzania zdarzeniami informacji o zabezpieczeniach (SIEM) w połączeniu z danymi z innych źródeł Microsoft 365, synchronizacją zdarzeń i alertów oraz zaawansowanym wyszukiwaniem zagrożeń.

> [!IMPORTANT]
> Łącznik Microsoft 365 Defender jest obecnie w **wersji zapoznawczej**. Zobacz Dodatkowe warunki użytkowania dla wersji zapoznawczej Microsoft Azure, aby zapoznać się z dodatkowymi warunkami prawnymi dotyczącymi funkcji platformy Azure, które są w wersji beta, wersji zapoznawczej lub w inny sposób nie zostały jeszcze udostępnione do ogólnej dostępności.>

## <a name="what-you-will-need"></a>Co będzie potrzebne
- Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2 lub nowszy. (Uwzględnione w planach E5)
- [Przewodnik Szybki start](/azure/sentinel/quickstart-onboard) dotyczący usługi Microsoft Sentinel.
- Wystarczające uprawnienia (administrator zabezpieczeń w usłudze M365 & uprawnienia do odczytu/zapisu w usłudze Sentinel).

## <a name="add-the-microsoft-365-defender-connector"></a>Dodawanie łącznika Microsoft 365 Defender
1. [Zaloguj się do witryny Azure Portal](https://portal.azure.com) i przejdź do usługi **Microsoft Sentinel** > Wybierz odpowiedni obszar roboczy, aby łączyć się z Microsoft 365 Defender
    1. W menu nawigacji po lewej stronie pod nagłówkiem **Konfiguracja** > wybierz pozycję **Łączniki danych**.
2. Po załadowaniu strony **wyszukaj** Microsoft 365 Defender **i wybierz łącznik Microsoft 365 Defender (wersja zapoznawcza).**
3. Na wysuwnym po prawej stronie wybierz pozycję **Otwórz stronę łącznika**.
4. W sekcji **Konfiguracja** na załadowanej stronie wybierz pozycję **Połączenie zdarzenia & alerty**, pozostawiając zaznaczenie opcji Wyłącz wszystkie reguły tworzenia zdarzeń firmy Microsoft dla tych produktów.
5. Przewiń do **Ochrona usługi Office 365 w usłudze Microsoft Defender** w sekcji **zdarzenia Połączenie** strony. Wybierz **pozycje EmailEvents, EmailUrlInfo, EmailAttachmentInfo & EmailPostDeliveryEvents** , a następnie  **zastosuj zmiany** w dolnej części strony. (W tym kroku wybierz tabele z innych produktów usługi Defender, jeśli są przydatne i odpowiednie).

## <a name="next-steps"></a>Następne kroki

Administratorzy będą teraz mogli wyświetlać zdarzenia, alerty i dane pierwotne w usłudze Microsoft Sentinel i używać tych danych do *zaawansowanego wyszukiwania zagrożeń*, przestawiając istniejące i nowe dane z usługi Microsoft Defender.

## <a name="more-information"></a>Więcej informacji

[Połączenie Microsoft 365 Defender danych do usługi Microsoft Sentinel | Microsoft Docs](/azure/sentinel/connect-microsoft-365-defender?tabs=MDE)

[Połączenie Microsoft Teams do usługi Microsoft Sentinel](/microsoftteams/teams-sentinel-guide)
