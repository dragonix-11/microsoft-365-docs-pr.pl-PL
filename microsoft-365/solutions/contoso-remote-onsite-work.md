---
title: Odpowiedź i obsługa coVID-19 firmy Contoso dla pracy hybrydowej
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Zrozumienie, jak firma Contoso Corporation reagowała na usługę COVID-19, i inżynieruje infrastrukturę instalacji i aktualizacji oprogramowania na przykład w celu pracy hybrydowej.
ms.openlocfilehash: 9ed3857c97bd82bd03a6a192bec5666f22e0589a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988365"
---
# <a name="contosos-covid-19-response-and-support-for-hybrid-work"></a>Odpowiedź i obsługa coVID-19 firmy Contoso dla pracy hybrydowej

Firma Contoso zawsze wspierała pracowników zdalnych, którzy uzyskiwali dostęp do zasobów lokalnych za pośrednictwem centralnego serwera VPN w siedzibie głównej w Paryżu. Firma Contoso wystawiła wszystkim pracownikom zdalnym zarządzany komputer przenośny. Pracownicy lokalni mieli mieszaninę komputerów stacjonarnych i laptopów.

## <a name="contosos-response-to-covid-19"></a>Odpowiedź firmy Contoso na kod COVID-19

Po najechu na proceder COVID-19 pracownicy zdalni byli nagle, ale wszyscy, oprócz podstawowych pracowników, byli pracownikami zdalnymi. Firma Contoso odpowiedziała, przesuwając pracowników do pracy z domu i przeprowadzając swoje podstawowe działania za pośrednictwem zdalnego dostępu do zasobów lokalnych i online przy Microsoft 365 usługach w chmurze.

Firma Contoso miała serwery VPN z dostępem zdalnym w biurze w siedzibie głównej w Paryżu, aby obsługiwać 25% jej już pracowników zdalnych, ale szybko przeniosła się w celu przeskalowania jego pojemności dostępu zdalnego do obsługi 90% jej pracowników. Serwery VPN z dostępem zdalnym firmy Contoso wdrożono w poszczególnych biurach satelitarnych, dzięki czemu pracownicy zdalni korzystali z regionalnego punktu wejścia na dostęp do intranetu firmy Contoso.

Firma Contoso zaktualizowała również konfigurację klientów SIECI VPN zainstalowanych na komputerach przenośnych, tabletach i smartfonach w celu rozdzielenia, dzięki czemu ruch dla zestawu punktów końcowych optymalizowania sieci Office 365 ominął połączenie VPN i został wysłany bezpośrednio przez Internet. Aby uzyskać więcej informacji, zobacz [Optymalizowanie Office 365 sieci zdalnej dla użytkowników zdalnych z podziałem sieci VPN](../enterprise/microsoft-365-vpn-split-tunnel.md).

Oto wynikowa konfiguracja urządzeń VPN zainstalowanych w siedzibie głównej w Paryżu i poszczególnych biur satelitarnych. 

![Infrastruktura sieci VPN firmy Contoso.](../media/contoso-remote-onsite-work/contoso-vpn-infrastructure.png)

Pracownik zdalny z zainstalowanym klientem SIECI VPN używa systemu DNS do odnalezienia najbliższego regionalnie biura i łączy się z zainstalowanym tam urządzeniem VPN. Dzięki rozdzielaniu rozdzielanym ruch do Microsoft 365 optymalizowania punktów końcowych jest wysyłany bezpośrednio do lokalizacji najbardziej Microsoft 365 sieciowej. Cały ruch jest przesyłany przez połączenie VPN do urządzenia VPN.

## <a name="contosos-support-for-hybrid-work"></a>Obsługa pracy hybrydowej firmy Contoso

Po początkowych zmianach w celu obsługi głównie pracowników zdalnych podczas blokad regionalnych firma Contoso wprowadzała zmiany w infrastrukturze w celu obsługi pracy hybrydowej, w której pracownik może być:

- Zawsze zdalnie.
- Zawsze pod miejscu.
- Połączenie ze zdalną i u firmy.

