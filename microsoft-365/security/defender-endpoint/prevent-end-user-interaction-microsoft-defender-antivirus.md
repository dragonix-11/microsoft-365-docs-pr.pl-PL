---
title: Ukrywanie Program antywirusowy Microsoft Defender sieci Web
description: Kafelek ochrony przed wirusami i zagrożeniami możesz ukryć w Zabezpieczenia Windows aplikacji.
keywords: blokowanie interfejsu użytkownika, tryb bezbłędny, ukrywanie aplikacji, ukrywanie ustawień, ukrywanie interfejsu
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: d54d8ecf2d0c365168ae636cbe85ef1da9cfb6b1
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997812"
---
# <a name="prevent-users-from-seeing-or-interacting-with-the-microsoft-defender-antivirus-user-interface"></a>Uniemożliwianie użytkownikom oglądania interfejsu Program antywirusowy Microsoft Defender interakcji z nim

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Za pomocą funkcji zasady grupy można uniemożliwić użytkownikom korzystającym z punktów końcowych wyświetlanie Program antywirusowy Microsoft Defender końcowych. Możesz również uniemożliwić wsłuchiwowanie skanów.

## <a name="hide-the-microsoft-defender-antivirus-interface"></a>Ukrywanie Program antywirusowy Microsoft Defender sieci Web

W Windows 10 wersji 1703 ukrycie interfejsu spowoduje ukrycie powiadomień programu Program antywirusowy Microsoft Defender i uniemożliwienie pojawiania się kafelka Ochrona przed zagrożeniami w aplikacji & w Zabezpieczenia Windows aplikacji.

Po ustawieniu **Włączone:**

:::image type="content" source="../../media/wdav-headless-mode-off-1703.png" alt-text="Zrzut ekranu Zabezpieczenia Windows sekcje ochrony przed wirusami i zagrożeniami bez ikony tarczy.":::

Po ustawieniu **wartości Wyłączone lub** nieskonfigurowane:

:::image type="content" source="../../media/wdav-headless-mode-1703.png" alt-text="Zrzut ekranu przedstawiający Zabezpieczenia Windows z ikoną tarczy i sekcjami ochrony przed zagrożeniami.":::

> [!NOTE]
> Ukrycie interfejsu uniemożliwi także Program antywirusowy Microsoft Defender w punkcie końcowym. Powiadomienia programu Microsoft Defender dla punktu końcowego będą nadal wyświetlane. Możesz także skonfigurować powiadomienia [wyświetlane w punktach końcowych pojedynczo.](configure-notifications-microsoft-defender-antivirus.md)

We wcześniejszych wersjach programu Windows 10 ustawienie spowoduje ukrycie Windows Defender klienta. Jeśli użytkownik spróbuje go otworzyć, otrzyma ostrzeżenie o treści "Twoja administrator systemu dostępu do tej aplikacji".

:::image type="content" source="../../media/wdav-headless-mode-1607.png" alt-text="Komunikat ostrzegawczy, gdy w programie Windows 10 w wersji wcześniejszej niż 1703 włączono tryb bezgłowy":::

## <a name="use-group-policy-to-hide-the-microsoft-defender-av-interface-from-users"></a>Ukrywanie interfejsu audio/wideo programu Microsoft Defender za pomocą funkcji zasady grupy użytkowników

1. Na komputerze zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie kliknij pozycję **Edytuj**.

2. Za pomocą **zasady grupy zarządzania przejdź** do **opcji Konfiguracja komputera**.

3. Kliknij **pozycję Szablony administracyjne**.

4. Rozwiń drzewo, **aby Windows składniki > Program antywirusowy Microsoft Defender > interfejsu klienta**.

5. Kliknij dwukrotnie ustawienie **Włącz tryb interfejsu użytkownika** bez nabłędzienia i ustaw opcję **Włączone**. Kliknij przycisk **OK**.

Zobacz [Uniemożliwianie użytkownikom lokalnego modyfikowania](configure-local-policy-overrides-microsoft-defender-antivirus.md) ustawień zasad, aby uzyskać więcej opcji dotyczących uniemożliwiania użytkownikom modyfikowania ochrony na swoich komputerach.

## <a name="prevent-users-from-pausing-a-scan"></a>Uniemożliwianie użytkownikom wsłuchiwania skanowania

Możesz uniemożliwić użytkownikom wsłuchianie skanów, co może być pomocne w celu zagwarantowania, że użytkownicy nie przerywają skanowania zaplanowanego lub na żądanie.

> [!NOTE]
> To ustawienie nie jest obsługiwane w Windows 10.

### <a name="use-group-policy-to-prevent-users-from-pausing-a-scan"></a>Za zasady grupy, aby uniemożliwić użytkownikom wsłuchiwanie skanowania

1. Na komputerze zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie kliknij pozycję **Edytuj**.

2. Za pomocą **zasady grupy zarządzania przejdź** do **opcji Konfiguracja komputera**.

3. Kliknij **pozycję Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki Program antywirusowy Microsoft Defender** \>  \> **skanu**.

5. Kliknij dwukrotnie ustawienie **Zezwalaj użytkownikom na wstrzymywanie skanowania** i ustaw dla tej opcji wartość **Wyłączone**. Kliknij przycisk **OK**.

## <a name="related-articles"></a>Artykuły pokrewne

- [Konfigurowanie powiadomień wyświetlanych w punktach końcowych](configure-notifications-microsoft-defender-antivirus.md)
- [Konfigurowanie interakcji użytkownika końcowego z Program antywirusowy Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
