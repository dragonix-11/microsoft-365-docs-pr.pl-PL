---
title: Zarządzanie etykietami poufności w aplikacjach Office
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Informacje dla administratorów IT dotyczące zarządzania etykietami wrażliwości Office aplikacji klasycznych, mobilnych i sieci Web.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0ca67ecb87b48d551ec4fb740e8732b8196c872c
ms.sourcegitcommit: 7aa2441c1f2cc5b4b5495d6fdb993e563f86647f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2022
ms.locfileid: "64637923"
---
# <a name="manage-sensitivity-labels-in-office-apps"></a>Zarządzanie etykietami poufności w aplikacjach Office

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Po [opublikowaniu etykiet](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) wrażliwości w centrum etykiet Centrum zgodności platformy Microsoft 365 lub równoważnego są one wyświetlane w aplikacjach pakietu Office, aby użytkownicy klasyfikowali i chronili dane po ich utworzeniu lub edytowaniu.

Informacje zawarte w tym artykule ułatwiają pomyślne zarządzanie etykietami wrażliwości w Office aplikacjach. Na przykład określ minimalne wersje aplikacji potrzebne do obsługi wbudowanych etykiet i opis interakcji z ujednoliconym klientem usługi Azure Information Protection etykietami oraz zgodność z innymi aplikacjami i usługami.

## <a name="labeling-client-for-desktop-apps"></a>Klient etykiet dla aplikacji klasycznych

Aby używać etykiet wrażliwości wbudowanych w Office klasycznych dla komputerów Windows i Mac, musisz użyć subskrypcji pakietu Office. Ten klient etykiet nie obsługuje autonomicznych wersji Office, nazywanych czasami "Office bezterminową".

Jeśli nie możesz uaktualnić oprogramowania do wersji Aplikacje Microsoft 365 dla przedsiębiorstw dla wersji Office usługi Windows Office, możesz użyć klienta [azure Information Protection etykiet](/azure/information-protection/rms-client/aip-clientv2).

## <a name="support-for-sensitivity-label-capabilities-in-apps"></a>Obsługa możliwości wrażliwości etykiet w aplikacjach

