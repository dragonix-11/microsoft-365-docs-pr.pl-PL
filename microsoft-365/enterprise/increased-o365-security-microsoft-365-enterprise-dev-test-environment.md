---
title: Zwiększone zabezpieczenia Microsoft 365 dla Microsoft 365 dla środowiska testowego przedsiębiorstwa
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Skorzystaj z tego przewodnika po laboratorium testowym, aby włączyć dodatkowe ustawienia zabezpieczeń Microsoft 365 Microsoft 365 dla środowiska testowego przedsiębiorstwa.
ms.openlocfilehash: 4c69fadd3fb3e6744fad850e76282ea2339f48ee
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100726"
---
# <a name="increased-microsoft-365-security-for-your-microsoft-365-for-enterprise-test-environment"></a>Zwiększone zabezpieczenia Microsoft 365 dla Microsoft 365 dla środowiska testowego przedsiębiorstwa

*Tego przewodnika laboratorium testowego można używać tylko w przypadku Microsoft 365 dla środowisk testowych przedsiębiorstwa.*

Instrukcje przedstawione w tym artykule umożliwiają skonfigurowanie dodatkowych ustawień Microsoft 365 w celu zwiększenia zabezpieczeń Microsoft 365 dla środowiska testowego przedsiębiorstwa.