Microsoft 365 funkcje tożsamości, zabezpieczeń i zgodności są zaprojektowane pod kątem zerowego zaufania i działają niezależnie od lokalizacji użytkownika i jego urządzenia. Aby uzyskać więcej informacji, zobacz [Zerowe zaufanie](https://www.microsoft.com/security/business/zero-trust).

Jednak zarządzanie nowymi instalacjami i aktualizacjami oprogramowania zależy od lokalizacji urządzenia, ponieważ oprogramowanie do zainstalowania może pochodzić ze źródła lokalnego lub internetowego. Nową infrastrukturę instalacji i aktualizacji projektują pracownicy firmy Contoso, a nie na podstawie lokalizacji urządzenia.

Wyznaczono dwa typy urządzeń: dedykowane lokalnie i mobilne.

### <a name="dedicated-on-premises"></a>Dedykowany lokalnie

Dedykowane urządzenie lokalne to komputer stacjonarny lub serwerowy, który nigdy nie opuszcza intranetu firmy Contoso i nie ma zainstalowanego klienta VPN. Te urządzenia lokalne nadal korzystają z Microsoft Endpoint Configuration Manager i ich punktów dystrybucji do instalacji i aktualizacji oprogramowania Windows 10, Aplikacje Microsoft 365 dla przedsiębiorstw i przeglądarki Microsoft Edge.

### <a name="roaming"></a>Roaming

Urządzenie mobilne może opuścić intranet firmy Contoso i obejmuje laptopy wydane wielu pracownikom biurowym i wszystkim pracownikom zdalnym oraz innym urządzeniom należącym do organizacji, takim jak smartfony i tablety z zainstalowanym klientem VPN firmy Contoso. 

Ponieważ te urządzenia mogą być połączone z Internetem w dowolnej chwili, korzystają one z intune lub innych usług opartych na chmurze na użytek instalacji i aktualizacji aplikacji Windows 10, Aplikacje Microsoft 365 dla przedsiębiorstw i Edge. Nie używają one istniejących lokalnych punktów Menedżer konfiguracji dystrybucyjnych.

Oznacza to, że niektóre instalacje i aktualizacje dla urządzeń mobilnych będą wykonywane przez Internet, gdy są lokalne i połączone z intranetem. Jednak zdaniem architektów IT firmy Contoso prostota konfiguracji jest ważniejsza niż optymalizacja przepustowości intranetu w Internecie, zwłaszcza gdy większość pracowników zdalnych rzadko łączy się z intranetem.

Oto infrastruktura wynikowa.

![Infrastruktura instalacji i aktualizacji firmy Contoso.](../media/contoso-remote-onsite-work/contoso-updates-infrastructure.png)

Zachowanie instalacji i aktualizacji zależy od tego, czy konta komputerów urządzeń należą do jednej z tych grup:

- OnPremDevices

  Klient Menedżer konfiguracji na urządzeniu używa punktów dystrybucji do instalacji i aktualizacji.

- RoamingDevices

  Intune and other settings on the device specify the use of the Microsoft 365 network for installs and updates.

## <a name="new-onboarding-process"></a>Nowy proces dołączania

W przypadku nowego dedykowanego urządzenia lokalnego wydanego nowemu pracownikowi lub nowemu serwerowi w centrum danych, gdy pracownik się Menedżer konfiguracji, klient programu Menedżer konfiguracji oparty na członkostwie w grupie OnPremDevices pobiera i instaluje najnowsze aktualizacje dla usługi Windows 10, Aplikacje Microsoft 365 dla przedsiębiorstw i Edge z lokalnych Menedżer konfiguracji punktów dystrybucji. Po zakończeniu dedykowane urządzenie lokalne jest gotowe do użycia i wykorzystuje te punkty dystrybucji na bieżąco.

W przypadku nowego urządzenia zdalnego wydanego nowemu pracownikowi, gdy pracownik się inicjuje, urządzenie na podstawie członkostwa w grupie RoamingDevices kontaktuje się z usługą Intune w chmurze i innymi usługami oraz pobiera i instaluje najnowsze aktualizacje dla aplikacji Windows 10, Aplikacje Microsoft 365 dla przedsiębiorstw i Edge. Po zakończeniu urządzenie zdalne jest gotowe do użycia i używa zainstalowanego klienta VPN w celu uzyskiwania dostępu do zasobów lokalnych i sieci Microsoft 365 na bieżąco.

## <a name="next-step"></a>Następny krok

[Skonfiguruj infrastrukturę do pracy hybrydowej](empower-people-to-work-remotely.md) w organizacji.
