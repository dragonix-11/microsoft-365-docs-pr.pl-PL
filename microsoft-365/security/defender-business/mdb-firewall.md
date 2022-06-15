---
title: Zapora w Microsoft Defender dla Firm
description: Dowiedz się więcej o ustawieniach Zapora Windows Defender w usłudze Defender dla Firm. Zapora może zapobiec przepływowi niepożądanego ruchu sieciowego do urządzeń firmowych.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 9ec6e0b10812c42c90266fd2793557ae6f3b2efc
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2022
ms.locfileid: "66090349"
---
# <a name="firewall-in-microsoft-defender-for-business"></a>Zapora w Microsoft Defender dla Firm

Microsoft Defender dla Firm obejmuje możliwości zapory z [Zapora Windows Defender](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). Ochrona zapory ułatwia zabezpieczanie urządzeń za pomocą reguł określających, który ruch sieciowy może wprowadzać lub przepływać z urządzeń. 

Za pomocą ochrony zapory można określić, czy zezwalać na połączenia na urządzeniach w różnych lokalizacjach, czy blokować je. Na przykład ustawienia zapory mogą zezwalać na połączenia przychodzące na urządzeniach połączonych z siecią wewnętrzną firmy, ale zapobiegać tym połączeniom, gdy urządzenie znajduje się w sieci z niezaufanymi urządzeniami.

**W tym artykule opisano**:

- [Domyślne ustawienia zapory w usłudze Defender dla Firm](#default-firewall-settings-in-defender-for-business)
- [Ustawienia zapory, które można skonfigurować w usłudze Defender dla Firm](#firewall-settings-you-can-configure-in-defender-for-business)


## <a name="default-firewall-settings-in-defender-for-business"></a>Domyślne ustawienia zapory w usłudze Defender dla Firm

Microsoft Defender dla Firm zawiera domyślne zasady zapory i ustawienia ułatwiające ochronę urządzeń firmy od pierwszego dnia. Gdy tylko urządzenia firmy zostaną dołączone do Microsoft Defender dla Firm, domyślne zasady zapory będą działać w następujący sposób:

- Połączenia wychodzące z urządzeń są domyślnie dozwolone niezależnie od lokalizacji.
- Gdy urządzenia są połączone z siecią firmy, wszystkie połączenia przychodzące są domyślnie blokowane.
- Gdy urządzenia są połączone z siecią publiczną lub siecią prywatną, wszystkie połączenia przychodzące są domyślnie blokowane.

W Microsoft Defender dla Firm można zdefiniować wyjątki, aby blokować lub zezwalać na połączenia przychodzące. Te wyjątki można zdefiniować, tworząc reguły niestandardowe. Zobacz [Zarządzanie regułami niestandardowymi dla zasad zapory](mdb-custom-rules-firewall.md).

## <a name="firewall-settings-you-can-configure-in-defender-for-business"></a>Ustawienia zapory, które można skonfigurować w usłudze Defender dla Firm

Microsoft Defender dla Firm obejmuje ochronę zapory za pośrednictwem Zapora Windows Defender. W poniższej tabeli wymieniono ustawienia, które można skonfigurować pod kątem ochrony zapory w Microsoft Defender dla Firm.

| Ustawienie | Opis |
|--|--|
| **Sieć domeny** | Profil sieci domeny ma zastosowanie do sieci firmowej. Ustawienia zapory dla sieci domeny mają zastosowanie do połączeń przychodzących inicjowanych na innych urządzeniach znajdujących się w tej samej sieci. Domyślnie połączenia przychodzące są ustawione na **wartość Blokuj wszystkie**.  |
| **Sieć publiczna** | Profil sieci publicznej ma zastosowanie do sieci, która może być używana w lokalizacji publicznej, takiej jak kawiarnia lub lotnisko. Ustawienia zapory dla sieci publicznych mają zastosowanie do połączeń przychodzących inicjowanych na innych urządzeniach znajdujących się w tej samej sieci. Ponieważ sieć publiczna może zawierać urządzenia, które nie są znane lub nie są zaufane, połączenia przychodzące są domyślnie ustawione na **wartość Blokuj wszystkie** .  |
| **Sieć prywatna** | Profil sieci prywatnej ma zastosowanie do sieci w lokalizacji prywatnej, takiej jak twój dom. Ustawienia zapory dla sieci prywatnych mają zastosowanie do połączeń przychodzących inicjowanych na innych urządzeniach znajdujących się w tej samej sieci. Ogólnie rzecz biorąc, w sieci prywatnej zakłada się, że wszystkie inne urządzenia w tej samej sieci są zaufanymi urządzeniami. Jednak domyślnie połączenia przychodzące są ustawione na **wartość Blokuj wszystkie**. |
| **Reguły niestandardowe** | [Reguły niestandardowe](mdb-custom-rules-firewall.md) umożliwiają blokowanie lub zezwalanie na określone połączenia. Załóżmy na przykład, że chcesz zablokować wszystkie połączenia przychodzące na urządzeniach połączonych z siecią prywatną, z wyjątkiem połączeń za pośrednictwem określonej aplikacji na urządzeniu. W takim przypadku należy ustawić **opcję Sieć prywatna** w celu zablokowania wszystkich połączeń przychodzących, a następnie dodać regułę niestandardową definiującą wyjątek. <br/><br/>Reguły niestandardowe umożliwiają definiowanie wyjątków dla określonych plików lub aplikacji, adresu protokołu internetowego (IP) lub zakresu adresów IP. <br/><br/>W zależności od typu tworzonej reguły niestandardowej poniżej przedstawiono przykładowe wartości, których można użyć: <br/><br/>Ścieżka pliku aplikacji: `C:\Windows\System\Notepad.exe or %WINDIR%\Notepad.exe` <br/><br/>ADRES IP: prawidłowy adres IPv4/IPv6, taki jak `192.168.11.0` lub `192.168.1.0/24` <br/><br/>ADRES IP: prawidłowy zakres adresów IPv4/IPv6, sformatowany jak `192.168.1.0-192.168.1.9` (bez spacji) |

## <a name="next-steps"></a>Następne kroki

- [Zarządzanie ustawieniami zapory w Microsoft Defender dla Firm](mdb-custom-rules-firewall.md)
- [Dowiedz się więcej o Zapora Windows Defender](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)
- [Wyświetlanie zdarzeń i zarządzanie nimi w Microsoft Defender dla Firm](mdb-view-manage-incidents.md)
- [Reagowanie na zagrożenia w Microsoft Defender dla Firm i eliminowanie ich](mdb-respond-mitigate-threats.md)
- [Przeglądanie akcji korygowania w centrum akcji](mdb-review-remediation-actions.md)