W poniższych tabelach przedstawiono minimalne Office, które są wymagane do obsługi etykiet wrażliwości przy użyciu wbudowanych etykiet. Lub, jeśli funkcja etykiet jest w publicznej wersji zapoznawczej lub w przeglądzie w przyszłej wersji. Skorzystaj z [Microsoft 365,](https://aka.ms/MIPC/Roadmap) aby uzyskać szczegółowe informacje o nowych możliwościach, które zaplanowano w przyszłych wersjach.

Nowe wersje Office są udostępniane w różnych momentach dla różnych kanałów aktualizacji. Dla Windows otrzymasz nowe funkcje wcześniej, gdy będziesz w bieżącym kanale lub miesięcznym kanale Enterprise, a nie Semi-Annual Enterprise kanału. Minimalne numery wersji mogą też różnić się w poszczególnych kanałach aktualizacji. Aby uzyskać więcej informacji, zobacz [Omówienie kanałów aktualizacji dla Aplikacje Microsoft 365](/deployoffice/overview-update-channels) [i Historia aktualizacji Aplikacje Microsoft 365](/officeupdates/update-history-microsoft365-apps-by-date).

Nowe funkcje dostępne w prywatnej wersji zapoznawczej nie są uwzględnione w tabeli, ale możesz mieć możliwość dołączenia do tych wersji zapoznawczych przez nominowanie organizacji do Microsoft Information Protection [prywatnego programu zapoznawczego](https://aka.ms/mip-preview).

Office dla systemu iOS i Office dla systemu Android: Etykiety wrażliwości są [wbudowane w aplikacja pakietu Office](https://www.microsoft.com/en-us/microsoft-365/blog/2020/02/19/new-office-app-android-ios-available/).

Dodatkowe funkcje są dostępne po zainstalowaniu klienta azure Information Protection etykiet, który działa tylko na Windows komputerach. Aby uzyskać te szczegółowe informacje, [zobacz Porównanie klientów etykiet dla Windows komputerów](/azure/information-protection/rms-client/use-client#compare-the-labeling-clients-for-windows-computers).

> [!TIP]
> Podczas porównywania minimalnych wersji tabel z wersjami, które posiadasz, pamiętaj o typowych praktykach puszczania wersji, aby pomijać zera wiodące.
> 
> Na przykład masz wersję 4.2128.0 i przeczytasz, że wersja 4.7.1+ jest wersją minimalną. Dla ułatwienia porównania przeczytaj 4.7.1 (bez zer wiodących) jako 4. **0007.1** (a nie 4.**7000.1**). Wersja 4.2128.0 jest wyższa niż 4.0007.1, więc jest obsługiwana.

### <a name="sensitivity-label-capabilities-in-word-excel-and-powerpoint"></a>Funkcje etykiet wrażliwości w programie Word, Excel i PowerPoint

Wymienione na liście liczby to minimalne Office wymaganych wersji aplikacji dla poszczególnych funkcji. 

> [!NOTE]
> W Windows i kanale Semi-Annual Enterprise minimalne obsługiwane numery wersji mogą jeszcze nie zostać opublikowane. [Dowiedz się więcej](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions)
 
|Funkcja |Windows |Mac |iOS |Android |Web |
|-----------|-------:|----|----|--------|----|
|[Ręczne stosowanie, zmienianie lub usuwanie etykiety](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| Bieżący kanał: 1910+ <br /><br> Miesięczny Enterprise kanału: 1910+ <br /><br> Semi-Annual Enterprise kanału: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Tak — opt-in](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Stosowanie etykiety domyślnej](sensitivity-labels.md#what-label-policies-can-do) do nowych dokumentów                                         | Bieżący kanał: 1910+ <br /><br> Miesięczny Enterprise kanału: 1910+ <br /><br> Semi-Annual Enterprise kanału: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Tak — opt-in](sensitivity-labels-sharepoint-onedrive-files.md)                                                        |
|[Stosowanie etykiety domyślnej](sensitivity-labels.md#what-label-policies-can-do) do istniejących dokumentów | Wersja zapoznawcza: Wyświetlanie w bieżącym [kanale (wersja Preview)](https://office.com/insider) | Wersja zapoznawcza: Wyświetlanie w bieżącym [kanale (wersja Preview)](https://office.com/insider) | W trakcie przeglądu | W trakcie przeglądu | [Tak — opt-in](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Wymaganie justowania w celu zmiany etykiety](sensitivity-labels.md#what-label-policies-can-do)                     | Bieżący kanał: 1910+ <br /><br> Miesięczny Enterprise kanału: 1910+  <br /><br> Semi-Annual Enterprise kanału: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Tak — opt-in](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Link Podaj pomoc do niestandardowej strony pomocy](sensitivity-labels.md#what-label-policies-can-do)                       | Bieżący kanał: 1910+ <br /><br> Miesięczny Enterprise kanału: 1910+ <br /><br> Semi-Annual Enterprise kanału: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Tak — opt-in](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Oznaczanie zawartości](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | Bieżący kanał: 1910+ <br /><br> Miesięczny Enterprise kanału: 1910+ <br /><br> Semi-Annual Enterprise kanału: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Tak — opt-in](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Oznaczenia dynamiczne ze zmiennymi](#dynamic-markings-with-variables)                                              | Bieżący kanał: 2010+ <br /><br> Miesięczny Enterprise kanału: 2010+ <br /><br> Semi-Annual Enterprise kanału: 2102+ | 16.42+     | 2.42+ | 16.0.13328+ | [Tak — opt-in](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Przypisz uprawnienia teraz](encryption-sensitivity-labels.md#assign-permissions-now)                                 | Bieżący kanał: 1910+ <br /><br> Miesięczny Enterprise kanału: 1910+ <br /><br> Semi-Annual Enterprise kanału: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Tak — opt-in](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Umożliwianie użytkownikom przypisywania uprawnień: <br /> — Monituj użytkowników](encryption-sensitivity-labels.md#let-users-assign-permissions)                     |Bieżący kanał: 2004+ <br /><br> Miesięczny Enterprise kanału: 2004+ <br /><br> Semi-Annual Enterprise kanału: 2008+ | 16.35+   | W trakcie przeglądu   | W trakcie przeglądu         | W trakcie przeglądu                                                        |
|[Inspekcja działań użytkowników związanych z etykietami](#auditing-labeling-activities)                      | Bieżący kanał: 2011+ <br /><br> Miesięczny Enterprise kanału: 2011+ <br /><br> Semi-Annual Enterprise kanału: 2108+ | 16.43+ | 2.46+ | 16.0.13628+ | Tak |
|[Wymaganie od użytkowników stosowania etykiety do wiadomości e-mail i dokumentów](#require-users-to-apply-a-label-to-their-email-and-documents)   | Bieżący kanał: 2101+ <br /><br> Miesięczny Enterprise kanału: 2101+ <br /><br> Semi-Annual Enterprise kanału: 2108+ | 16.45+         | 2.47+ | 16.0.13628+ | [Tak — opt-in](sensitivity-labels-sharepoint-onedrive-files.md)                                            
|[Automatyczne stosowanie etykiety poufności do zawartości](apply-sensitivity-label-automatically.md) <br /> — Używanie typów informacji poufnych                    | Bieżący kanał: 2009+ <br /><br> Miesięczny Enterprise kanału: 2009+ <br /><br> Semi-Annual Enterprise kanału: 2102+ | 16.44+ | W trakcie przeglądu | W trakcie przeglądu | [Tak — opt-in](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Automatyczne stosowanie etykiety poufności do zawartości](apply-sensitivity-label-automatically.md) <br /> - Korzystanie z klasyfikatorów przeszkolnych                    | Bieżący kanał: 2105+ <br /><br> Miesięczny Enterprise kanału: 2105+ <br /><br> Semi-Annual Enterprise kanału: 2108+ | 16.49+ | W trakcie przeglądu | W trakcie przeglądu | [Tak — opt-in](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Obsługa współtworzeń i autozazawów](sensitivity-labels-coauthoring.md) dla dokumentów oznaczonych i zaszyfrowanych | Bieżący kanał: 2107+ <br /><br> Miesięczny Enterprise kanał: 2107+ <br /><br> Semi-Annual Enterprise kanału: 2202+ |  16.51+ | Wersja przedpremierowa: 2,58+ po [wybrali opcję](sensitivity-labels-coauthoring.md#opt-in-to-the-preview-of-co-authoring-for-ios-and-android) | Wersja przedpremierowa: 16.0.14931 lub więcej, gdy [się na to zdecydujesz](sensitivity-labels-coauthoring.md#opt-in-to-the-preview-of-co-authoring-for-ios-and-android) | [Tak — opt-in](sensitivity-labels-sharepoint-onedrive-files.md) |


### <a name="sensitivity-label-capabilities-in-outlook"></a>Funkcje etykiet wrażliwości w programie Outlook

Wymienione na liście liczby to minimalne Office wymaganych wersji aplikacji dla poszczególnych funkcji. 

> [!NOTE]
> W Windows i kanale Semi-Annual Enterprise minimalne obsługiwane numery wersji mogą jeszcze nie zostać opublikowane. [Dowiedz się więcej](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions)

|Funkcja |Outlook dla Windows |Outlook dla komputerów Mac |Outlook w systemie iOS |Outlook w systemie Android |Outlook on the web |
|-----------|-------------------:|----------------|---------------|-------------------|-------------------|
|[Ręczne stosowanie, zmienianie lub usuwanie etykiety](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| Bieżący kanał: 1910+ <br /><br> Miesięczny Enterprise kanału: 1910+ <br /><br> Semi-Annual Enterprise kanału: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Tak               |
|[Stosowanie etykiety domyślnej](sensitivity-labels.md#what-label-policies-can-do)                                         | Bieżący kanał: 1910+ <br /><br> Miesięczny Enterprise kanału: 1910+ <br /><br> Semi-Annual Enterprise kanału: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Tak               |
|[Wymaganie justowania w celu zmiany etykiety](sensitivity-labels.md#what-label-policies-can-do)                     | Bieżący kanał: 1910+ <br /><br> Miesięczny Enterprise kanału: 1910+ <br /><br> Semi-Annual Enterprise kanału: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Tak               |
|[Link Podaj pomoc do niestandardowej strony pomocy](sensitivity-labels.md#what-label-policies-can-do)                       | Bieżący kanał: 1910+ <br /><br> Miesięczny Enterprise kanału: 1910+ <br /><br> Semi-Annual Enterprise kanału: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Tak               |
|[Oznaczanie zawartości](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | Bieżący kanał: 1910+ <br /><br> Miesięczny Enterprise kanału: 1910+ <br /><br> Semi-Annual Enterprise kanału: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Tak               |
|[Oznaczenia dynamiczne ze zmiennymi](#dynamic-markings-with-variables)                                              | Bieżący kanał: 1910+ <br /><br> Miesięczny Enterprise kanału: 1910+ <br /><br> Semi-Annual Enterprise kanału: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Tak               |
|[Przypisz uprawnienia teraz](encryption-sensitivity-labels.md#assign-permissions-now)                                 | Bieżący kanał: 1910+ <br /><br> Miesięczny Enterprise kanału: 1910+ <br /><br> Semi-Annual Enterprise kanału: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Tak               |
|[Umożliwianie użytkownikom przypisywania uprawnień: <br /> — Nie przesyłaj dalej](encryption-sensitivity-labels.md#let-users-assign-permissions)                     | Bieżący kanał: 1910+ <br /><br> Miesięczny Enterprise kanału: 1910+ <br /><br> Semi-Annual Enterprise kanału: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Tak               |
|[Umożliwianie użytkownikom przypisywania uprawnień: <br /> — Tylko szyfrowanie](encryption-sensitivity-labels.md#let-users-assign-permissions)  | Bieżący kanał: 2011+ <br /><br> Miesięczny Enterprise kanału: 2011+ <br /><br> Semi-Annual Enterprise kanału: 2108+ | 16.48+ <sup>\*</sup> | 4.2112.0+  | 4.2112.0+ | Tak |
|[Wymaganie od użytkowników stosowania etykiety do wiadomości e-mail i dokumentów](#require-users-to-apply-a-label-to-their-email-and-documents)   | Bieżący kanał: 2101+ <br /><br> Miesięczny Enterprise kanału: 2101+ <br /><br> Semi-Annual Enterprise kanału: 2108+ | 16.43+ <sup>\*</sup>                    | 4.2111+            | 4.2111+                | Tak                |
|[Inspekcja działań użytkowników związanych z etykietami](#auditing-labeling-activities) | Bieżący kanał: 2011+ <br /><br> Miesięczny Enterprise kanału: 2011+ <br /><br> Semi-Annual Enterprise kanału: 2108+ | 16.51+ <sup>\*</sup> | 4.2126+ | 4.2126+ | Tak |
|[Automatyczne stosowanie etykiety poufności do zawartości](apply-sensitivity-label-automatically.md) <br /> — Używanie typów informacji poufnych                    | Bieżący kanał: 2009+ <br /><br> Miesięczny Enterprise kanału: 2009+ <br /><br> Semi-Annual Enterprise kanału: 2102+ | 16.44+ <sup>\*</sup>                    | W trakcie przeglądu           | W trakcie przeglądu               | Tak |
|[Automatyczne stosowanie etykiety poufności do zawartości](apply-sensitivity-label-automatically.md) <br /> - Korzystanie z klasyfikatorów przeszkolnych                    | Bieżący kanał: 2105+ <br /><br> Miesięczny Enterprise kanału: 2105+ <br /><br> Semi-Annual Enterprise kanału: 2108+ | 16.49+ | W trakcie przeglądu           | W trakcie przeglądu               | Tak |
|[Różne ustawienia etykiet domyślnych i obowiązkowych etykiet](#outlook-specific-options-for-default-label-and-mandatory-labeling)                    | Bieżący kanał: 2105+ <br /><br> Miesięczny Enterprise kanału: 2105+ <br /><br> Semi-Annual Enterprise kanału: 2108+ | 16.43+ <sup>\*</sup>                   | 4.2111+           | 4.2111+               | Tak |
|

**Przypisy dolne:**

<sup>\*</sup>Wymaga [nowej Outlook dla komputerów Mac](https://support.microsoft.com/office/the-new-outlook-for-mac-6283be54-e74d-434e-babb-b70cefc77439)


## <a name="office-built-in-labeling-client-and-other-labeling-solutions"></a>Office wbudowany klient etykiet i inne rozwiązania do oznaczania etykiet

Wbudowany Office etykiet pobiera etykiety wrażliwości i ustawienia zasad wrażliwości z Centrum zgodności platformy Microsoft 365. 

Aby używać Office etykiet, musisz opublikować jedną lub więcej zasad etykiet dla użytkowników z Centrum zgodności oraz obsługiwaną wersję pakietu [Office](#support-for-sensitivity-label-capabilities-in-apps).[](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)

Jeśli oba te warunki są spełnione, ale musisz wyłączyć wbudowane etykiety w Windows Office, użyj zasady grupy ustawienia:

1. Przejdź do **konfiguracji użytkownika/szablonów administracyjnych/Microsoft Office 2016/Security Ustawienia**.

2. Ustaw **ustawienie Użyj funkcji wrażliwości w Office, aby zastosować etykiety wrażliwości i wyświetlić je jako** **0**. 
 
Wdąć to ustawienie przy zasady grupy lub przy użyciu usługi Office [zasad chmury](/DeployOffice/overview-office-cloud-policy-service). To ustawienie dzieje się po ponownym uruchomieniu Office aplikacji. 

Ponieważ to ustawienie jest specyficzne dla aplikacji pakietu Windows Office, nie ma Windows wpływu na inne aplikacje, które obsługują etykiety wrażliwości (takie jak Power BI) ani inne platformy (takie jak system macOS, urządzenia przenośne i Office dla sieci web). Jeśli nie chcesz, aby niektórzy lub wszyscy użytkownicy widzili etykiet wrażliwości i używali ich na wszystkich aplikacjach, wszystkich platformach, nie przypisuj tym użytkownikom zasad etykiet wrażliwości. 

### <a name="office-built-in-labeling-client-and-the-azure-information-protection-client"></a>Office wbudowany klient etykiet i klient usługi Azure Information Protection etykiet

Jeśli na komputerach z systemem Windows Information Protection jest zainstalowany klient usługi [Azure Information Protection (AIP](/azure/information-protection/rms-client/aip-clientv2)), etykiety wbudowane są domyślnie wyłączone w aplikacjach pakietu Windows Office, które je [obsługują](#labeling-client-for-desktop-apps). Ponieważ na etykietach wbudowanych nie jest używany dodatek Office, tak jak jest używany przez klienta AIP, ich zaletą jest większa stabilność i większa wydajność. Obsługują one również najnowsze funkcje, takie jak zaawansowane klasyfikatory.

Aby dowiedzieć się więcej na temat opcji oznaczania etykiet za pomocą klienta AIP, zobacz Dlaczego warto wybrać wbudowaną etykietę MIP w dodatku [AIP dla aplikacji Office AIP](sensitivity-labels-aip.md).

## <a name="office-file-types-supported"></a>Office obsługiwane typy plików

Office, które mają wbudowane etykiety dla plików programów Word, Excel i PowerPoint obsługują format Open XML (taki jak .docx i .xlsx), ale nie format Microsoft Office 97–2003 (na przykład .doc i .xls), format Open Document (na przykład odt i ods) lub inne formaty. Jeśli typ pliku nie jest obsługiwany dla wbudowanych etykiet, przycisk Charakter nie jest  dostępny w aplikacja pakietu Office.

Klient ujednoliconej Information Protection Azure obsługuje zarówno format Open XML, jak i format Microsoft Office 97–2003. Aby uzyskać więcej informacji, zobacz Typy plików obsługiwane przez Information Protection [Azure i ujednoliconego](/azure/information-protection/rms-client/clientv2-admin-guide-file-types) klienta etykiet w przewodniku administracyjnym tego klienta.

Aby uzyskać informacje na temat innych rozwiązań etykiet, sprawdź w dokumentacji obsługiwane typy plików.

## <a name="protection-templates-and-sensitivity-labels"></a>Szablony ochrony i etykiety wrażliwości

Szablony [ochrony zdefiniowane przez](/azure/information-protection/configure-policy-templates) administratora, takie jak zdefiniowane dla szyfrowania wiadomości Office 365, nie są widoczne w aplikacjach pakietu Office podczas korzystania z wbudowanych etykiet. To uproszczone środowisko odzwierciedla, że nie trzeba wybierać szablonu ochrony, ponieważ te same ustawienia są zawarte w etykietach wrażliwości z włączonym szyfrowaniem.

Jeśli używasz polecenia cmdlet [New-Label](/powershell/module/exchange/new-label) z parametrem *EncryptionTemplateId* , możesz przekonwertować istniejący szablon na etykietę wrażliwości.

## <a name="information-rights-management-irm-options-and-sensitivity-labels"></a>Opcje usługi Zarządzanie prawami do informacji (IRM) i etykiety wrażliwości

Etykiety wrażliwości skonfigurowane do stosowania szyfrowania usuwają złożoność użytkowników, określając ich własne ustawienia szyfrowania. W wielu Office zarządzanie prawami do informacji (IRM) nadal użytkownicy mogą ręcznie konfigurować te indywidualne ustawienia szyfrowania. Na przykład dla Windows aplikacji:

- W przypadku dokumentu: **FileInfoProtect** >  >  **DocumentRestrict Access** > 
- w przypadku wiadomości e-mail: **Na karcie Opcje** kliknij > **szyfruj** 
  
Gdy użytkownicy na początku oznaczą etykietą dokument lub wiadomość e-mail, mogą zastąpić ustawienia konfiguracji etykiet własnymi ustawieniami szyfrowania. Przykład:

- Użytkownik stosuje **etykietę Confidential \ All Employees** do dokumentu, a ta etykieta jest skonfigurowana do stosowania ustawień szyfrowania dla wszystkich użytkowników w organizacji. Następnie użytkownik ręcznie konfiguruje ustawienia usługi IRM w celu ograniczenia dostępu do użytkownika spoza organizacji. Wynikiem końcowy jest dokument o etykiecie Poufne **\** Wszyscy pracownicy i zaszyfrowany, ale użytkownicy w Twojej organizacji nie mogą go otworzyć zgodnie z oczekiwaniami.

- Użytkownik stosuje etykietę **Confidential \ Recipients Only** (Tylko adresaci) do wiadomości e-mail i ta wiadomość e-mail jest skonfigurowana do stosowania ustawienia szyfrowania **Nie przesyłaj dalej**. W Outlook następnie ręcznie wybiera ustawienie usługi IRM dla opcji Tylko szyfrowanie. Końcowy rezultat jest taki, że mimo że wiadomość e-mail pozostaje zaszyfrowana, może zostać przesyłana dalej przez adresatów, mimo że ma etykietę **Poufne \ Tylko adresaci** .
    
    Jedynym wyjątkiem od Outlook w sieci Web opcji **z menu** Szyfruj jest to, że użytkownik nie może wybrać, kiedy aktualnie wybrana etykieta ma zastosowanie szyfrowanie.

- Użytkownik zastosuje **etykietę Ogólne** do dokumentu i ta etykieta nie jest skonfigurowana do stosowania szyfrowania. Następnie użytkownik ręcznie konfiguruje ustawienia usługi IRM w celu ograniczenia dostępu do dokumentu. Wynikiem końcowy jest dokument z etykietą Ogólne, ale który  również stosuje szyfrowanie, aby niektórzy użytkownicy nie mogą go otworzyć zgodnie z oczekiwaniami.

Jeśli dokument lub wiadomość e-mail jest już oznaczona etykietą, użytkownik może wykonać dowolną z tych czynności, jeśli zawartość nie jest jeszcze zaszyfrowana albo [](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) ma odpowiednie użycie Eksportowanie lub Pełna kontrola. 

Aby zapewnić bardziej spójne środowisko etykiet z zrozumiałym raportowaniem, podaj odpowiednie etykiety i wskazówki dla użytkowników dotyczące stosowania tylko etykiet w celu ochrony dokumentów i wiadomości e-mail. Przykład:

- W przypadku wyjątków, w których użytkownicy muszą przypisywać własne uprawnienia, podaj etykiety, [które umożliwiają użytkownikom przypisywanie własnych uprawnień](encryption-sensitivity-labels.md#let-users-assign-permissions). 

- Zamiast ręcznego usuwania szyfrowania przez użytkowników po wybraniu etykiety, która stosuje szyfrowanie, udostępnij etykietę podrzędną, gdy użytkownicy potrzebują etykiety z taką samą klasyfikacją, ale bez szyfrowania. Na przykład:
    - **Poufne \ Wszyscy pracownicy**
    - **Poufne \ Każdy (bez szyfrowania)**

- Rozważ wyłączenie ustawień usługi IRM, aby uniemożliwić użytkownikom ich wybieranie:
    - Outlook dla Windows: 
        - Klucze rejestru (DWORD:00000001) *DisableDNF* *i DisableEO* z HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Common\DRM
        - Upewnij się, że zasady grupy opcji **Konfiguruj domyślne szyfrowanie przycisku** Szyfruj nie jest skonfigurowane
    - Outlook dla komputerów Mac: 
        - Keys *DisableEncryptOnly* *and DisableDoNotForward* security settings documented in [Set preferences for Outlook dla komputerów Mac](/DeployOffice/mac/preferences-outlook)
    - Outlook w sieci Web: 
        - Parameters *SimplifiedClientAccessDoNotForwardDisabled* and *SimplifiedClientAccessEncryptOnlyDisabled documented* for [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration)
    - Outlook dla systemów iOS i Android: Te aplikacje nie obsługują stosowania szyfrowania przez użytkowników bez etykiet, więc nic nie należy wyłączać.

> [!NOTE]
> Jeśli użytkownicy ręcznie usuwają szyfrowanie z dokumentu oznaczonego etykietą, który jest przechowywany w programie SharePoint lub OneDrive, i masz włączone etykiety wrażliwości dla plików Office w usługach [SharePoint i OneDrive](sensitivity-labels-sharepoint-onedrive-files.md), szyfrowanie etykiet zostanie automatycznie przywrócone przy następnym dostępie do dokumentu lub jego pobraniu. 


## <a name="apply-sensitivity-labels-to-files-emails-and-attachments"></a>Stosowanie etykiet wrażliwości do plików, wiadomości e-mail i załączników

Użytkownicy mogą zastosować tylko jedną etykietę na raz do każdego dokumentu lub wiadomości e-mail.

Jeśli oznaczysz etykietą wiadomość e-mail, która ma załączniki, dziedziczą one etykietę tylko wtedy, gdy etykieta, która ma zastosowanie do wiadomości e-mail, ma szyfrowanie, a załącznik jest dokumentem programu Office nie jest jeszcze zaszyfrowany. Dziedziczona etykieta stosuje szyfrowanie, dlatego załącznik staje się nowo zaszyfrowany.

Załącznik nie dziedziczy etykiet wiadomości e-mail, gdy etykieta zastosowana do wiadomości e-mail nie stosuje szyfrowania lub załącznik jest już zaszyfrowany.

Przykłady dziedziczenia etykiet, w przypadku których etykieta **Poufne** stosuje szyfrowanie, a etykieta **Ogólne** nie stosuje szyfrowania:

- Użytkownik tworzy nową wiadomość e-mail i **stosuje do tej** wiadomości etykietę Poufny. Następnie dodają dokument programu Word, który nie jest oznaczony etykietą ani zaszyfrowany. W wyniku dziedziczenia dokument ma nową etykietę **Poufne** i ma teraz zastosowane szyfrowanie.

- Użytkownik tworzy nową wiadomość e-mail i **stosuje do tej** wiadomości etykietę Poufny. Następnie dodają dokument programu Word z etykietą **Ogólne** , a ten plik nie jest zaszyfrowany. W wyniku dziedziczenia dokument zostaje oznaczony ponownie jako poufny, a teraz ma  zastosowane szyfrowanie na tej etykiecie.

## <a name="sensitivity-label-compatibility"></a>Zgodność etykiet wrażliwości

**Aplikacje z usługą RMS**. Jeśli otworzysz oznaczony i zaszyfrowany dokument lub wiadomość [e-mail](/azure/information-protection/requirements-applications#rms-enlightened-applications) w aplikacji z obsługą usługi RMS, która nie obsługuje etykiet wrażliwości, aplikacja nadal wymusza szyfrowanie i zarządzanie prawami.

Klient **usługi Azure Information Protection**: Możesz wyświetlać i zmieniać etykiety wrażliwości stosowane do dokumentów i wiadomości e-mail za pomocą wbudowanego klienta etykiet usługi Office, używając klienta usługi Azure Information Protection — i na drugi sposób.

**W innych wersjach programu Office**: Każdy autoryzowany użytkownik może otwierać dokumenty i wiadomości e-mail z etykietami w innych wersjach Office. Etykietę można jednak wyświetlić lub zmienić tylko w obsługiwanych Office wersji lub przy użyciu klienta usługi Azure Information Protection. Obsługiwane aplikacja pakietu Office są wymienione w [poprzedniej sekcji](#support-for-sensitivity-label-capabilities-in-apps).

## <a name="support-for-sharepoint-and-onedrive-files-protected-by-sensitivity-labels"></a>Obsługa SharePoint i OneDrive chronionych etykietami wrażliwości

Aby używać wbudowanego Office etykiet z programem Office w sieci Web do obsługi dokumentów w programie SharePoint lub OneDrive, upewnij się, że włączono etykiety wrażliwości dla plików Office w programach [SharePoint i OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

## <a name="support-for-external-users-and-labeled-content"></a>Obsługa użytkowników zewnętrznych i zawartości oznaczonej etykietą

Etykieta oznaczana dokumentem lub wiadomością e-mail jest przechowywana jako metadane, które zawierają dzierżawę i identyfikator GUID etykiety. Po otwarciu dokumentu lub wiadomości e-mail z etykietą przez aplikacja pakietu Office obsługującego etykiety wrażliwości te metadane są odczytywane i tylko wtedy, gdy użytkownik należy do tej samej dzierżawy, etykieta jest wyświetlana w jego aplikacji. Na przykład na wbudowanych etykietach dla aplikacji Word, PowerPoint i Excel etykieta jest wyświetlana na pasku stanu. 

Oznacza to, że jeśli udostępniasz dokumenty innej organizacji, która używa innych nazw etykiet, każda organizacja może zastosować i zobaczyć własną etykietę zastosowaną do dokumentu. Jednak następujące elementy z etykiety zastosowanej są widoczne dla użytkowników spoza organizacji:

- Oznaczenia zawartości. Gdy etykieta powoduje zastosowanie nagłówka, stopki lub znaku wodnego, są one dodawane bezpośrednio do zawartości i pozostają widoczne do momentu, aż ktoś je zmodyfikuje lub usunie.

- Nazwa i opis źródłowego szablonu ochrony na podstawie etykiety, która zastosować szyfrowanie. Informacje te są wyświetlane na pasku komunikatów u góry dokumentu w celu podania informacji o tym, kto jest uprawniony do otwierania dokumentu, i o prawach użytkowania tego dokumentu.

### <a name="sharing-encrypted-documents-with-external-users"></a>Udostępnianie zaszyfrowanych dokumentów użytkownikom zewnętrznym

Oprócz ograniczenia dostępu do użytkowników we własnej organizacji możesz rozszerzyć dostęp do dowolnego innego użytkownika, który ma konto w u Azure Active Directory. Jeśli jednak w organizacji są używane zasady dostępu warunkowego, zapoznaj się z dodatkowymi zagadnieniami [w](#conditional-access-policies) następnej sekcji.

Wszystkie Office i inne aplikacje [rms mogą](/azure/information-protection/requirements-applications#rms-enlightened-applications) otwierać zaszyfrowane dokumenty po pomyślnym uwierzytelnieniu użytkownika. 

Jeśli użytkownicy zewnętrzni nie mają konta w u Azure Active Directory, mogą uwierzytelnić się przy użyciu kont gości w Twojej dzierżawie. Tych kont gości można również używać do uzyskiwania dostępu do dokumentów udostępnionych w programie SharePoint lub OneDrive po włączeniu etykiet wrażliwości dla plików Office w programie [SharePoint](sensitivity-labels-sharepoint-onedrive-files.md) i OneDrive:

- Jedną z możliwości jest utworzenie tych kont gości samodzielnie. Możesz określić dowolny adres e-mail, który będzie już przez tych użytkowników używać. Na przykład adres w usłudze Gmail.
    
    Zaletą tej opcji jest możliwość ograniczenia dostępu i praw do określonych użytkowników, określając ich adresy e-mail w ustawieniach szyfrowania. Minusem jest obciążenie administracyjne związane z tworzeniem i koordynacją konta z konfiguracją etykiet.

- Innym rozwiązaniem jest korzystanie SharePoint i [OneDrive z usługą Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration), dzięki czemu konta gości są tworzone automatycznie, gdy użytkownicy korzystają z linków.
    
    Zaletą tej opcji jest minimalne obciążenie administracyjne, ponieważ konta są tworzone automatycznie i prostsza konfiguracja etykiet. W tym scenariuszu należy wybrać opcję szyfrowania [Dodaj](encryption-sensitivity-labels.md#requirements-and-limitations-for-add-any-authenticated-users) dowolnego uwierzytelnionego użytkownika, ponieważ adresy e-mail nie będą wcześniej poznane. Minusem jest to, że to ustawienie nie pozwala na ograniczenie praw dostępu i użytkowania do konkretnych użytkowników.

Użytkownicy zewnętrzni mogą również używać konta Microsoft do otwierania zaszyfrowanych dokumentów podczas korzystania z usług Windows i Aplikacje Microsoft 365 (dawniej [Office 365 apps](/deployoffice/name-change)) lub autonomicznej wersji programu Office 2019. Konta Microsoft, które są ostatnio obsługiwane dla innych platform, są również obsługiwane do otwierania zaszyfrowanych dokumentów w systemie macOS (Aplikacje Microsoft 365, wersja 16.42+), Android (wersja 16.0.13029+) i iOS (wersja 2.42+). Na przykład użytkownik w Twojej organizacji udostępnia zaszyfrowany dokument użytkownikowi spoza organizacji, a ustawienia szyfrowania określają adres e-mail usługi Gmail dla użytkownika zewnętrznego. Ten użytkownik zewnętrzny może utworzyć własne konto Microsoft, które używa swojego adresu e-mail w usłudze Gmail. Następnie, po zalogowaniu się przy użyciu tego konta, mogą oni otworzyć dokument i edytować go zgodnie z określonymi dla nich ograniczeniami użytkowania. Aby uzyskać przykład instruktażowy tego scenariusza, zobacz [Otwieranie i edytowanie chronionego dokumentu](/azure/information-protection/secure-collaboration-documents#opening-and-editing-the-protected-document).

> [!NOTE]
> Adres e-mail konta Microsoft musi być taki, jak określony w celu ograniczenia dostępu do ustawień szyfrowania.

Gdy użytkownik z kontem Microsoft otwiera zaszyfrowany dokument w ten sposób, automatycznie tworzy konto gościa dla dzierżawy, jeśli konto gościa o tej samej nazwie jeszcze nie istnieje. Jeśli konto gościa istnieje, można go następnie używać do otwierania dokumentów w usługach SharePoint i OneDrive przy użyciu programu Office w sieci Web oprócz otwierania zaszyfrowanych dokumentów z obsługiwanych aplikacji klasycznych i Office przenośnych.

W tym scenariuszu automatyczne konto gościa nie jest jednak tworzone natychmiast ze względu na opóźnienie replikacji. Jeśli w ustawieniach szyfrowania etykiet określisz osobiste adresy e-mail, zalecamy utworzenie odpowiednich kont gości w aplikacji Azure Active Directory. Następnie poukaj tym użytkownikom, że muszą oni użyć tego konta, aby otworzyć zaszyfrowany dokument z Twojej organizacji.

> [!TIP]
> Ponieważ nie masz pewności, czy użytkownicy zewnętrzni będą korzystać z obsługiwanej aplikacji klienckiej Office, linki udostępniania z usług SharePoint i OneDrive są udostępnianie po utworzeniu kont gościa (dla określonych użytkowników) lub podczas korzystania z integracji usług [SharePoint i OneDrive z usługami Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview)  (dla każdego uwierzytelnionego użytkownika) jest bardziej niezawodną metodą zapewnienia bezpiecznej współpracy z użytkownikami zewnętrznymi.

### <a name="conditional-access-policies"></a>Zasady dostępu warunkowego

Jeśli Twoja organizacja wdrożyła Azure Active Directory [dostęp warunkowy](/azure/active-directory/conditional-access/overview), sprawdź ich konfigurację. Jeśli zasady **obejmują Microsoft Azure Information Protection i** rozciągają się na użytkowników zewnętrznych, ci użytkownicy zewnętrzni muszą mieć konto gościa w Twojej dzierżawie, nawet jeśli mają konto usługi Azure AD w swojej dzierżawie.

Bez tego konta gościa nie będzie można otworzyć zaszyfrowanego dokumentu i zostanie wyświetlony komunikat o błędzie. Tekst wiadomości może informować o tym, że jego konto musi zostać dodane jako użytkownik zewnętrzny w dzierżawie, z nieprawidłowymi instrukcjami dla tego scenariusza: Wylogowanie i zalogowanie się ponownie przy użyciu innego **konta Azure Active Directory użytkownika**.

Jeśli nie możesz tworzyć i konfigurować kont gości w dzierżawie dla użytkowników zewnętrznych, którzy muszą otwierać dokumenty zaszyfrowane na etykietach, musisz usunąć usługę Azure Information Protection z zasad dostępu warunkowego lub wykluczyć użytkowników zewnętrznych z tych zasad.

Aby uzyskać więcej informacji na temat dostępu warunkowego i usługi Azure Information Protection, usługi szyfrowania używanej na etykietach wrażliwości, zobacz często zadawane pytanie: Usługa Azure Information Protection jest wymieniona jako dostępna aplikacja w chmurze do obsługi dostępu warunkowego — jak [to działa?](/azure/information-protection/faqs#i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work)

## <a name="when-office-apps-apply-content-marking-and-encryption"></a>Gdy Office zastosują oznaczanie i szyfrowanie zawartości

Office aplikacje stosują oznaczenia zawartości i szyfrowania przy użyciu etykiet wrażliwości w różny sposób, w zależności od aplikacji, z których korzystasz.

| Aplikacja | Oznaczanie zawartości | Szyfrowanie |
| --- | --- | --- |
| Word, Excel, PowerPoint na wszystkich platformach | Natychmiast | Natychmiast |
| Outlook dla komputerów PC i Mac | Po Exchange Online wysyła wiadomość e-mail | Natychmiast |
| Outlook w sieci Web, iOS i Android | Po Exchange Online wysyła wiadomość e-mail | Po Exchange Online wysyła wiadomość e-mail |
|

Rozwiązania, które stosują etykiety wrażliwości do plików Office, można to zrobić, stosując metadane etykiet do pliku. W tym scenariuszu zawartość oznaczana z konfiguracji etykiety nie jest wstawiana do pliku, ale zastosowano szyfrowanie. 

Po otwarciu tych plików w aplikacji klasycznej pakietu Office oznaczenia zawartości są automatycznie stosowane przez klienta azure Information Protection etykiet ujednoliconej etykiet podczas pierwszego zapisania pliku. Oznaczenia zawartości nie są automatycznie stosowane w przypadku korzystania z wbudowanych etykiet dla komputerów stacjonarnych, urządzeń przenośnych lub aplikacji sieci Web.

Scenariusze, które obejmują stosowanie etykiet wrażliwości poza Office aplikacji:

- Skaner, Eksplorator plików i program PowerShell z usługi Azure Information Protection klienta ujednoliconego oznaczania 

- Zasady automatycznego oznaczania etykiet dla SharePoint i OneDrive

- Wyeksportowano oznaczone i zaszyfrowane dane z aplikacji Power BI

- Microsoft Defender for Cloud Apps

W takich scenariuszach za pomocą aplikacji pakietu Office użytkownik z wbudowanymi etykietami może zastosować oznaczenia zawartości etykiet, tymczasowo usuwając lub zamieniając bieżącą etykietę, a następnie ponownie stosując oryginalną etykietę.

### <a name="dynamic-markings-with-variables"></a>Oznaczenia dynamiczne ze zmiennymi

> [!IMPORTANT]
> Jeśli Twoje Office nie obsługują tej funkcji, zamiast rozwiązując zmienne, zastosują one oznaczenia jako oryginalny tekst określony w konfiguracji etykiet.
> 
> Klient azure Information Protection etykiet obsługuje oznaczenia dynamiczne. Aby uzyskać informacje na temat Office wbudowanych etykiet, zobacz tabele w sekcji funkcje na [](#support-for-sensitivity-label-capabilities-in-apps) tej stronie, aby uzyskać informacje o minimalnych obsługiwanych wersjach.

Podczas konfigurowania etykiety wrażliwości na oznaczenia zawartości można używać następujących zmiennych w ciągu tekstowym nagłówka, stopki lub znaku wodnego:

| Zmienna | Opis | Przykład zastosowania etykiety |
| -------- | ----------- | ------- |
| `${Item.Label}` | Nazwa wyświetlana etykiety | **Ogólne**|
| `${Item.Name}` | Nazwa pliku lub temat wiadomości e-mail zawartości oznaczonej etykietą | **Sales.docx** |
| `${Item.Location}` | Ścieżka i nazwa pliku oznaczania dokumentu lub temat wiadomości e-mail z etykietą | **\\\Sales\2020\Q3\Report.docx**|
| `${User.Name}` | Nazwa wyświetlana użytkownika stosującego etykietę | **Szymon Wołosz** |
| `${User.PrincipalName}` | Główna nazwa użytkownika (UPN) w usłudze Azure AD użytkownika stosująca etykietę | **rsimone\@ contoso.com** |
| `${Event.DateTime}` | Data i godzina na etykiecie zawartości w lokalnej strefie czasowej użytkownika mającej zastosowanie etykiety w aplikacjach pakietu Microsoft 365 lub czasu uniwersalnego UTC (Coordinated Universal Time) dla usługi Office Online i zasad automatycznego oznaczania etykiet | **2020-08-10 13:30** |

> [!NOTE]
> W składni tych zmiennych jest rozróżniana wielkość liter.

#### <a name="setting-different-visual-markings-for-word-excel-powerpoint-and-outlook"></a>Ustawianie różnych oznaczeń wizualnych dla Excel, PowerPoint i innych Outlook

Jako dodatkową zmienną można konfigurować oznaczenia wizualne dla każdego typu aplikacji programu Office przy użyciu instrukcji zmiennej "If.App" w ciągu tekstowym oraz identyfikować typ aplikacji przy użyciu wartości **Word**, **Excel**, **PowerPoint** lub **Outlook**. Te wartości można także skracać, co jest konieczne, jeśli w jednej instrukcji If.App określić więcej niż jedną wartość.

Należy stosować następującą składnię:

```
${If.App.<application type>}<your visual markings text> ${If.End}
```

Podobnie jak w przypadku innych dynamicznych oznaczeń wizualnych w składni jest uwzględniana wielkość liter, która obejmuje skróty dla każdego typu aplikacji (WEPO).

Przykłady:

- **Ustawianie tekstu nagłówka tylko w dokumentach programu Word:**

    `${If.App.Word}This Word document is sensitive ${If.End}`

    W przypadku tylko nagłówków dokumentu programu Word etykieta powoduje zastosowanie tekstu nagłówka "Ten dokument programu Word jest poufny". Tekst nagłówka nie jest stosowany do Office aplikacji.

- **Ustaw tekst stopki dla programu Word, Excel, Outlook i inny tekst stopki dla PowerPoint:**

    `${If.App.WXO}This content is confidential. ${If.End}${If.App.PowerPoint}This presentation is confidential. ${If.End}`

    W programie Word, Excel i Outlook etykieta powoduje zastosowanie tekstu stopki "Ta zawartość jest poufna". Na PowerPoint etykieta powoduje zastosowanie tekstu stopki "Ta prezentacja jest poufna".

- **Ustaw określony tekst znaku wodnego dla programu Word i PowerPoint, a następnie tekst znaku wodnego dla programu Word, Excel i PowerPoint:**

    `${If.App.WP}This content is ${If.End}Confidential`

    W programie Word PowerPoint etykieta powoduje zastosowanie tekstu znaku wodnego "Ta zawartość jest poufna". W Excel etykieta powoduje zastosowanie tekstu znaku wodnego "Poufne". Na Outlook etykieta nie ma zastosowania do tekstu znaku wodnego, ponieważ znaki wodne jako znaki wizualne nie są obsługiwane w Outlook.

## <a name="require-users-to-apply-a-label-to-their-email-and-documents"></a>Wymaganie od użytkowników stosowania etykiety do wiadomości e-mail i dokumentów

> [!IMPORTANT]
> 
> Klient [ujednoliconej Information Protection Azure Information Protection](/azure/information-protection/rms-client/install-unifiedlabelingclient-app) tę konfigurację, która jest również znana jako obowiązkowa etykieta. Aby uzyskać informacje na temat Office wbudowanych aplikacji, zobacz tabele w sekcji funkcje na tej [](#support-for-sensitivity-label-capabilities-in-apps) stronie, aby uzyskać informacje o minimalnych wersjach.
>
> Aby użyć obowiązkowych etykiet w dokumentach, ale nie w wiadomościach e-mail, zapoznaj się z instrukcjami w następnej sekcji, w których wyjaśniono, jak skonfigurować Outlook e-mail.
> 
> Aby użyć obowiązkowych etykiet dla Power BI, zobacz Zasady dotyczące obowiązkowych etykiet [dla Power BI](/power-bi/admin/service-security-sensitivity-label-mandatory-label-policy).

Gdy ustawienie zasad Wymagaj od użytkowników stosowania etykiety do wiadomości e-mail i dokumentów jest zaznaczone, użytkownicy przypisani do zasad muszą wybrać i zastosować etykietę wrażliwości w następujących scenariuszach:

- W przypadku klienta usługi Azure Information Protection etykiet ujednoliconej:
    - W przypadku dokumentów (Word, Excel, PowerPoint): Po zapisaniu dokumentu bez etykiety lub zamknięciu go przez użytkowników.
    - W przypadku wiadomości e-Outlook): kiedy użytkownicy wysyłają wiadomość bez etykiety.

- Aby uzyskać etykiety wbudowane w Office aplikacji:
    - W przypadku dokumentów (Word, Excel, PowerPoint): Po otwarciu lub zapisaniu dokumentu bez etykiety.
    - W przypadku wiadomości e Outlook): kiedy użytkownicy wysyłają wiadomość e-mail bez etykiety.

Dodatkowe informacje dotyczące wbudowanych etykiet:

- Gdy użytkownik jest monitowany o dodanie etykiety wrażliwości, ponieważ otwiera dokument bez etykiety, może dodać etykietę lub otworzyć dokument w trybie tylko do odczytu.

- Gdy dzieje się obowiązkowe etykiety, użytkownicy nie mogą usuwać etykiet wrażliwości z dokumentów, ale mogą zmienić istniejącą etykietę.

Aby uzyskać wskazówki dotyczące tego, kiedy używać tego ustawienia, zobacz informacje o [ustawieniach zasad](sensitivity-labels.md#what-label-policies-can-do).

> [!NOTE]
> Jeśli oprócz obowiązkowych etykiet używasz domyślnego ustawienia zasad dotyczących etykiet dla dokumentów i wiadomości e-mail: 
>
> Etykieta domyślna zawsze ma pierwszeństwo przed etykietami obowiązkowymi. Jednak w przypadku dokumentów ujednolicony klient etykiet usługi Azure Information Protection stosuje etykietę domyślną do wszystkich dokumentów bez etykiet, a wbudowane etykiety — do nowych dokumentów, a nie do istniejących dokumentów bez etykiety. Ta różnica w zachowaniu oznacza, że w przypadku używania obowiązkowych etykiet z domyślnym ustawieniem etykiety użytkownicy prawdopodobnie będą monitowali o stosowanie etykiet wrażliwości częściej, gdy używają wbudowanych etykiet niż w przypadku korzystania z ujednoliconego klienta etykiet usługi Azure Information Protection.
> 
> Teraz wprowadzamy: Office, które korzystają z wbudowanych etykiet i obsługują etykietę domyślną dla istniejących dokumentów. Aby uzyskać szczegółowe informacje, zobacz [tabelę możliwości](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) dla programu Word, Excel i PowerPoint.

## <a name="outlook-specific-options-for-default-label-and-mandatory-labeling"></a>Outlook opcji etykiet domyślnych i obowiązkowych

W przypadku wbudowanych etykiet określ minimalne wersje programu Outlook, które obsługują te funkcje, za pomocą tabeli możliwości dla programu [Outlook](#sensitivity-label-capabilities-in-outlook) na tej stronie oraz wiersza Inne ustawienia etykiet domyślnych i obowiązkowych **etykiet.** Wszystkie wersje klienta usługi Azure Information Protection z ujednoliconą etykietą obsługują Outlook opcji.

Jeśli aplikacja Outlook obsługuje domyślne ustawienie etykiety inne niż domyślne ustawienie etykiet dla dokumentów:

- W konfiguracji zasad etykiet z Centrum zgodności platformy Microsoft 365 na stronie Zastosuj etykietę domyślną do wiadomości  e-mail: Możesz określić swój wybór etykiety wrażliwości, która będzie stosowana do wszystkich wiadomości e-mail bez etykiety, która nie jest etykietą domyślną. To ustawienie jest **niezależne od** domyślnego ustawienia Zastosuj tę etykietę do dokumentów na poprzedniej stronie Ustawienia **zasad dla dokumentów** w konfiguracji.

Jeśli aplikacja Outlook nie obsługuje domyślnego ustawienia etykiety innego niż domyślne ustawienie etykiety dla dokumentów: program Outlook zawsze będzie używać wartości domyślną Zastosuj tę etykietę do dokumentów na stronie Ustawienia zasad dla dokumentów  w konfiguracji zasad etykiet.

Gdy aplikacja Outlook obsługuje wyłączanie obowiązkowych etykiet:

- W konfiguracji zasad etykiet z Centrum zgodności platformy Microsoft 365 na stronie **Ustawienia** zasad: Wybierz pozycję Wymagaj od użytkowników stosowania etykiety do wiadomości e-mail **lub dokumentów**. Następnie wybierz **pozycję** **DalejNastępny** >  i wyczyść pole wyboru Wymagaj od użytkowników **stosowania etykiety do swoich wiadomości e-mail**. Jeśli chcesz, aby etykiety obowiązkowych dotyczyły wiadomości e-mail, a także dokumentów, zachowaj zaznaczone pole wyboru.

Gdy aplikacja Outlook nie obsługuje wyłączania obowiązkowych etykiet: Jeśli wybierzesz opcję Wymagaj od użytkowników stosowania  etykiety do swoich wiadomości e-mail lub dokumentów jako ustawienia zasad, program Outlook zawsze będzie monitował użytkowników o wybranie etykiety dla wiadomości e-mail bez etykiety.

> [!NOTE]
> Jeśli w programie PowerShell skonfigurowano ustawienia zaawansowane programów **OutlookDefaultLabel** i **DisableMandatoryInOutlook** przy użyciu poleceń cmdlet [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy) lub [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy) :
> 
> Wartości wybrane dla tych ustawień programu PowerShell są odzwierciedlane w konfiguracji zasad etykiet w Centrum zgodności i automatycznie działają dla Outlook, które obsługują te ustawienia. Pozostałe ustawienia zaawansowane programu PowerShell pozostaną obsługiwane tylko dla Information Protection Azure Information Protection ujednoliconego klienta etykiet.

## <a name="auditing-labeling-activities"></a>Działania związane z etykietami inspekcji

Aby uzyskać informacje na temat zdarzeń inspekcji generowanych przez działania etykiet wrażliwości, zobacz sekcję Działania [](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) etykiet wrażliwości w sekcji Przeszukiwanie dziennika inspekcji [w centrum zgodności](search-the-audit-log-in-security-and-compliance.md).

Te informacje inspekcji są wizualnie reprezentowane w Eksploratorze [](data-classification-content-explorer.md) zawartości i w [](data-classification-activity-explorer.md) Eksploratorze aktywności, aby ułatwić zrozumienie sposobu, w jaki są używane etykiety wrażliwości i gdzie znajduje się zawartość oznaczona etykietą. 

Podczas eksportowania i konfigurowania rekordów dziennika inspekcji można również tworzyć raporty niestandardowe, korzystając z oprogramowania do zarządzania informacjami o zabezpieczeniach i [zarządzania zdarzeniami](export-view-audit-log-records.md). Aby uzyskać bardziej szczegółowe rozwiązania do raportowania, zobacz Dokumentacja [Office 365 API działań zarządzania](/office/office-365-management-api/office-365-management-activity-api-reference).

> [!TIP]
> Aby ułatwić tworzenie raportów niestandardowych, zobacz następujące wpisy w blogu:
> - [Microsoft 365 działań dziennika inspekcji zgodności za pośrednictwem interfejsu API zarządzania usługi O365 — część 1](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/microsoft-365-compliance-audit-log-activities-via-o365/ba-p/2957171)
> - [Microsoft 365 dziennika inspekcji zgodności za pośrednictwem interfejsu API zarządzania usługi O365 — część 2](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/microsoft-365-compliance-audit-log-activities-via-o365/ba-p/2957297)

## <a name="end-user-documentation"></a>Dokumentacja użytkownika końcowego

- [Stosowanie etykiet wrażliwości do plików i wiadomości e-mail w pakiecie Office](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
    - [Znane problemy z etykietami wrażliwości w Office](https://support.microsoft.com/en-us/office/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [Automatyczne stosowanie etykiet wrażliwości do plików i wiadomości e-mail w wiadomościach e-mail w programie Office](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)
    - [Znane problemy dotyczące automatycznego stosowania lub polecania etykiet wrażliwości](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)
