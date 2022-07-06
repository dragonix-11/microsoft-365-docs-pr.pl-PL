---
title: Rozpocznij pracę z lokalnym skanerem w celu zapobiegania utracie danych
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
description: Konfigurowanie lokalnego skanera zapobiegania utracie danych
ms.openlocfilehash: a1bcebfb48a502a9d7c484d266d91fe105603f84
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625440"
---
# <a name="get-started-with-the-data-loss-prevention-on-premises-scanner"></a>Wprowadzenie do lokalnego skanera zapobiegania utracie danych

W tym artykule przedstawiono wymagania wstępne i konfigurację lokalnego skanera ochrony przed utratą danych usługi Microsoft Purview.

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="skusubscriptions-licensing"></a>Licencjonowanie jednostek SKU/subskrypcji

Przed rozpoczęciem pracy ze skanerem lokalnym DLP należy potwierdzić [subskrypcję platformy Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) i wszelkie dodatki. Konto administratora, które konfiguruje reguły DLP, musi mieć przypisaną jedną z następujących licencji:

- Microsoft 365 E5
- Zgodność platformy Microsoft 365 E5
- Microsoft 365 E5 Information Protection & ładu 


Aby uzyskać szczegółowe informacje o licencjonowaniu, zobacz: [Microsoft 365 licensing guidance for security & compliance (Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance))

> [!IMPORTANT]
> Wszyscy użytkownicy, którzy współtworzą zeskanowaną lokalizację, dodając pliki lub używając plików, muszą mieć licencję, a nie tylko użytkownika skanera.

### <a name="permissions"></a>Uprawnienia

Dane z lokalnego skanera DLP można wyświetlić w [Eksploratorze działań](data-classification-activity-explorer.md). Istnieją cztery role, które udzielają uprawnień do Eksploratora działań. Konto używane do uzyskiwania dostępu do danych musi być członkiem dowolnej z nich.

- Administrator globalny
- Administrator zgodności
- Administrator zabezpieczeń
- Administrator danych zgodności

#### <a name="roles-and-role-groups-in-preview"></a>Role i grupy ról w wersji zapoznawczej

W wersji zapoznawczej dostępne są role i grupy ról, które można przetestować, aby dostosować mechanizmy kontroli dostępu.