![Przewodniki laboratorium testowego dla chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Kliknij [tutaj](../downloads/Microsoft365EnterpriseTLGStack.pdf), aby uzyskać wizualną mapę na wszystkie artykuły w stosie Microsoft 365 for enterprise Test Lab Guide.
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Faza 1. Tworzenie Microsoft 365 dla środowiska testowego przedsiębiorstwa

Jeśli chcesz skonfigurować zwiększone zabezpieczenia Microsoft 365 w sposób uproszczony z minimalnymi wymaganiami, postępuj zgodnie z instrukcjami w temacie [Uproszczona konfiguracja podstawowa](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Jeśli chcesz skonfigurować zwiększone zabezpieczenia Microsoft 365 w symulowanym przedsiębiorstwie, postępuj zgodnie z instrukcjami w temacie [Uwierzytelnianie przekazywane](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Testowanie zwiększonych zabezpieczeń Microsoft 365 nie wymaga symulowanego środowiska testowego przedsiębiorstwa, które obejmuje symulowany intranet połączony z Internetem i synchronizację katalogów dla lasu Active Directory Domain Services (AD DS). Jest ona dostępna tutaj jako opcja, dzięki czemu można przetestować automatyczne licencjonowanie i członkostwo w grupach i eksperymentować z nim w środowisku reprezentującym typową organizację. 

## <a name="phase-2-configure-increased-microsoft-365-security"></a>Faza 2. Konfigurowanie zwiększonych zabezpieczeń Microsoft 365

W tej fazie włączysz zwiększone zabezpieczenia Microsoft 365 dla Microsoft 365 dla środowiska testowego przedsiębiorstwa. Aby uzyskać dodatkowe szczegóły i ustawienia, zobacz [Konfigurowanie dzierżawy pod kątem zwiększonych zabezpieczeń](/office365/securitycompliance/tenant-wide-setup-for-increased-security).

### <a name="configure-sharepoint-online-to-block-apps-that-dont-support-modern-authentication"></a>Konfigurowanie usługi SharePoint Online w celu blokowania aplikacji, które nie obsługują nowoczesnego uwierzytelniania

Aplikacje, które nie obsługują nowoczesnego uwierzytelniania, nie mogą mieć [zastosowanych konfiguracji dostępu do tożsamości i urządzeń](../security/office-365-security/microsoft-365-policies-configurations.md), co jest ważnym elementem zabezpieczania subskrypcji Microsoft 365 i jej zasobów cyfrowych. 

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a> i zaloguj się do subskrypcji laboratorium testowego Microsoft 365 przy użyciu konta administratora globalnego.
    
  - Jeśli używasz uproszczonego środowiska testowego Microsoft 365, zaloguj się z komputera lokalnego.
    
  - Jeśli używasz symulowanego środowiska testowego Microsoft 365 przedsiębiorstwa, użyj [Azure Portal](https://portal.azure.com), aby nawiązać połączenie z maszyną wirtualną CLIENT1, a następnie zaloguj się z klienta CLIENT1.
 
2. Na nowej karcie **Centrum administracyjne platformy Microsoft 365** w obszarze **Centra administracyjne** w okienku nawigacji po lewej stronie kliknij pozycję **SharePoint**.
3. Na nowej karcie **centrum administracyjnego SharePoint** wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185071" target="_blank">**ZasadyKontrola**</a> >  dostępu.
4. Wybierz pozycję **Aplikacje, które nie obsługują nowoczesnego uwierzytelniania**, wybierz pozycję **Blokuj dostęp**, a następnie wybierz pozycję **Zapisz**.


### <a name="enable-defender-for-office-365-for-sharepoint-onedrive-for-business-and-microsoft-teams"></a>Włączanie Ochrona usługi Office 365 w usłudze Defender dla SharePoint, OneDrive dla Firm i Microsoft Teams

Ochrona usługi Office 365 w usłudze Defender SharePoint, OneDrive i Microsoft Teams chroni organizację przed nieumyślnym udostępnianiem złośliwych plików.

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum zgodności & zabezpieczeń</a> i zaloguj się przy użyciu konta administratora globalnego.

2. W okienku nawigacji po lewej stronie w obszarze **Zarządzanie zagrożeniami** kliknij pozycję **Zasady**, a następnie kliknij pozycję **Sejf Załączniki**. 

3. W obszarze **Ochrona plików w SharePoint, OneDrive i Microsoft Teams**. wybierz pozycję **Włącz usługę ATP dla SharePoint, OneDrive i Microsoft Teams**.

4. Kliknij **Zapisz**.


### <a name="enable-anti-malware"></a>Włączanie ochrony przed złośliwym oprogramowaniem

Złośliwe oprogramowanie składa się z wirusów i programów szpiegujących. Wirusy infekują inne programy i dane i rozprzestrzeniają się na całym komputerze w poszukiwaniu programów do zainfekowania. Oprogramowanie szpiegujące odnosi się do złośliwego oprogramowania, które zbiera dane osobowe, takie jak dane logowania i dane osobowe, i wysyła je z powrotem do autora złośliwego oprogramowania. 

Microsoft 365 ma wbudowane funkcje filtrowania złośliwego oprogramowania i spamu, które pomagają chronić przychodzące i wychodzące wiadomości przed złośliwym oprogramowaniem i chronić przed spamem. Aby uzyskać więcej informacji, zobacz [Ochrona przed spamem & ochrony przed złośliwym oprogramowaniem](../security/office-365-security/anti-spam-and-anti-malware-protection.md).

Aby upewnić się, że przetwarzanie chroniące przed złośliwym oprogramowaniem jest wykonywane w plikach z typowymi typami plików załączników:

1. Kliknij przycisk Wstecz w przeglądarce, aby wrócić do strony **Zasady** .
2. Kliknij **pozycję Ochrona przed złośliwym oprogramowaniem**.
3. Kliknij dwukrotnie zasady o nazwie **Domyślne**.
4. W oknie **Zasady ochrony przed złośliwym oprogramowaniem** kliknij pozycję **Ustawienia**.
4. W obszarze **Filtr typów załączników** wybierz pozycję **Włączone**, a następnie kliknij przycisk **Zapisz**.


## <a name="phase-3-examine-the-security-dashboard"></a>Faza 3. Sprawdzanie pulpitu nawigacyjnego zabezpieczeń

Zarządzanie zagrożeniami w Microsoft 365 może pomóc w kontrolowaniu dostępu urządzeń przenośnych do danych organizacji i zarządzaniu nimi, chronić organizację przed utratą danych oraz chronić przychodzące i wychodzące wiadomości przed złośliwym oprogramowaniem i spamem. Możesz również użyć zarządzania zagrożeniami, aby chronić reputację domeny i określić, czy nadawcy złośliwie podszywają się pod konta z domeny. 

Aby wyświetlić pulpit nawigacyjny zabezpieczeń:

1. W razie potrzeby przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum zgodności & zabezpieczeń</a> i zaloguj się przy użyciu konta administratora globalnego.

2. W okienku nawigacji po lewej stronie w obszarze **Zarządzanie zagrożeniami** kliknij pozycję **Pulpit nawigacyjny**.

Przyjrzyj się bliżej wszystkim kartom na pulpicie nawigacyjnym, aby zapoznać się z podanymi informacjami.

Aby uzyskać więcej informacji, zobacz [Pulpit nawigacyjny zabezpieczeń](../security/office-365-security/security-dashboard.md).


## <a name="phase-4-examine-microsoft-secure-score"></a>Faza 4. Badanie wskaźnika bezpieczeństwa firmy Microsoft

Wskaźnik bezpieczeństwa firmy Microsoft przedstawia stan zabezpieczeń jako liczbę, która wskazuje bieżący poziom w stosunku do funkcji dostępnych w subskrypcji. Zawiera również listę akcji poprawy, które można podjąć, aby poprawić swój wynik.

1. Utwórz nową kartę w przeglądarce, przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>, a następnie kliknij pozycję **Wskaźnik bezpieczeństwa**.
2. Na karcie **Przegląd**  zanotuj bieżący wskaźnik bezpieczeństwa i sposób porównywania go ze średnią globalną i subskrypcjami z podobną liczbą licencji.
3. Na karcie **Akcje poprawy** zapoznaj się z listą akcji, które można wykonać, aby zwiększyć swój wynik.

Aby uzyskać więcej informacji, zobacz [Microsoft Secure Score (Wskaźnik bezpieczeństwa firmy Microsoft](../security/defender/microsoft-secure-score.md)).

## <a name="next-steps"></a>Następne kroki

Zapoznaj się z dodatkowymi funkcjami i możliwościami [ochrony informacji](m365-enterprise-test-lab-guides.md#information-protection) w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Microsoft 365 dla przewodników laboratorium testowego w przedsiębiorstwie](m365-enterprise-test-lab-guides.md)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Dokumentacja dotycząca subskrypcji Microsoft 365 dla Przedsiębiorstw](/microsoft-365-enterprise/)
