---
title: Wprowadzenie do lokalnego Microsoft 365 ochrony przed utratą danych
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: how-to
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Konfigurowanie lokalnego Microsoft 365 ochrony przed utratą danych
ms.openlocfilehash: 1586489389931b3df19a1c84f0ae49ac7ff9c099
ms.sourcegitcommit: d37fce3b708ea5232b4102fd0e693f4bf17a8948
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/21/2022
ms.locfileid: "63013354"
---
# <a name="get-started-with-the-data-loss-prevention-on-premises-scanner"></a>Wprowadzenie do lokalnego skanera ochrony przed utratą danych

Ten artykuł zawiera informacje o wymaganiach wstępnych i konfiguracji skanera Microsoft 365 ochrony przed utratą danych.

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="skusubscriptions-licensing"></a>Licencjonowanie subskrypcji/licencji na subskrypcje sKU

Przed rozpoczęciem pracy ze skanerem lokalnym DLP należy potwierdzić swoją subskrypcję usługi [Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) i wszelkie dodatki. Do konta administratora, który konfiguruje reguły DLP, należy przypisać jedną z następujących licencji:

- Microsoft 365 E5
- Zgodność platformy Microsoft 365 E5
- Microsoft 365 E5 i zarządzanie & informacjami 


Aby uzyskać szczegółowe informacje o licencjonowaniu, zobacz: [Microsoft 365 licencjonowania w celu zapewnienia zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

> [!IMPORTANT]
> Wszyscy użytkownicy, którzy współtworzą zeskanowaną lokalizację, dodając pliki lub korzystając z plików, muszą mieć licencję, nie tylko użytkownik skanera.

### <a name="permissions"></a>Uprawnienia

Dane ze skanera lokalnego DLP można wyświetlać w [Eksploratorze aktywności](data-classification-activity-explorer.md). Istnieją cztery role, które przyznają uprawnienia do Eksploratora aktywności — konto, za pomocą których uzyskujesz dostęp do danych, musi być członkiem dowolnej z nich.

- Administrator globalny
- Administrator zgodności
- Administrator zabezpieczeń
- Administrator danych zgodności

#### <a name="roles-and-role-groups-in-preview"></a>Role i grupy ról w wersji Preview

W wersji Preview są dostępne role i grupy ról, które możesz przetestować, aby precyzyjnie dostosować kontrolki dostępu.

Oto lista dostępnych w wersji Microsoft Information Protection (MIP), które są dostępne w wersji zapoznawczej. Aby dowiedzieć się więcej na ich temat, zobacz [Role w Centrum & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Administrator ochrony informacji
- Analityk ochrony informacji
- Ochrona informacji
- Czytnik ochrony informacji

Poniżej znajdziesz listę grup ról miP, które są dostępne w wersji Preview. Aby dowiedzieć się więcej na ten temat, [zobacz Grupy ról w Centrum & zabezpieczeń.](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Ochrona informacji
- Administratorzy ochrony informacji
- Analitycy ochrony informacji
- Schoweki ochrony informacji
- Czytniki informacji

### <a name="dlp-on-premises-scanner-prerequisites"></a>Wymagania wstępne lokalnego skanera DLP

- Skaner Azure Information Protection (AIP) implementuje dopasowywanie zasad DLP i wymuszanie zasad. Skaner jest instalowany jako część klienta AIP, więc instalacja musi spełniać wszystkie wymagania wstępne programu AIP, klienta AIP i ujednoliconego skanera etykiet.
- Wdeksuj klienta i skaner AIP. Aby uzyskać więcej informacji [Zainstaluj klienta ujednoliconego etykiet AIP](/azure/information-protection/rms-client/install-unifiedlabelingclient-app) i znak [], zobacz Konfigurowanie i instalowanie ujednoliconego skanera [etykiet usługi Azure Information Protection](/azure/information-protection/deploy-aip-scanner-configure-install).
- W dzierżawie musi być opublikowana co najmniej jedna etykieta i zasady, nawet jeśli wszystkie reguły wykrywania są oparte tylko na typach informacji poufnych.

## <a name="deploy-the-dlp-on-premises-scanner"></a>Wdrażanie lokalnego skanera DLP

1. Postępuj zgodnie z [procedurami w tece Instalowanie klienta ujednoliconego etykiet AIP](/azure/information-protection/rms-client/install-unifiedlabelingclient-app). 
2. Wykonaj procedury zawarte w [konfigurowaniu i instalowaniu ujednoliconego skanera etykiet usługi Azure Information Protection](/azure/information-protection/deploy-aip-scanner-configure-install) , aby ukończyć instalację skanera.
    1. Konfiguracja zadań odnajdowania sieci jest krokiem opcjonalnym. Możesz go pominąć i zdefiniować określone repozytoria do skanowania w zadaniu skanowania zawartości.
    2. Musisz utworzyć zadanie skanowania zawartości i określić repozytoria hostów plików, które muszą zostać ocenić przez aparat DLP.
    3. Włącz reguły DLP w utworzonym zadaniu skanowania zawartości i ustaw dla  opcji Wymuś wartość **Wyłączone, chyba** że chcesz przejść bezpośrednio do etapu wymuszania ochrony przed dlp.
3. Sprawdź, czy zadanie skanowania zawartości jest przypisane do odpowiedniego klastra. Jeśli nadal nie utworzysz zadania skanowania zawartości, utwórz nowe zadanie i przypisz je do klastru zawierającego węzły skanera.

4. Połączenie do rozszerzenia [Azure Information Protection w portalu Azure Portal](https://portal.azure.com/#blade/Microsoft_Azure_InformationProtection/DataClassGroupEditBlade/scannerProfilesBlade) i dodaj repozytoria do zadania skanowania zawartości, które będzie przeprowadzać skanowanie.

5. Aby uruchomić skanowanie, wykonaj jedną z następujących czynności:
    1. ustawianie harmonogramu skanera
    1. używanie opcji **ręcznego skanowania teraz** w portalu
    1. lub uruchom **polecenie cmdlet Start-AIPKan** programu PowerShell

   > [!IMPORTANT]
   > Pamiętaj, że skaner domyślnie uruchamia skanowanie różnicowe repozytorium, a pliki, które zostały już zeskanowane w poprzednim cyklu skanowania, zostaną pominięte, chyba że plik został zmieniony lub zainicjowano ponowne skanowanie. Pełne ponowne skanowanie można zainicjować za pomocą **opcji Ponownie uruchom** wszystkie pliki w interfejsie użytkownika lub **uruchamiając narzędzie Start-AIPKan-Reset**.

6.  Otwórz stronę [Ochrona przed utratą danych](https://compliance.microsoft.com/datalossprevention?viewid=policies) w centrum Microsoft 365 zgodności.

7. Wybierz **pozycję Utwórz zasady** i utwórz testowe zasady DLP. Jeśli [potrzebujesz pomocy w tworzeniu zasad,](create-a-dlp-policy-from-a-template.md) zobacz Tworzenie zasad DLP na podstawie szablonu. Pamiętaj, aby go uruchomić w teście, dopóki nie będziesz mieć pewności, jak będziesz mieć pewność, że ta funkcja będzie ci dobrze dostępna. Użyj tych parametrów zasad:
    1. W razie potrzeby zawęś zakres reguły skanera lokalnego DLP do określonych lokalizacji. Jeśli **zawęzsz** lokalizacje do pozycji **Wszystkie**, wszystkie pliki skanowane przez skaner będą podlegały regułom DLP dopasowywania i wymuszania.
    1. Podczas określania lokalizacji możesz użyć listy wykluczeń lub dołączeń. Możesz albo zdefiniować, że reguła ma znaczenie tylko dla ścieżek zgodnych z jednym ze wzorców wymienionych na liście dołączanych lub wszystkich plików, z wyjątkiem plików zgodnych ze wzorcem wymienionym na liście dołączanych. Nie są obsługiwane żadne ścieżki lokalne. Oto kilka przykładów prawidłowych ścieżek:
      - \\\server\share
      - \\\server\share\folder1\subfolderabc
      - \*\\folder1
      - \*tajny\*.docx
      - \*tajny\*.\*
      - https:// sp2010.local/sites/HR
      - \*https:///KADR 
    3. Oto kilka przykładów nieakceptowalnych wartości:
      - \*
      - \*\\a
      - Aaa
      - c:\
      - C:\test

> [!IMPORTANT]
> Lista wykluczeń ma pierwszeństwo przed listą dołączeń.

### <a name="viewing-dlp-on-premises-scanner-alerts-in-dlp-alerts-management-dashboard"></a>Wyświetlanie lokalnych alertów skanera DLP na pulpicie nawigacyjnym zarządzania alertami DLP

1. Otwórz stronę [Ochrona przed utratą danych w](https://compliance.microsoft.com/datalossprevention?viewid=policies) Centrum Microsoft 365 zgodności i wybierz pozycję **Alerty**.

2. Aby wyświetlić alerty dotyczące zasad DLP w punktach końcowych, zobacz procedury konfigurowania i wyświetlania alertów dotyczących zasad [DLP](dlp-configure-view-alerts-policies.md) .

### <a name="viewing-dlp-on-premises-scanner-in-activity-explorer-and-audit-log"></a>Wyświetlanie lokalnego skanera DLP w Eksploratorze działań i dzienniku inspekcji

> [!NOTE]
> Skaner lokalnych wymaga, aby włączono inspekcję. W Microsoft 365 inspekcja jest domyślnie włączona.

1. Otwórz stronę [Klasyfikacja danych dla](https://compliance.microsoft.com/dataclassification?viewid=overview) swojej domeny w centrum zgodności usługi Microsoft 365 i wybierz pozycję Eksplorator aktywności.

2. Zapoznaj się z procedurami w [tece Wprowadzenie do Eksploratora](data-classification-activity-explorer.md) aktywności, aby uzyskać dostęp do wszystkich danych lokalnych lokalizacji skanera i przefiltrować je.

3. Otwórz dziennik [inspekcji w Centrum zgodności](https://security.microsoft.com/auditlogsearch). Dopasowania reguł DLP są dostępne w interfejsie użytkownika dziennika inspekcji lub dostępne przez [program PowerShell Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) 


## <a name="next-steps"></a>Następne kroki
Po wdrożeniu zasad testowania dla lokalizacji lokalnych zasad DLP i wyświetlaniu danych aktywności w Eksploratorze aktywności możesz przejść do następnego kroku, w którym utworzysz zasady DLP chroniące poufne elementy.

- [Korzystanie z lokalnego programu DLP](dlp-on-premises-scanner-use.md)

## <a name="see-also"></a>Zobacz też

- [Dowiedz się więcej o lokalnym skanerze dlp](dlp-on-premises-scanner-learn.md)
- [Używanie skanera lokalnego DLP](dlp-on-premises-scanner-use.md)
- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md)
- [Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md)
- [Wprowadzenie do Eksploratora aktywności](data-classification-activity-explorer.md)
- [Microsoft 365 subskrypcji](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