Oto lista odpowiednich ról w wersji zapoznawczej. Aby dowiedzieć się więcej na ich temat, zobacz [Role w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Information Protection Administracja
- analityk Information Protection
- badacz Information Protection
- czytelnik Information Protection

Oto lista odpowiednich grup ról, które są w wersji zapoznawczej. Aby dowiedzieć się więcej na temat programu , zobacz [Grupy ról w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Information Protection
- administratorzy Information Protection
- analitycy Information Protection
- Information Protection śledczy
- czytniki Information Protection

### <a name="dlp-on-premises-scanner-prerequisites"></a>Wymagania wstępne dotyczące skanera lokalnego DLP

- Skaner usługi Azure Information Protection (AIP) implementuje dopasowywanie zasad DLP i wymuszanie zasad. Skaner jest instalowany jako część klienta usługi AIP, więc instalacja musi spełniać wszystkie wymagania wstępne dotyczące usługi AIP, klienta usługi AIP i skanera ujednoliconego etykietowania usługi AIP.
- Wdróż klienta i skaner usługi AIP. Aby uzyskać więcej informacji[, zainstaluj klienta ujednoliconego etykietowania usługi AIP](/azure/information-protection/rms-client/install-unifiedlabelingclient-app) i [], zobacz [Konfigurowanie i instalowanie skanera ujednoliconego etykietowania usługi Azure Information Protection](/azure/information-protection/deploy-aip-scanner-configure-install).
- W dzierżawie musi być opublikowana co najmniej jedna etykieta i zasady, nawet jeśli wszystkie reguły wykrywania są oparte tylko na typach informacji poufnych.

## <a name="deploy-the-dlp-on-premises-scanner"></a>Wdrażanie lokalnego skanera DLP

1. Postępuj zgodnie z procedurami w [temacie Instalowanie klienta ujednoliconego etykietowania usługi AIP](/azure/information-protection/rms-client/install-unifiedlabelingclient-app). 
2. Postępuj zgodnie z procedurami opisanymi w temacie [Konfigurowanie i instalowanie skanera ujednoliconego etykietowania usługi Azure Information Protection](/azure/information-protection/deploy-aip-scanner-configure-install), aby ukończyć instalację skanera.
    1. Konfiguracja zadań odnajdywania sieci jest krokiem opcjonalnym. Można go pominąć i zdefiniować określone repozytoria do skanowania w zadaniu skanowania zawartości.
    2. Musisz utworzyć zadanie skanowania zawartości i określić repozytoria hostujące pliki, które muszą być oceniane przez aparat DLP.
    3. Włącz reguły DLP w utworzonym zadaniu skanowania zawartości i ustaw opcję **Wymuszaj** na **wartość Wyłączone**, chyba że chcesz przejść bezpośrednio do etapu wymuszania DLP.
3. Sprawdź, czy zadanie skanowania zawartości zostało przypisane do odpowiedniego klastra. Jeśli nadal nie utworzono zadania skanowania zawartości, utwórz nowe zadanie i przypisz je do klastra zawierającego węzły skanera.

4. Połącz się z [rozszerzeniem usługi Azure Information Protection w Azure Portal](https://portal.azure.com/#blade/Microsoft_Azure_InformationProtection/DataClassGroupEditBlade/scannerProfilesBlade) i dodaj repozytoria do zadania skanowania zawartości, które przeprowadzi skanowanie.

5. Wykonaj jedną z następujących czynności, aby uruchomić skanowanie:
    1. ustawianie harmonogramu skanera
    1. użyj opcji ręcznie **skanuj teraz** w portalu
    1. lub uruchom polecenie cmdlet **start-AIPScan** programu PowerShell

   > [!IMPORTANT]
   > Pamiętaj, że skaner domyślnie uruchamia skanowanie różnicowe repozytorium, a pliki, które zostały już przeskanowane w poprzednim cyklu skanowania, zostaną pominięte, chyba że plik został zmieniony lub zainicjowano pełne ponowne skanowanie. Pełne ponowne skanowanie można zainicjować przy użyciu opcji **Przeskanuj ponownie wszystkie pliki** w interfejsie użytkownika lub uruchamiając polecenie **Start-AIPScan-Reset**.

6.  Otwórz [stronę Ochrona przed utratą danych](https://compliance.microsoft.com/datalossprevention?viewid=policies) w portal zgodności Microsoft Purview.

7. Wybierz **pozycję Utwórz zasady** i utwórz testowe zasady DLP. Zobacz [Tworzenie zasad DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md) , jeśli potrzebujesz pomocy w tworzeniu zasad. Pamiętaj, aby uruchomić go w teście, dopóki nie będziesz mieć pewności z tą funkcją. Użyj następujących parametrów dla zasad:
    1. W razie potrzeby określ zakres reguły skanera lokalnego DLP do określonych lokalizacji. W przypadku określania **zakresu lokalizacji** na **Wszystkie** wszystkie pliki skanowane przez skaner będą podlegać dopasowywaniu i wymuszaniu reguł DLP.
    1. Podczas określania lokalizacji można użyć listy wykluczeń lub dołączania. Można zdefiniować, że reguła ma zastosowanie tylko do ścieżek pasujących do jednego z wzorców wymienionych na liście dołączania lub wszystkich plików, z wyjątkiem plików pasujących do wzorca wymienionego na liście dołączania. Żadne ścieżki lokalne nie są obsługiwane. Oto kilka przykładów prawidłowych ścieżek:
      - \\\server\share
      - \\\server\share\folder1\subfolderabc
      - \*\\folder1
      - \*.docx wpisu tajnego\*
      - \*wpis tajny\*.\*
      - https:// sp2010.local/sites/HR
      - \*https:///HR 
    3. Oto kilka przykładów niedopuszczalnych wartości:
      - \*
      - \*\\A
      - Aaa
      - C:\
      - C:\test

> [!IMPORTANT]
> Lista wykluczeń ma pierwszeństwo przed listą dołączań.

### <a name="viewing-dlp-on-premises-scanner-alerts-in-dlp-alerts-management-dashboard"></a>Wyświetlanie alertów skanera lokalnego DLP na pulpicie nawigacyjnym zarządzania alertami DLP

1. Otwórz [stronę Zapobieganie utracie danych](https://compliance.microsoft.com/datalossprevention?viewid=policies) w portal zgodności Microsoft Purview i wybierz pozycję **Alerty**.

2. Zapoznaj się z procedurami w temacie [How to configure and view alerts for your DLP policies to view alerts for your Endpoint DLP policies (Jak skonfigurować i wyświetlić alerty dla zasad DLP](dlp-configure-view-alerts-policies.md) punktu końcowego).

### <a name="viewing-dlp-on-premises-scanner-in-activity-explorer-and-audit-log"></a>Wyświetlanie lokalnego skanera DLP w eksploratorze aktywności i dzienniku inspekcji

> [!NOTE]
> Lokalny skaner wymaga włączenia inspekcji. W usłudze Microsoft 365 inspekcja jest domyślnie włączona.

1. Otwórz [stronę Klasyfikacja danych](https://compliance.microsoft.com/dataclassification?viewid=overview) dla domeny w portal zgodności Microsoft Purview i wybierz pozycję Eksplorator działań.

2. Zapoznaj się z procedurami w temacie [Wprowadzenie do Eksploratora działań](data-classification-activity-explorer.md) , aby uzyskać dostęp do wszystkich danych lokalnych lokalizacji skanera i filtrować je.

3. Otwórz [dziennik inspekcji w Centrum zgodności](https://security.microsoft.com/auditlogsearch). Dopasowania reguł DLP są dostępne w interfejsie użytkownika dziennika inspekcji lub dostępne w programie [PowerShell Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) 


## <a name="next-steps"></a>Następne kroki
Teraz, gdy wdrożono zasady testowania dla lokalizacji lokalnych DLP i można wyświetlać dane aktywności w Eksploratorze działań, możesz przejść do następnego kroku, w którym utworzysz zasady DLP chroniące poufne elementy.

- [Korzystanie z lokalnego protokołu DLP](dlp-on-premises-scanner-use.md)

## <a name="see-also"></a>Zobacz też

- [Dowiedz się więcej o lokalnym skanerze DLP](dlp-on-premises-scanner-learn.md)
- [Korzystanie ze skanera lokalnego DLP](dlp-on-premises-scanner-use.md)
- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md)
- [Twórz, testuj i dostrajaj zasady DLP](create-test-tune-dlp-policy.md)
- [Wprowadzenie do Eksploratora działań](data-classification-activity-explorer.md)
- [Subskrypcja platformy Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
