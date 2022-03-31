---
title: Wprowadzenie do rozszerzenia zgodności firmy Microsoft
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
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
description: Przygotowanie i wdrażanie rozszerzenia zgodności firmy Microsoft.
ms.openlocfilehash: 5ffd04ee0b89c2e920f55c3e6fbefbab4c82983e
ms.sourcegitcommit: db2ed146b46ade9ea62eed9cb8efff5fea7a35e6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2022
ms.locfileid: "64481391"
---
# <a name="get-started-with-microsoft-compliance-extension"></a>Wprowadzenie z rozszerzeniem zgodności firmy Microsoft

Skorzystaj z tych procedur, aby stosować rozszerzenie zgodności firmy Microsoft.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby można było korzystać z rozszerzenia zgodności firmy Microsoft, urządzenie musi być dołączane do funkcji DLP punktu końcowego. Zapoznaj się z tymi artykułami, jeśli jesteś nowym użytkownikm usługi DLP lub usługi DLP punktu końcowego.

- [Dowiedz się więcej o rozszerzeniu zgodności firmy Microsoft](dlp-chrome-learn-about.md)
- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md)
- [Twórz, testuj i dostrajaj zasady DLP](create-test-tune-dlp-policy.md)
- [Twórz zasady DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md)
- [Informacje na temat ochrony przed utratą danych w punkcie końcowym](endpoint-dlp-learn-about.md)
- [Wprowadzenie do ochrony przed utratą danych punktu końcowego](endpoint-dlp-getting-started.md)
- [Narzędzia i metody dołączania do Windows 10 urządzeniach](device-onboarding-overview.md)
- [Konfiguruj ustawienia serwera proxy urządzenia i połączenia internetowego dla usługi Information Protection](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection)
- [Korzystanie z ochrony przed utratą danych punktu końcowego](endpoint-dlp-using.md)

### <a name="skusubscriptions-licensing"></a>Licencjonowanie subskrypcji/licencji na subskrypcje sKU

Przed rozpoczęciem należy potwierdzić subskrypcję [Microsoft 365 i wszelkie](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) dodatki. Aby uzyskać dostęp do funkcji DLP punktu końcowego i korzystać z nich, musisz mieć jedną z tych subskrypcji lub dodatków.

- Microsoft 365 E5
- Microsoft 365 A5 (EDU)
- Microsoft 365 E5 zgodności
- Microsoft 365 A5 zgodności
- Microsoft 365 E5 i zarządzanie informacjami
- Microsoft 365 A5 i zarządzanie informacjami

