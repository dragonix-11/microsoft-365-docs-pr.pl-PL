---
title: Większe Microsoft 365 dla Twojego Microsoft 365 dla środowiska testowania w przedsiębiorstwie
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/09/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-security-compliance
ms.custom:
- Ent_TLGs
- admindeeplinkMAC
- admindeeplinkDEFENDER
- admindeeplinkSPO
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Skorzystaj z tego przewodnika laboratorium testowego, aby Microsoft 365 dodatkowych ustawień zabezpieczeń Microsoft 365 dla środowiska testowania w przedsiębiorstwie.
ms.openlocfilehash: bf64bb23192eb4a4d2b3700a2b0c4390efc1f53e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327913"
---
# <a name="increased-microsoft-365-security-for-your-microsoft-365-for-enterprise-test-environment"></a>Większe Microsoft 365 dla Twojego Microsoft 365 dla środowiska testowania w przedsiębiorstwie

*Ten przewodnik laboratorium testowego może być używany tylko w Microsoft 365 testowych w przedsiębiorstwie.*

Zgodnie z instrukcjami w tym artykule możesz skonfigurować dodatkowe Microsoft 365 w celu zwiększenia bezpieczeństwa w środowisku testowym Microsoft 365 przedsiębiorstwa.

![Przewodniki laboratorium testowego dotyczące chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Kliknij [tutaj,](../downloads/Microsoft365EnterpriseTLGStack.pdf) aby uzyskać wizualną mapę do wszystkich artykułów w p Microsoft 365 przewodników laboratorium testowego dla przedsiębiorstw.
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Etap 1. Tworzenie środowiska testowego Microsoft 365 przedsiębiorstwa

Jeśli chcesz tylko skonfigurować większe Microsoft 365 z minimalnymi wymaganiami, postępuj zgodnie z instrukcjami w tece Konfiguracja bazy [podstawowej](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Jeśli chcesz skonfigurować większe Microsoft 365 w symulowanym przedsiębiorstwie, postępuj zgodnie z instrukcjami w tece [uwierzytelnianie za pośrednictwem aplikacji](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Testowanie zwiększonych Microsoft 365 nie wymaga symulowanego środowiska testowania przedsiębiorstwa, które obejmuje symulowany intranet połączony z Internetem i synchronizację katalogów dla lasu Usługi domenowe w usłudze Active Directory (AD DS). Jest ona dostępna jako opcja, która umożliwia testowanie automatycznego licencjonowania i członkostwa w grupach oraz eksperymentowanie z nim w środowisku reprezentującym typową organizację. 

## <a name="phase-2-configure-increased-microsoft-365-security"></a>Etap 2. Konfigurowanie zwiększonych Microsoft 365 zabezpieczeń

W tej fazie zwiększysz poziom zabezpieczeń Microsoft 365 firmowego Microsoft 365 w środowisku testowania przedsiębiorstwa. Aby uzyskać dodatkowe informacje i ustawienia, zobacz [Konfigurowanie dzierżawy w celu zwiększenia zabezpieczeń](/office365/securitycompliance/tenant-wide-setup-for-increased-security).

### <a name="configure-sharepoint-online-to-block-apps-that-dont-support-modern-authentication"></a>Konfigurowanie SharePoint Online w celu blokowania aplikacji, które nie obsługują nowoczesnego uwierzytelniania

Aplikacje, które nie obsługują nowoczesnego uwierzytelniania, [](../security/office-365-security/microsoft-365-policies-configurations.md) nie mogą mieć zastosowanych konfiguracji tożsamości ani dostępu do urządzeń, co jest ważnym elementem zabezpieczania subskrypcji usługi Microsoft 365 i jej cyfrowych elementów. 

1. Przejdź do tego <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365</a> i zaloguj się do Microsoft 365 laboratorium testowego za pomocą konta administratora globalnego.
    
  - Jeśli używasz uproszczonego środowiska Microsoft 365, zaloguj się na komputerze lokalnym.
    
  - Jeśli używasz symulowanego środowiska testowego dla przedsiębiorstw Microsoft 365, użyj portalu [Azure Portal](https://portal.azure.com), aby nawiązać połączenie z maszyną wirtualną CLIENT1, a następnie zaloguj się z klienta CLIENT1.
 
2. Na nowej karcie **centrum administracyjne platformy Microsoft 365** w obszarze **Centra** administracyjne w lewym okienku nawigacji **kliknij pozycję SharePoint**.
3. Na nowej karcie **centrum SharePoint administracyjnego** wybierz **pozycję Kontrolka policiesAccess** > .<a href="https://go.microsoft.com/fwlink/?linkid=2185071" target="_blank"></a>
4. Wybierz **pozycję Aplikacje, które nie obsługują nowoczesnego uwierzytelniania**, wybierz pozycję **Zablokuj dostęp**, a następnie wybierz pozycję **Zapisz**.


### <a name="enable-defender-for-office-365-for-sharepoint-onedrive-for-business-and-microsoft-teams"></a>Włączanie usługi Defender Office 365 dla SharePoint, OneDrive dla Firm i Microsoft Teams

Program Defender Office 365 for SharePoint, OneDrive i Microsoft Teams chroni organizację przed nieumyślnie udostępnieniem złośliwych plików.

1. Przejdź do Centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">zabezpieczeń & zgodności</a> i zaloguj się przy użyciu konta administratora globalnego.

2. W lewym okienku nawigacji w obszarze **Zarządzanie zagrożeniami** kliknij pozycję **Zasady**, a następnie kliknij pozycję Sejf **załączników**. 

3. W **obszarze Ochrona plików w SharePoint, OneDrive i Microsoft Teams**. wybierz **pozycję Włącz atP dla SharePoint, OneDrive i Microsoft Teams**.

4. Kliknij **Zapisz**.


### <a name="enable-anti-malware"></a>Włączanie ochrony przed złośliwym oprogramowaniem

Złośliwe oprogramowanie składa się z wirusów i oprogramowania szpiegującego. Wirusy infekują inne programy i dane i rozpowszechniają się na komputerze, szukając programów do zainfekowania. Oprogramowanie szpiegujące to oprogramowanie, które zbiera informacje osobiste, takie jak informacje logowania i dane osobowe, i odsyła je autorowi złośliwego oprogramowania. 

Microsoft 365 ma wbudowane funkcje filtrowania spamu i złośliwego oprogramowania, które pomagają chronić wiadomości przychodzące i wychodzące przed złośliwym oprogramowaniem oraz chronić cię przed spamem. Aby uzyskać więcej informacji, zobacz [Ochrona przed spamem & ochrony przed złośliwym oprogramowaniem](../security/office-365-security/anti-spam-and-anti-malware-protection.md).

Aby upewnić się, że w przypadku plików z typami plików załączników jest przeprowadzane przetwarzanie chroniące przed złośliwym oprogramowaniem:

1. Kliknij przycisk wstecz w przeglądarce, aby wrócić do **strony** Zasady.
2. Kliknij **pozycję Ochrona przed złośliwym oprogramowaniem**.
3. Kliknij dwukrotnie zasady o nazwie **Domyślne**.
4. W **oknie zasad ochrony przed złośliwym** oprogramowaniem kliknij pozycję **Ustawienia**.
4. W **obszarze Filtr typowych typów załączników** wybierz pozycję **Wł**., a następnie kliknij przycisk **Zapisz**.


## <a name="phase-3-examine-the-security-dashboard"></a>Etap 3. Zbadanie pulpitu nawigacyjnego zabezpieczeń

Zarządzanie zagrożeniami w programie Microsoft 365 może ułatwić sterowanie dostępem do danych organizacji i zarządzanie nimi na urządzeniach przenośnych, chronić organizację przed utratą danych oraz chronić wiadomości przychodzące i wychodzące przed złośliwym oprogramowaniem i spamem. Zarządzanie zagrożeniami umożliwia również ochronę reputacji domeny i określanie, czy nadawcy podszywają się pod konta w domenie w sposób złośliwy. 

Aby wyświetlić pulpit nawigacyjny zabezpieczeń:

1. W razie potrzeby przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum zabezpieczeń & zgodności</a> i zaloguj się przy użyciu konta administratora globalnego.

2. W lewym okienku nawigacji w obszarze **Zarządzanie zagrożeniami** kliknij pozycję Pulpit **nawigacyjny**.

Przyjrzyj się dokładnie wszystkim kartom na pulpicie nawigacyjnym, aby zapoznać się z informacjami.

Aby uzyskać więcej informacji, zobacz [Pulpit nawigacyjny zabezpieczeń](../security/office-365-security/security-dashboard.md).


## <a name="phase-4-examine-microsoft-secure-score"></a>Etap 4. Badanie bezpiecznego wyniku firmy Microsoft

Raport Microsoft Secure Score przedstawia stan zabezpieczeń jako liczbę, która wskazuje Twój bieżący poziom w stosunku do funkcji dostępnych w subskrypcji. Jest to również lista działań udoskonalania, które można podjąć, aby poprawić swoje wyniki.

1. Utwórz nową kartę w przeglądarce, przejdź <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">do portalu Microsoft 365 Defender</a>, a następnie kliknij **pozycję Bezpieczny wynik**.
2. Na karcie **Omówienie**  sprawdź bieżący wynik bezpiecznego połączenia oraz porównanie go ze średnią globalną i subskrypcjami z podobną liczbą licencji.
3. Na **karcie Akcje udoskonalania** zapoznaj się z listą akcji, które można podjąć, aby zwiększyć wynik.

Aby uzyskać więcej informacji, zobacz [Microsoft Secure Score](../security/defender/microsoft-secure-score.md).

## <a name="next-steps"></a>Następne kroki

Poznaj dodatkowe [funkcje i możliwości](m365-enterprise-test-lab-guides.md#information-protection) ochrony informacji w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Microsoft 365 laboratorium testowego dla przedsiębiorstw](m365-enterprise-test-lab-guides.md)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Microsoft 365 dla przedsiębiorstw](/microsoft-365-enterprise/)
