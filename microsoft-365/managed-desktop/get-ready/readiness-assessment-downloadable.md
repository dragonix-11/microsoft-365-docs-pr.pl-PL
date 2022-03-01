---
title: Sprawdzanie gotowości do pobrania
description: Sprawdza ustawienia urządzenia i sieci, w tym wymagane punkty końcowe
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 9e3ad0953cdbd6561f9a0145ccff5aefe24b8dfb
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011323"
---
# <a name="downloadable-readiness-assessment-checker"></a>Sprawdzanie gotowości do pobrania

Aby dobrze pracować z Microsoft Managed Desktop, urządzenia muszą spełniać określone wymagania dotyczące sprzętu i ustawień. Każde urządzenie musi mieć możliwość dotarcia do kluczowych punktów końcowych.

Pobierz i uruchom narzędzie do sprawdzania gotowości, aby uzyskać raport HTML, wyświetlić wyniki i podjąć działania. Musisz pobrać narzędzie i pliki supportowe. Następnie uruchom go ręcznie na każdym urządzeniu, na którym chcesz się zarejestrować Microsoft Managed Desktop.

Dla każdego sprawdzenia narzędzie raportuje jeden z trzech możliwych wyników:

| Result (Wynik) | Znaczenie |
| ----- | ----- |
| Gotowe | Przed ukończeniem rejestracji nie jest wymagane żadne działanie. |
| Porada | Postępuj zgodnie z instrukcjami w narzędziu, aby uzyskać najlepsze środowisko rejestracji i dla użytkowników. <br><br> Możesz *zakończyć* rejestrację, ale musisz rozwiązać te problemy przed wdrożeniem pierwszego urządzenia. |
| Jeszcze nie gotowe | **Rejestracja nie powiedzie się** , jeśli nie rozwiążesz tych problemów. <br><br> Postępuj zgodnie z instrukcjami narzędzia, aby je rozwiązać. |

## <a name="obtain-the-checker"></a>Uzyskiwanie sprawdzania

Pobierz .zip pliku z https://aka.ms/mmddratoolv0.

> [!NOTE]
> Użytkownik uruchamiając narzędzie musi mieć prawa administratora lokalnego na urządzeniu, na którym je uruchamia.

**Aby uruchomić narzędzie:**

1. Skopiuj pobrany plik .zip na każde urządzenie, które chcesz sprawdzić.
2. Wyodrębnij wszystkie pliki w skompresowanym pliku do pobrania.
3. Uruchom **Microsoft.MMD.DeviceReadinessAssessmentTool.exe**.
4. Po wyświetleniu monitu Kontrola dostępu użytkownika wybierz pozycję **Tak**. Narzędzie uruchomi się i otworzy raport w domyślnej przeglądarce.

Możesz również pobrać i wyodrębnić archiwum .zip do udostępnionej lokalizacji, uzyskać dostęp **do** Microsoft.MMD.DeviceReadinessAssessmentTool.exez każdego urządzenia. Następnie uruchom go lokalnie.

## <a name="checks"></a>Testy

Narzędzie do pobrania sprawdza następujące urządzenia i elementy związane z siecią:

| Czek | Opis |
| ----- | ----- |
| Sprzęt | Urządzenia muszą spełniać określone wymagania sprzętowe, aby można było pracować z Microsoft Managed Desktop. Aby uzyskać więcej informacji, zobacz [Wymagania dotyczące urządzenia](../service-description/device-list.md). <br><br> Jeśli urządzenie nie sprawdzi się, będzie zgodne z programem Microsoft Managed Desktop. |
| Punkty końcowe sieci | Urządzenia bardzo mogą uzyskać kilka [kluczowych punktów końcowych do](network.md) pracy z Microsoft Managed Desktop. <br><br> Jeśli narzędzie raportuje **wynik Nie gotowe** , zobacz szczegółowy raport, aby dowiedzieć się, które punkty końcowe nie były osiągalne. Następnie dostosuj zaporę lub inne ustawienia sieci, aby upewnić się, że te punkty końcowe będą osiągne. |

### <a name="other-settings"></a>Inne ustawienia

| Ustawienie | Opis |
| ----- | ----- |
| Enterprise Wi-Fi profilów | Wynik **porady** oznacza, że korzystasz z niektórych Wi-Fi profilów, które wymagają certyfikatów i profilów, aby działały prawidłowo. Aby uzyskać więcej informacji, zobacz [Wdrażanie certyfikatów i profilu sieci Wi-Fi/VPN](certs-wifi-lan.md#deploy-certificates-and-wi-fivpn-profile). |
| Profile sieci LAN | Wynik **porady** oznacza, że masz sieci LANs, które wymagają certyfikatów i profilów, aby działały prawidłowo. Aby uzyskać więcej informacji, zobacz [Przygotowanie certyfikatów i profilów sieci dla Microsoft Managed Desktop](certs-wifi-lan.md). |
| Profile VPN | Wynik **porad oznacza** , że korzystasz z wirtualnej sieci prywatnej (VPN). Utwórz profil VPN, aby wdrażać certyfikaty zintegrowane z usługą Microsoft Intune. Aby uzyskać więcej informacji, zobacz [Przygotowanie certyfikatów i profilów sieci dla Microsoft Managed Desktop](certs-wifi-lan.md). |
| Mapowane dyski | Wynik **porady** oznacza, że masz niektóre zamapowane dyski, które nie są zalecane. Aby uzyskać więcej informacji, zobacz [Przygotowanie zamapowanych dysków dla Microsoft Managed Desktop](mapped-drives.md). |
| Drukuj kolejki | Wynik **porady** oznacza, że masz jakieś zaległe kolejki wydruku, które nie są zalecane. Jednym z rozwiązań jest użycie funkcji drukowania w chmurze. Aby uzyskać więcej informacji, zobacz [Przygotowanie zasobów do drukowania Microsoft Managed Desktop](printing.md). |
| Proxy | Wynik **porady** oznacza, że korzystasz z serwera proxy. Aby uzyskać więcej informacji, [zobacz Konfiguracja sieci dla Microsoft Managed Desktop](network.md). |
