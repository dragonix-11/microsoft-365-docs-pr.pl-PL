---
title: Zapora w programie Microsoft Defender dla firm (wersja Preview)
description: Dowiedz się Windows Defender o Zaporze programu Microsoft Defender dla firm (wersja Preview), w tym o ustawieniach konfiguracji
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: d3fbaa66dd29c0c5ff3dcc2a420d1d05e789bd33
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027046"
---
# <a name="firewall-in-microsoft-defender-for-business-preview"></a>Zapora w programie Microsoft Defender dla firm (wersja Preview)

> [!IMPORTANT]
> Usługa Microsoft Defender dla firm jest teraz w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, którzy zarejestrują się tutaj [, aby](https://aka.ms/mdb-preview) poprosić o to. W najbliższych tygodniach nawiązemy wstępną ofertę klientów i partnerów oraz rozszerzymy jej wersja zapoznawczą, aby rozszerzyć jej dostępność do ogólnej dostępności. Pamiętaj, że wersja Preview zostanie uruchamiana z [początkowym zestawem scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a funkcje będą regularnie dodajemy.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

Program Microsoft Defender dla firm (wersja Preview) zawiera funkcje zapory z [Windows Defender sieciowej](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). Ochrona za pomocą zapory pomaga zabezpieczyć urządzenia za pomocą reguł, które określają ruch sieciowy, który może napływać do urządzeń lub z nich przepływać. 

Za pomocą ochrony zapory możesz określić, czy zezwalać na połączenia na urządzeniach w różnych lokalizacjach, czy blokować je. Ustawienia zapory mogą na przykład zezwalać na połączenia przychodzące na urządzeniach połączonych z siecią wewnętrzną organizacji, ale zapobiegać tym połączeniom, gdy urządzenie znajduje się w sieci z niezaufanymi urządzeniami.

**W tym artykule opisano**:

- [Domyślne ustawienia zapory w programie Defender dla firm (wersja Preview)](#default-firewall-settings-in-defender-for-business)
- [Ustawienia zapory, które można skonfigurować w programie Defender dla firm (wersja Preview)](#firewall-settings-you-can-configure-in-defender-for-business)

## <a name="default-firewall-settings-in-defender-for-business"></a>Domyślne ustawienia zapory w programie Defender dla firm

Program Microsoft Defender dla firm (wersja Preview) zawiera domyślne zasady zapory i ustawienia, które pomagają chronić urządzenia Twojej organizacji od pierwszego dnia. Po dołączonach urządzeń organizacji do programu Microsoft Defender dla firm (wersja Preview) domyślne zasady zapory są następujące:

- Połączenia wychodzące z urządzeń są domyślnie dozwolone, niezależnie od lokalizacji.
- Gdy urządzenia są połączone z siecią organizacji, wszystkie połączenia przychodzące są domyślnie blokowane.
- Gdy urządzenia są połączone z siecią publiczną lub prywatną, wszystkie połączenia przychodzące są domyślnie blokowane.

W programie Microsoft Defender dla firm (wersja Preview) można zdefiniować wyjątki w celu zablokowania lub zablokowania połączeń przychodzących. Wyjątki te można zdefiniować, tworząc reguły niestandardowe. Zobacz [Zarządzanie regułami niestandardowymi dla zasad zapory](mdb-custom-rules-firewall.md).

## <a name="firewall-settings-you-can-configure-in-defender-for-business"></a>Ustawienia zapory, które można skonfigurować w programie Defender dla firm

Usługa Microsoft Defender dla firm (wersja Preview) zapewnia ochronę za pomocą Windows Defender sieciowej. W poniższej tabeli wymieniono ustawienia, które można skonfigurować w celu ochrony zapory w programie Microsoft Defender dla firm (wersja Preview). <br/><br/>

| Ustawienie | Opis |
|--|--|
| **Sieć domenowa** | Profil sieci domeny dotyczy sieci Twojej organizacji. Ustawienia zapory sieci Twojej domeny mają zastosowanie do połączeń przychodzących inicjowanych na innych urządzeniach w tej samej sieci. Domyślnie dla połączeń przychodzących ustawiono opcję **Blokuj wszystkie**.  |
| **Sieć publiczna** | Profil sieci publicznej dotyczy sieci, która może być dostępna w lokalizacji publicznej, takiej jak kawiarnia lub lotniska. Ustawienia zapory dla sieci publicznych mają zastosowanie do połączeń przychodzących inicjowanych na innych urządzeniach w tej samej sieci. Ponieważ sieć publiczna może zawierać urządzenia, których nie znasz lub które nie są zaufane, połączenia przychodzące są domyślnie ustawione **jako Zablokuj wszystko** .  |
| **Sieć prywatna** | Profil sieci prywatnej dotyczy sieci w lokalizacji prywatnej, takiej jak Twój dom. Ustawienia zapory dla sieci prywatnych mają zastosowanie do połączeń przychodzących inicjowanych na innych urządzeniach w tej samej sieci. Ogólnie w sieci prywatnej zakłada się, że wszystkie inne urządzenia w tej samej sieci są urządzeniami zaufanymi. Jednak domyślnie dla połączeń przychodzących ustawiono opcję **Blokuj wszystkie**. |
| **Reguły niestandardowe** | [Reguły niestandardowe](mdb-custom-rules-firewall.md) umożliwiają blokowanie określonych połączeń lub zezwalanie na nie. Załóżmy na przykład, że chcesz zablokować wszystkie połączenia przychodzące na urządzeniach połączonych z siecią prywatną z wyjątkiem połączeń za pośrednictwem określonej aplikacji na urządzeniu. W tym przypadku należy ustawić opcję **Sieć** prywatna tak, aby blokowała wszystkie połączenia przychodzące, a następnie dodać regułę niestandardową definiującą wyjątek. <br/><br/>Możesz użyć reguł niestandardowych w celu zdefiniowania wyjątków dla określonych plików lub aplikacji, adresu IP lub zakresu adresów IP. <br/><br/>Oto kilka przykładowych wartości, których możesz użyć, w zależności od typu tworzyć reguły niestandardowe: <br/><br/>Ścieżka pliku aplikacji: `C:\Windows\System\Notepad.exe or %WINDIR%\Notepad.exe` <br/><br/>IP: Prawidłowy adres IPv4/IPv6, taki jak `192.168.1.0` lub `192.168.1.0/24` <br/><br/>IP: prawidłowy zakres adresów IPv4/IPv6 sformatowany tak `192.168.1.0-192.168.1.9` , jak (bez spacji) |

## <a name="next-steps"></a>Następne kroki

- [Zarządzanie ustawieniami zapory w programie Microsoft Defender dla firm (wersja Preview)](mdb-custom-rules-firewall.md)

- [Dowiedz się więcej o Windows Defender sieciowej](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)

- [Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm (wersja Preview)](mdb-view-manage-incidents.md)

- [Reagowanie na zagrożenia i ograniczanie ich w programie Microsoft Defender dla firm (wersja Preview)](mdb-respond-mitigate-threats.md)

- [Przeglądanie działań naprawczych w Centrum akcji](mdb-review-remediation-actions.md)