Aby uzyskać szczegółowe wskazówki dotyczące licencjonowania, [zobacz Microsoft 365 licencjonowania w celu zapewnienia zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

- Twoja organizacja musi mieć licencję na DLP punktu końcowego
- Na urządzeniach musi być uruchomiona Windows 10 x64 kompilacja 1809 lub nowszy.
- Urządzenie musi mieć wersję klienta ochrony przed złośliwym oprogramowaniem: 4.18.2202.x lub nowszą. Sprawdź bieżącą wersję, otwierając **aplikację Zabezpieczenia Windows****, wybierz** ikonę Ustawienia, a następnie wybierz pozycję **Informacje**.


### <a name="permissions"></a>Uprawnienia

Dane z zasad DLP punktu końcowego można wyświetlać w [Eksploratorze aktywności](data-classification-activity-explorer.md). Istnieje siedem ról, które przyznają uprawnienia do Eksploratora aktywności — konto, za pomocą których uzyskujesz dostęp do danych, musi być członkiem dowolnej z nich.

- Administrator globalny
- Administrator zgodności
- Administrator zabezpieczeń
- Administrator danych dot. zgodności
- Czytelnik globalny
- Czytelnik zabezpieczeń
- Czytelnik raportów

#### <a name="roles-and-role-groups-in-preview"></a>Role i grupy ról w wersji Preview

W wersji Preview są dostępne role i grupy ról, które możesz przetestować, aby precyzyjnie dostosować kontrolki dostępu.

Oto lista dostępnych w wersji Microsoft Information Protection (MIP), które są dostępne w wersji zapoznawczej. Aby dowiedzieć się więcej na ich temat, zobacz [Role w Centrum & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Information Protection administratorem
- Information Protection analitykiem
- Information Protection Ciesom
- Information Protection czytnik zawartości ekranu

Poniżej znajdziesz listę grup ról miP, które są dostępne w wersji Preview. Aby dowiedzieć się więcej na ten temat, [zobacz Grupy ról w Centrum & zabezpieczeń.](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Information Protection
- Information Protection administratorzy
- Information Protection analityków
- Information Protection Się
- Information Protection czytelnicy

### <a name="overall-installation-workflow"></a>Całkowity przepływ pracy instalacji

Wdrażanie rozszerzenia zgodności firmy Microsoft jest wielofazowym procesem. Możesz zainstalować oprogramowanie na jednym komputerze na raz albo używać pakietu Microsoft Endpoint Manager lub zasady grupy w przypadku wdrożeń dla całej organizacji.

1. [Przygotuj swoje urządzenia](#prepare-your-devices).
2. [Selfhost programu Single Machine w konfiguracji podstawowej](#basic-setup-single-machine-selfhost)
3. [Wdrażanie przy użyciu Microsoft Endpoint Manager](#deploy-using-microsoft-endpoint-manager)
4. [Wdrażanie przy użyciu zasady grupy](#deploy-using-group-policy)
5. [Testowanie rozszerzenia](#test-the-extension)
6. [Wyświetlanie alertów DLP w przeglądarce Chrome za pomocą pulpitu nawigacyjnego zarządzania alertami](#use-the-alerts-management-dashboard-to-viewing-chrome-dlp-alerts)
7. [Wyświetlanie danych DLP przeglądarki Chrome w Eksploratorze aktywności](#viewing-chrome-dlp-data-in-activity-explorer)

### <a name="prepare-infrastructure"></a>Przygotowywanie infrastruktury

W przypadku rozszerzenia zgodności firmy Microsoft na wszystkich monitorowanych urządzeniach z systemem Windows 10 należy usunąć przeglądarkę Google Chrome z listy nieprzesłanych aplikacji i nieprzesłanych przeglądarek. Aby uzyskać więcej informacji, zobacz [Przeglądarki niedozwolone](dlp-configure-endpoint-settings.md#unallowed-browsers). Jeśli jest ona wprowadzana tylko na kilku urządzeniach, możesz pozostawić przeglądarkę Chrome na niedozwolonej liście przeglądarek lub aplikacji, których nie chcesz używać. Rozszerzenie zgodności firmy Microsoft ominie ograniczenia dotyczące obu list dla tych komputerów, na których je zainstalowano.

### <a name="prepare-your-devices"></a>Przygotowywanie urządzeń

1. Aby korzystać z urządzeń, skorzystaj z procedur  poruszanych w tych tematach:
    1. [Wprowadzenie do ochrony przed utratą danych punktu końcowego](endpoint-dlp-getting-started.md)
    1. [Urządzenia Windows 10 i Windows 11 urządzenia przenośne](device-onboarding-overview.md)
    1. [Konfiguruj ustawienia serwera proxy urządzenia i połączenia internetowego dla usługi Information Protection](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection)

### <a name="basic-setup-single-machine-selfhost"></a>Selfhost programu Single Machine w konfiguracji podstawowej

Jest to zalecana metoda.

1. Przejdź do [rozszerzenia zgodności firmy Microsoft — Chrome Web Store (google.com)](https://chrome.google.com/webstore/detail/microsoft-compliance-exte/echcggldkblhodogklpincgchnpgcdco).

2. Zainstaluj rozszerzenie, korzystając z instrukcji na Chrome Web Store pliku.

### <a name="deploy-using-microsoft-endpoint-manager"></a>Wdrażanie przy użyciu Microsoft Endpoint Manager

Użyj tej metody konfiguracji w przypadku wdrożeń w całej organizacji.

#### <a name="microsoft-endpoint-manager-force-install-steps"></a>Microsoft Endpoint Manager Wymuchij instalację

Przed dodaniem rozszerzenia zgodności firmy Microsoft do listy zainstalowanych rozszerzeń należy dodać rozszerzenia Chrome ADMX. Kroki tego procesu w programie Microsoft Endpoint Manager są dokumentowane przez firmę Google: Zarządzaj przeglądarką Chrome za pomocą programu [Microsoft Intune - Przeglądarka Google Chrome Enterprise Pomocy](https://support.google.com/chrome/a/answer/9102677?hl=en#zippy=%2Cstep-ingest-the-chrome-admx-file-into-intune).

 Po utworzeniu pliku ADMX można wykonać poniższe czynności w celu utworzenia profilu konfiguracji dla tego rozszerzenia.

1. Zaloguj się do centrum Microsoft Endpoint Manager administracyjnego (https://endpoint.microsoft.com).

2. Przejdź do profilów konfiguracji.

3. Wybierz **pozycję Utwórz profil**.

4. Wybierz **Windows 10** jako platformę.

5. Wybierz **pozycję Niestandardowy** jako typ profilu.

6. Wybierz **kartę Ustawienia** zaawansowanej.

7. Wybierz opcję **Dodaj**.

8. Wprowadź następujące informacje o zasadach.

    OMA-URI: `./Device/Vendor/MSFT/Policy/Config/Chrome~Policy~googlechrome~Extensions/ExtensionInstallForcelist`<br/>
    Typ danych: `String`<br/>
    Wartość: `<enabled/><data id="ExtensionInstallForcelistDesc" value="1&#xF000; echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx"/>`

9. Kliknij przycisk Utwórz.

### <a name="deploy-using-group-policy"></a>Wdrażanie przy użyciu zasady grupy

Jeśli nie chcesz używać funkcji Microsoft Endpoint Manager, możesz użyć zasad grupy, aby wdrożyć rozszerzenie zgodności firmy Microsoft w organizacji.

#### <a name="adding-the-chrome-extension-to-the-forceinstall-list"></a>Dodawanie rozszerzenia Chrome do listy ForceInstall

1. W edytorze zasady grupy zarządzaniem przejdź do twojej aplikacji OU.

2. Rozwiń następującą **ścieżkę Konfiguracja komputera/** > **użytkownikaPoliciesAdministracyjne** **szablony** >  >  administracyjneKlasyfikacyjne  >  szablony **administracyjneGoogleGoogle** >  **ChromeExtensions** > . Ta ścieżka może się różnić w zależności od konfiguracji.

3. Wybierz **pozycję Konfiguruj listę zainstalowanych rozszerzeń**.

4. Kliknij prawym przyciskiem myszy i wybierz **polecenie Edytuj**.

5. Wybierz **pozycję Włączone**.

6. Wybierz **pozycję Pokaż**.

7. W **obszarze** Wartość dodaj następujący wpis: `echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx`

8. Wybierz **przycisk OK,** a następnie przycisk **Zastosuj**.

### <a name="test-the-extension"></a>Testowanie rozszerzenia

#### <a name="upload-to-cloud-service-or-access-by-unallowed-browsers-cloud-egress"></a>Upload usługi w chmurze lub uzyskiwanie do nich dostępu za pomocą odblokowanych przeglądarek w chmurze Egress

1. Utwórz lub pobierz poufny element, a następnie spróbuj przekazać plik do jednej z domen usługi z ograniczeniami twojej organizacji. Poufne dane muszą być zgodne z jednym z naszych wbudowanych typów informacji poufnych [lub jednym](sensitive-information-type-entity-definitions.md) z typów informacji poufnych w organizacji. Otrzymasz wyskakujące powiadomienie dotyczące zasad DLP na testowym urządzeniu, które pokazuje, że ta akcja nie jest dozwolona, gdy plik jest otwarty.

#### <a name="testing-other-dlp-scenarios-in-chrome"></a>Testowanie innych scenariuszy zasad DLP w przeglądarce Chrome

Po usunięciu przeglądarki Chrome z listy niedozwolone przeglądarki/aplikacje możesz przetestować poniższe scenariusze, aby potwierdzić, że zachowanie spełnia wymagania Twojej organizacji:

- Kopiowanie danych z poufnego elementu do innego dokumentu przy użyciu Schowka
  - Aby przetestować, otwórz plik chroniony przed kopiowaniem do akcji schowka w przeglądarce Chrome i spróbuj skopiować dane z tego pliku.
  - Oczekiwany wynik: wyskakujące powiadomienie dotyczące zasad DLP wskazujące, że ta akcja nie jest dozwolona, gdy plik jest otwarty.
- Drukowanie dokumentu
  - Aby przetestować, otwórz plik chroniony przed akcjami drukowania w przeglądarce Chrome i spróbuj go wydrukować.
  - Oczekiwany wynik: wyskakujące powiadomienie dotyczące zasad DLP wskazujące, że ta akcja nie jest dozwolona, gdy plik jest otwarty.
- Kopiowanie na dysk USB, który można usunąć
  - Aby przetestować, spróbuj zapisać plik w magazynie multimediów, który można usunąć.
  - Oczekiwany wynik: wyskakujące powiadomienie dotyczące zasad DLP wskazujące, że ta akcja nie jest dozwolona, gdy plik jest otwarty.
- Kopiuj do udziału sieciowego
  - Aby przetestować, spróbuj zapisać plik w udziału sieciowym.
  - Oczekiwany wynik: wyskakujące powiadomienie dotyczące zasad DLP wskazujące, że ta akcja nie jest dozwolona, gdy plik jest otwarty.

### <a name="use-the-alerts-management-dashboard-to-viewing-chrome-dlp-alerts"></a>Wyświetlanie alertów DLP w przeglądarce Chrome za pomocą pulpitu nawigacyjnego zarządzania alertami

1. Otwórz stronę **Ochrona przed utratą danych** w centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a> i wybierz pozycję **Alerty**.

2. Aby wyświetlić alerty dotyczące zasad DLP w punktach końcowych, zobacz procedury konfigurowania i wyświetlania alertów dotyczących zasad [DLP](dlp-configure-view-alerts-policies.md) .

### <a name="viewing-chrome-dlp-data-in-activity-explorer"></a>Wyświetlanie danych DLP przeglądarki Chrome w Eksploratorze aktywności

1. Otwórz stronę [Klasyfikacja danych](https://compliance.microsoft.com/dataclassification?viewid=overview) dla swojej domeny w centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365 wybierz</a> **pozycję Eksplorator aktywności**.

2. Skorzystaj z procedur w te Wprowadzenie [w Eksploratorze](data-classification-activity-explorer.md) aktywności, aby uzyskać dostęp do wszystkich danych dla urządzeń z punktami końcowymi i filtrować je.

   > [!div class="mx-imgBorder"]
   > ![filtr Eksploratora aktywności dla urządzeń końcowych.](../media/endpoint-dlp-4-getting-started-activity-explorer.png)

### <a name="known-issues-and-limitations"></a>Znane problemy i ograniczenia

1. Tryb incognito nie jest obsługiwany i musi być wyłączony.

## <a name="next-steps"></a>Następne kroki

Teraz, gdy masz urządzenia ze swoim systemem i możesz wyświetlać dane dotyczące aktywności w Eksploratorze aktywności, możesz przejść do następnego kroku, w którym utworzysz zasady DLP chroniące poufne elementy.

- [Korzystanie z ochrony przed utratą danych punktu końcowego](endpoint-dlp-using.md)

## <a name="see-also"></a>Zobacz też

- [Dowiedz się więcej o ochronie przed utratą danych punktu końcowego](endpoint-dlp-learn-about.md)
- [Korzystanie z ochrony przed utratą danych punktu końcowego](endpoint-dlp-using.md)
- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md)
- [Twórz, testuj i dostrajaj zasady DLP](create-test-tune-dlp-policy.md)
- [Wprowadzenie w Eksploratorze aktywności](data-classification-activity-explorer.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/)
- [Narzędzia i metody dołączania do Windows 10 komputerów](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [Microsoft 365 subskrypcji](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Urządzenia przyłączone do usługi Azure AD](/azure/active-directory/devices/concept-azure-ad-join)
- [Pobierz nowy Microsoft Edge na podstawie Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
