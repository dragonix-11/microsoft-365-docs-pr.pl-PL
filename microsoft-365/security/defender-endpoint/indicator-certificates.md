---
title: Tworzenie wskaźników na podstawie certyfikatów
ms.reviewer: ''
description: Tworzenie wskaźników na podstawie certyfikatów definiujących wykrywanie, zapobieganie i wykluczenie obiektów.
keywords: ioc, certificate, certificates, manage, allowed, blocked, block, clean, malicious, file hash, ip address, urls, domain
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 7140b5714dd3660fe8dead37c3b6341d026fbb7c
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998122"
---
# <a name="create-indicators-based-on-certificates"></a>Tworzenie wskaźników na podstawie certyfikatów

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Dla certyfikatów można tworzyć wskaźniki. Niektóre typowe przypadki użycia to:

- Scenariusze, w których konieczne jest wdrożenie technologii blokowania, takich [](attack-surface-reduction.md) jak reguły ograniczania powierzchni ataków [](controlled-folders.md) i kontrolowany dostęp do folderu, ale musisz zezwolić na zachowania ze strony podpisanych aplikacji, dodając certyfikat do listy zezwalań.
- Blokowanie używania określonej podpisanej aplikacji w całej organizacji. Tworząc wskaźnik w celu zablokowania certyfikatu aplikacji, funkcja audio/wideo Windows Defender zapobiega wykonywaniu plików (blokowaniu i rozwiązywaniu problemów), a automatyczne badanie i rozwiązywanie problemów działa tak samo.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Ważne jest zrozumienie następujących wymagań przed utworzeniem wskaźników dla certyfikatów:

- Ta funkcja jest dostępna, jeśli Twoja organizacja Program antywirusowy Windows Defender i jest włączona ochrona oparta na chmurze. Aby uzyskać więcej informacji, zobacz [Zarządzanie ochroną opartą na chmurze](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus).
- Wersja klienta ochrony przed złośliwym oprogramowaniem musi mieć wersję 4.18.1901.x lub nowszą.
- Obsługiwane na komputerach z Windows 10, wersja 1703 lub nowsza, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 i Windows Server 2022.
    
    >[!NOTE]
    >Windows Server 2016 i Windows Server 2012 R2 muszą zostać naniesone zgodnie z instrukcjami podanymi w te sposób: Windows [onboard](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016), aby ta funkcja działała. 

- Definicje ochrony przed wirusami i zagrożeniami muszą być aktualne.
- Ta funkcja obecnie obsługuje wprowadzanie . CER lub . Rozszerzenia plików PEM.

> [!IMPORTANT]
>
> - Certyfikat prawidłowego liścia jest certyfikatem podpisywania, który ma prawidłową ścieżkę certyfikacji i musi być przekierowyny w łańcuch do głównego urzędu certyfikacji zaufanego przez firmę Microsoft. Ewentualnie certyfikat niestandardowy (z podpisem własnym) może być używany, o ile jest zaufany przez klienta (certyfikat głównego urzędu certyfikacji jest instalowany w obszarze zaufanych głównych urzędów certyfikacji na komputerze lokalnym).
> - Dzieci lub element nadrzędny usługi IOCs certyfikatu zezwalania/blokowania nie są uwzględniane w funkcji zezwalania/blokowania usługi IoC. Obsługiwane są tylko certyfikaty liści.
> - Nie można zablokować certyfikatów podpisanych przez firmę Microsoft.

## <a name="create-an-indicator-for-certificates-from-the-settings-page"></a>Na stronie ustawień utwórz wskaźnik dla certyfikatów:

> [!IMPORTANT]
> Utworzenie i usunięcie certyfikatu IoC może potrwać do 3 godzin.

1. W okienku nawigacji wybierz pozycję Wskaźnik **Ustawienia** \> **punktów** \> **końcowych** (w obszarze **Reguły**).

2. Wybierz **wskaźnik Dodaj**.

3. Określ następujące szczegóły:
   - Wskaźnik — określ szczegóły jednostki i zdefiniuj wygasanie wskaźnika.
   - Akcja — określ akcję, która ma zostać wykonane, i podaj opis.
   - Zakres — definiowanie zakresu grupy maszyn.

4. Przejrzyj szczegóły na karcie Podsumowanie, a następnie kliknij przycisk **Zapisz**.

## <a name="related-topics"></a>Tematy pokrewne

- [Tworzenie wskaźników](manage-indicators.md)
- [Tworzenie wskaźników dla plików](indicator-file.md)
- [Tworzenie wskaźników adresów IP oraz adresów URL/domen](indicator-ip-domain.md)
- [Zarządzanie wskaźnikami](indicator-manage.md)
