---
title: Konfigurowanie Program antywirusowy Microsoft Defender powiadomień
description: Dowiedz się, jak skonfigurować i dostosować zarówno standardowe, jak i inne Program antywirusowy Microsoft Defender dotyczące punktów końcowych.
keywords: powiadomienia, defender, oprogramowanie antywirusowe, punkt końcowy, zarządzanie, administrator
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.topic: article
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 287e49a92032e725153065ef3d996e2b5c14baf9
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/29/2021
ms.locfileid: "62996794"
---
# <a name="configure-microsoft-defender-antivirus-notifications-that-appear-on-endpoints"></a>Konfigurowanie Program antywirusowy Microsoft Defender, które są wyświetlane w punktach końcowych

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

W Windows 10 i Windows 11 powiadomienia aplikacji dotyczące wykrywania złośliwego oprogramowania i rozwiązywania problemów są bardziej niezawodne, spójne i zwięzłe. Program antywirusowy Microsoft Defender są wyświetlane w punktach końcowych po zakończeniu skanowania i wykryciu zagrożeń. Powiadomienia są wyświetlane zarówno po zaplanowanych, jak i ręcznie wyzwalanych skanach. Powiadomienia te są również wyświetlane w **Centrum** powiadomień, a w regularnych odstępach czasu jest wyświetlane podsumowanie skanów i wykrywania zagrożeń.

Jeśli jesteś częścią zespołu zabezpieczeń organizacji, możesz skonfigurować sposób, w jaki powiadomienia są wyświetlane w punktach końcowych, takie jak powiadomienia, które monitowały o ponowne uruchomienie systemu lub wskazujące, że wykryto i usunięto zagrożenie.

## <a name="configure-antivirus-notifications-using-group-policy-or-the-windows-security-app"></a>Konfigurowanie powiadomień antywirusowych zasady grupy aplikacji Zabezpieczenia Windows sieci

W aplikacji mobilnej można skonfigurować wyświetlanie dodatkowych powiadomień, takich jak podsumowania dotyczące wykrywania zagrożeń, [Zabezpieczenia Windows](microsoft-defender-security-center-antivirus.md) aplikacji oraz powiadomienia zasady grupy.

> [!NOTE]
> W Windows 10 1607  \> ta funkcja była nazywana rozszerzonymi powiadomieniami i  została skonfigurowana w obszarze aktualizacji Windows Ustawienia aktualizacji & **zabezpieczeń** \> **Windows Defender**. W zasady grupy dla wszystkich wersji systemu Windows 10 i Windows 11 funkcja powiadomień nosi nazwę **Rozszerzone powiadomienia**.

### <a name="use-group-policy-to-disable-additional-notifications"></a>Użyj zasady grupy, aby wyłączyć dodatkowe powiadomienia

