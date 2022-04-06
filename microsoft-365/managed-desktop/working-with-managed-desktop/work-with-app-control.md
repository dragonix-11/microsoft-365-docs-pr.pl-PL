---
title: Praca z kontrolką aplikacji
description: Dowiedz się, jak zarządzać kontrolą aplikacji.
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: 99979a08a67245d471b33ce26e4b7f35790fead5
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569914"
---
# <a name="work-with-app-control"></a>Praca z kontrolką aplikacji

Po wdrożeniu kontroli aplikacji w środowisku zarówno Ty, jak i Microsoft Managed Desktop mają bieżące obowiązki. Na przykład możesz zechcieć dodać nową aplikację w środowisku lub dodać (lub usunąć) zaufanego podpisatora. Aby zwiększyć bezpieczeństwo, przed ich zwolnieniem dla użytkowników wszystkie aplikacje powinny zostać podpisane kodem. Szczegóły wydawcy aplikacji zawierają informacje o podpisie.

## <a name="add-a-new-app"></a>Dodawanie nowej aplikacji

**Aby dodać nową aplikację:**

1. Dodaj aplikację do [Microsoft Intune](/mem/intune/apps/apps-win32-app-management).
1. Wdeksuj aplikację na dowolnym urządzeniu w pierścieniu testowania.
1. Przetestuj aplikację zgodnie ze standardowymi procesami biznesowymi.
1. Sprawdź Podgląd zdarzeń w obszarze **Dzienniki aplikacji i usług\Microsoft\Windows\AppLocker**. Poszukaj dowolnych **zdarzeń 8003** lub **8006** . Te zdarzenia wskazują, że aplikacja zostałaby zablokowana. Aby uzyskać więcej informacji na temat wszystkich zdarzeń funkcji App Locker i ich znaczenia, zobacz Używanie funkcji Podgląd zdarzeń [z funkcją AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/using-event-viewer-with-applocker).
1. Jeśli znajdziesz dowolne z tych zdarzeń, otwórz żądanie osoby podpiszcej za pomocą Microsoft Managed Desktop operacji.

## <a name="add-or-remove-a-trusted-signer"></a>Dodawanie (lub usuwanie) zaufanej podpisatora

Po otwarciu wniosku o podpis, musisz najpierw podać niektóre ważne szczegóły dotyczące wydawcy.

**Aby dodać (lub usunąć) zaufanego podpisatora:**

1. [Zbierz szczegóły wydawcy](#gather-publisher-details).
1. Otwórz bilet z operacyjną Microsoft Managed Desktop, aby poprosić o regułę podpisacza i uwzględnić następujące szczegóły:  
    - Nazwa aplikacji
    - Wersja aplikacji
    - Opis
    - Zmień typ ("dodaj" lub "usuń")  
    - Publisher szczegóły (na przykład: `O=<publisher name>,L=<location>,S=State,C=Country`)

> [!NOTE]
> Aby usunąć zaufanie dla aplikacji, wykonaj te same czynności, ale ustaw **typ zmiany w** celu *usunięcia*.

Operacje będą stopniowo wdrażać zasady w grupach wdrożeń zgodnie z tym harmonogramem:

|Grupa Wdrażania|Typ zasad|Chronometraż|
|---|---|---|
|Test|Inspekcja|Dzień 0|
|Pierwszy|Wymuszone|Dzień 1|
|Szybkie|Wymuszone|Dzień 2|
|Broad|Wymuszone|Dzień 3|

W dowolnym momencie w trakcie wdrażania możesz wstrzymać lub wycofać wdrożenie. Aby wstrzymać lub wycofać wniosek o pomoc techniczną, otwórz kolejny wniosek o pomoc techniczną Microsoft Managed Desktop operacje.

> [!NOTE]
> Jeśli wstrzymasz wydanie reguły podpiszcej, ta reguła musi zostać wycofana lub ukończona, zanim będzie można rozpocząć kolejne rozpoczęcie.

## <a name="gather-publisher-details"></a>Gromadzenie szczegółów wydawcy

**Aby uzyskać dostęp do danych wydawcy dla aplikacji:**

1. Znajdź urządzenie Microsoft Managed Desktop w pierścieniu testowania z zastosowanymi zasadami trybu inspekcji.
1. Spróbuj zainstalować aplikację na urządzeniu.
1. Otwórz Podgląd zdarzeń na tym urządzeniu.
1. W witrynie Podgląd zdarzeń do folderu Dzienniki aplikacji i usług **\Microsoft\Windows**, a następnie wybierz pozycję **AppLocker**.
1. Znajdź dowolne **zdarzenie 8003** lub **8006** , a następnie skopiuj informacje z tego zdarzenia:
    - Nazwa aplikacji
    - Wersja aplikacji
    - Opis
    - Publisher szczegóły (na przykład: `O=<publisher name>, L=<location>, S=State, C=Country`)