1. Na komputerze zasady grupy zarządzania otwórz [konsolę zasady grupy zarządzania danymi](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Kliknij prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

3. W zasady grupy **zarządzania przejdź** do **konfiguracji komputera**.

4. Wybierz **pozycję Szablony administracyjne**.

5. Rozwiń drzewo, **aby Windows składniki** \> **Program antywirusowy Microsoft Defender** >  **Raportowanie**.

6. Kliknij dwukrotnie **pozycję Wyłącz rozszerzone powiadomienia** i ustaw dla tej opcji wartość **Włączone**. Następnie wybierz przycisk **OK**. Zapobiegnie to pojawianiu się dodatkowych powiadomień.

> [!IMPORTANT]
> Wyłączenie dodatkowych powiadomień nie spowoduje wyłączenia powiadomień krytycznych, takich jak wykrywanie zagrożeń i alerty o działaniach naprawczych.

### <a name="use-the-windows-security-app-to-disable-additional-notifications"></a>Wyłączanie dodatkowych Zabezpieczenia Windows za pomocą aplikacji Zabezpieczenia Windows

1. Otwórz aplikację Zabezpieczenia Windows, klikając ikonę tarczy na pasku zadań lub wyszukując w menu Start pozycję **Zabezpieczenia**.

2. Wybierz **kafelek Ochrona przed** & zagrożeniami (lub ikonę tarczy na lewym pasku menu), a następnie wybierz pozycję Ustawienia ochrony przed & **wirusami**

3. Przewiń do sekcji **Powiadomienia** i wybierz **pozycję Zmień ustawienia powiadomień**.

4. Przesuń przełącznik do opcji **Wyłączone lub** **Wł.,** aby wyłączyć lub włączyć dodatkowe powiadomienia.

> [!IMPORTANT]
> Wyłączenie dodatkowych powiadomień nie spowoduje wyłączenia powiadomień krytycznych, takich jak wykrywanie zagrożeń i alerty o działaniach naprawczych.

## <a name="configure-standard-notifications-on-endpoints-using-group-policy"></a>Konfigurowanie standardowych powiadomień dotyczących punktów końcowych przy użyciu zasady grupy

Za pomocą zasady grupy:

- Wyświetlanie dodatkowego, dostosowanego tekstu na punktach końcowych, gdy użytkownik musi wykonać akcję
- Ukrywanie wszystkich powiadomień w punktach końcowych
- Ukrywanie powiadomień o ponownym uruchomieniu w punktach końcowych

Ukrycie powiadomień może być przydatne w sytuacjach, w których nie można ukryć całego Program antywirusowy Microsoft Defender interfejsu. Aby [uzyskać więcej informacji,](prevent-end-user-interaction-microsoft-defender-antivirus.md) zobacz Uniemożliwianie użytkownikom Program antywirusowy Microsoft Defender interfejsu użytkownika. Ukrycie powiadomień występuje tylko w przypadku punktów końcowych, w których wdrożono zasady. Powiadomienia dotyczące czynności, które należy wykonać (takich jak ponowne uruchomienie), nadal będą wyświetlane na Microsoft Endpoint Manager Endpoint Protection [nawigacyjnym monitorowania i raportach](/configmgr/protect/deploy-use/monitor-endpoint-protection). 

Aby dodać niestandardowe informacje kontaktowe do powiadomień dotyczących punktów końcowych, zobacz [Dostosowywanie Zabezpieczenia Windows dla organizacji](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center).

### <a name="use-group-policy-to-hide-notifications"></a>Ukrywanie zasady grupy za pomocą funkcji powiadomienia

1. Na komputerze zasady grupy zarządzania otwórz [konsolę zasady grupy zarządzania danymi](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Kliknij prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

3. W **administracyjnym zasady grupy zarządzania** przejdź do **strony Konfiguracja komputera,** a następnie wybierz pozycję **Szablony administracyjne**.

4. Rozwiń drzewo, **aby Windows składniki Program antywirusowy Microsoft Defender** \>  \> **interfejsu klienta**. 

5. Kliknij dwukrotnie pozycję **Pomiń wszystkie** powiadomienia i ustaw dla opcji wartość **Włączone**. 

6. Wybierz przycisk **OK**. Zapobiegnie to pojawianiu się dodatkowych powiadomień.

### <a name="use-group-policy-to-hide-reboot-notifications"></a>Ukrywanie zasady grupy ponownego rozruchu za pomocą funkcji aktualizacji

1. Na komputerze zasady grupy zarządzania otwórz [konsolę zasady grupy zarządzania danymi](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Kliknij prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

2. W zasady grupy **zarządzania przejdź** do **konfiguracji komputera**.

3. Kliknij **pozycję Szablony administracyjne**.

4. Rozwiń drzewo, **aby Windows składniki Program antywirusowy Microsoft Defender** \>  \> **interfejsu klienta**.

5. Kliknij dwukrotnie pozycję **Pomiń powiadomienia o ponownym uruchomieniu** i ustaw opcję **Włączone**. 

5. Wybierz przycisk **OK**. Zapobiegnie to pojawianiu się dodatkowych powiadomień.

