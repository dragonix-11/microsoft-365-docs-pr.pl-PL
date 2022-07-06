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
description: Informacje dla administratorów IT dotyczące zarządzania etykietami poufności w aplikacjach pakietu Office dla komputerów stacjonarnych, urządzeń przenośnych i sieci Web.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c0557f53ee50189969f7e2225cabd74354b28055
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66640483"
---
# <a name="manage-sensitivity-labels-in-office-apps"></a>Zarządzanie etykietami poufności w aplikacjach Office

>*[Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Po [opublikowaniu](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) etykiet poufności z portal zgodności Microsoft Purview zaczynają one pojawiać się w aplikacjach pakietu Office, aby użytkownicy mogli klasyfikować i chronić dane podczas ich tworzenia lub edytowania.

Informacje zawarte w tym artykule ułatwiają pomyślne zarządzanie etykietami poufności w aplikacjach pakietu Office. Na przykład zidentyfikuj minimalne wersje aplikacji, które są potrzebne dla funkcji specyficznych dla wbudowanego etykietowania, wszelkie dodatkowe informacje o konfiguracji tych funkcji oraz zapoznaj się z interakcjami z klientem Information Protection ujednoliconego etykietowania oraz innymi aplikacjami i usługami.

## <a name="labeling-client-for-desktop-apps"></a>Klient etykietowania dla aplikacji klasycznych

Aby używać etykiet poufności wbudowanych w aplikacje klasyczne pakietu Office dla systemów Windows i Mac, należy użyć wersji subskrypcji pakietu Office. Ten klient etykietowania nie obsługuje autonomicznych wersji pakietu Office, czasami nazywanych "Office Perpetual".

Jeśli nie możesz przeprowadzić uaktualnienia do Aplikacje Microsoft 365 dla przedsiębiorstw dla wersji subskrypcji pakietu Office, tylko w przypadku komputerów z systemem Windows możesz użyć [klienta ujednoliconego etykietowania usługi Azure Information Protection (AIP](/azure/information-protection/rms-client/aip-clientv2)). Jednak ten klient jest teraz w [trybie konserwacji](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/announcing-aip-unified-labeling-client-maintenance-mode-and/ba-p/3043613) i nie zalecamy korzystania z dodatku AIP dla aplikacji pakietu Office, chyba że trzeba. Aby uzyskać więcej informacji, zobacz [Dlaczego warto wybierać wbudowane etykietowanie w dodatku AIP dla aplikacji pakietu Office](sensitivity-labels-aip.md).

## <a name="support-for-sensitivity-label-capabilities-in-apps"></a>Obsługa funkcji etykiet poufności w aplikacjach

W poniższych tabelach wymieniono minimalną wersję pakietu Office, która wprowadziła określone możliwości etykiet poufności wbudowanych w aplikacje pakietu Office. Lub, jeśli możliwość etykiety jest w publicznej wersji zapoznawczej lub w trakcie przeglądu dla przyszłej wersji. Aby uzyskać szczegółowe informacje o nowych możliwościach, które są planowane w przyszłych wersjach, skorzystaj z [planu platformy Microsoft 365](https://aka.ms/MIPC/Roadmap) .

Nowe wersje aplikacji pakietu Office są udostępniane w różnym czasie dla różnych kanałów aktualizacji. W przypadku systemu Windows nowe możliwości zostaną wyświetlone wcześniej, gdy korzystasz z kanału Bieżące kanały lub kanału Miesięczne przedsiębiorstwo, zamiast Semi-Annual Enterprise Channel. Minimalne numery wersji mogą również różnić się od jednego kanału aktualizacji do następnego. Aby uzyskać więcej informacji, zobacz [Omówienie kanałów aktualizacji dla Aplikacje Microsoft 365](/deployoffice/overview-update-channels) i [Historia aktualizacji dla Aplikacje Microsoft 365](/officeupdates/update-history-microsoft365-apps-by-date).

Nowe możliwości w prywatnej wersji zapoznawczej nie są uwzględnione w tabeli, ale możesz dołączyć do tych wersji zapoznawczych, nominując organizację do [programu Microsoft Information Protection prywatnej wersji zapoznawczej](https://aka.ms/mip-preview).

Pakiet Office dla systemów iOS i Office dla systemu Android: etykiety poufności są wbudowane w [aplikację pakietu Office](https://www.microsoft.com/en-us/microsoft-365/blog/2020/02/19/new-office-app-android-ios-available/).

> [!TIP]
> Podczas porównywania minimalnych wersji w tabelach z wersjami, które masz, należy pamiętać o typowym rozwiązaniu wersji wersji, aby pominąć zera wiodące.
> 
> Na przykład masz wersję 4.2128.0 i odczytujesz, że wersja 4.7.1+ jest wersją minimalną. Aby ułatwić porównanie, przeczytaj 4.7.1 (bez zer wiodących) jako 4. **0007.1** (a nie 4.**7000.1**). Wersja 4.2128.0 jest wyższa niż 4.0007.1, więc twoja wersja jest obsługiwana.

### <a name="sensitivity-label-capabilities-in-word-excel-and-powerpoint"></a>Funkcje etykiet poufności w programach Word, Excel i PowerPoint

Wymienione liczby to minimalne wersje aplikacji pakietu Office wymagane dla każdej funkcji. 

> [!NOTE]
> W przypadku systemu Windows i Semi-Annual Enterprise Channel minimalne obsługiwane numery wersji mogą jeszcze nie zostać wydane. [Dowiedz się więcej](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions)
 
|Możliwości |Windows |Mac |iOS |Android |Web |
|-----------|-------:|----|----|--------|----|
|[Ręczne stosowanie, zmienianie lub usuwanie etykiety](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| Bieżący kanał: 1910+ <br /><br> Miesięczny kanał przedsiębiorstwa: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Tak — zgoda](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Obsługa wielu języków](create-sensitivity-labels.md#additional-label-settings-with-security--compliance-powershell)| Bieżący kanał: 1910+ <br /><br> Miesięczny kanał przedsiębiorstwa: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | W trakcie przeglądu |
|[Stosowanie etykiety domyślnej](sensitivity-labels.md#what-label-policies-can-do) do nowych dokumentów                                         | Bieżący kanał: 1910+ <br /><br> Miesięczny kanał przedsiębiorstwa: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Tak — zgoda](sensitivity-labels-sharepoint-onedrive-files.md)                                                        |
|[Stosowanie etykiety domyślnej](sensitivity-labels.md#what-label-policies-can-do) do istniejących dokumentów | Wersja zapoznawcza: wprowadzanie do [kanału beta](https://office.com/insider) | Wersja zapoznawcza: wdrażanie do [bieżącego kanału (wersja zapoznawcza)](https://office.com/insider) | W trakcie przeglądu | W trakcie przeglądu | [Tak — zgoda](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Wymagaj uzasadnienia, aby zmienić etykietę](sensitivity-labels.md#what-label-policies-can-do)                     | Bieżący kanał: 1910+ <br /><br> Miesięczny kanał przedsiębiorstwa: 1910+  <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Tak — zgoda](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Podaj link pomocy do niestandardowej strony pomocy](sensitivity-labels.md#what-label-policies-can-do)                       | Bieżący kanał: 1910+ <br /><br> Miesięczny kanał przedsiębiorstwa: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Tak — zgoda](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Oznaczanie zawartości](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | Bieżący kanał: 1910+ <br /><br> Miesięczny kanał przedsiębiorstwa: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Tak — zgoda](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Oznaczenia dynamiczne ze zmiennymi](#dynamic-markings-with-variables)                                              | Bieżący kanał: 2010+ <br /><br> Miesięczny kanał przedsiębiorstwa: 2010+ <br /><br> Semi-Annual Enterprise Channel: 2102+ | 16.42+     | 2.42+ | 16.0.13328+ | [Tak — zgoda](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Przypisz teraz uprawnienia](encryption-sensitivity-labels.md#assign-permissions-now)                                 | Bieżący kanał: 1910+ <br /><br> Miesięczny kanał przedsiębiorstwa: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Tak — zgoda](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Zezwalaj użytkownikom na przypisywanie uprawnień: <br /> — monituj użytkowników](encryption-sensitivity-labels.md#let-users-assign-permissions)                     |Bieżący kanał: 2004+ <br /><br> Miesięczny kanał przedsiębiorstwa: 2004+ <br /><br> Semi-Annual Enterprise Channel: 2008+ | 16.35+   | W trakcie przeglądu   | W trakcie przeglądu         | W trakcie przeglądu                                                        |
|[Inspekcja działania użytkownika związanego z etykietami](#auditing-labeling-activities)                      | Bieżący kanał: 2011+ <br /><br> Miesięczny kanał przedsiębiorstwa: 2011+ <br /><br> Semi-Annual Enterprise Channel: 2108+ | 16.43+ | 2.46+ | 16.0.13628+ | Tak |
|[Wymaganie od użytkowników zastosowania etykiety do poczty e-mail i dokumentów](#require-users-to-apply-a-label-to-their-email-and-documents)   | Bieżący kanał: 2101+ <br /><br> Miesięczny kanał przedsiębiorstwa: 2101+ <br /><br> Semi-Annual Enterprise Channel: 2108+ | 16.45+         | 2.47+ | 16.0.13628+ | [Tak — zgoda](sensitivity-labels-sharepoint-onedrive-files.md)                                            
|[Automatyczne stosowanie etykiety poufności do zawartości](apply-sensitivity-label-automatically.md) <br /> — Używanie typów informacji poufnych                    | Bieżący kanał: 2009+ <br /><br> Miesięczny kanał przedsiębiorstwa: 2009+ <br /><br> Semi-Annual Enterprise Channel: 2102+ | 16.44+ | W trakcie przeglądu | W trakcie przeglądu | [Tak — zgoda](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Automatyczne stosowanie etykiety poufności do zawartości](apply-sensitivity-label-automatically.md) <br /> — Używanie klasyfikatorów z możliwością trenowania                    | Bieżący kanał: 2105+ <br /><br> Miesięczny kanał przedsiębiorstwa: 2105+ <br /><br> Semi-Annual Enterprise Channel: 2108+ | 16.49+ | W trakcie przeglądu | W trakcie przeglądu | [Tak — zgoda](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Obsługa współtwoerowania i automatycznego](sensitivity-labels-coauthoring.md) zapisywania dla dokumentów oznaczonych etykietami i zaszyfrowanych | Bieżący kanał: 2107+ <br /><br> Miesięczny kanał przedsiębiorstwa: 2107+ <br /><br> Semi-Annual Enterprise Channel: 2202+ |  16.51+ | Wersja zapoznawcza: 2.58+ po [zalogowaniu](sensitivity-labels-coauthoring.md#opt-in-to-the-preview-of-co-authoring-for-ios-and-android) | Wersja zapoznawcza: 16.0.14931+ po [włączeniu](sensitivity-labels-coauthoring.md#opt-in-to-the-preview-of-co-authoring-for-ios-and-android) | [Tak — zgoda](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Obsługa plików PDF](#pdf-support)| Wersja zapoznawcza: wprowadzanie do [kanału beta](https://office.com/insider) |  W trakcie przeglądu | W trakcie przeglądu | W trakcie przeglądu | W trakcie przeglądu |


### <a name="sensitivity-label-capabilities-in-outlook"></a>Możliwości etykiet poufności w programie Outlook

Wymienione liczby to minimalne wersje aplikacji pakietu Office wymagane dla każdej funkcji. 

> [!NOTE]
> W przypadku systemu Windows i Semi-Annual Enterprise Channel minimalne obsługiwane numery wersji mogą jeszcze nie zostać wydane. [Dowiedz się więcej](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions)

|Możliwości |Outlook dla systemu Windows |Outlook dla komputerów Mac |Program Outlook w systemie iOS |Outlook w systemie Android |Outlook on the web |
|-----------|-------------------:|----------------|---------------|-------------------|-------------------|
|[Ręczne stosowanie, zmienianie lub usuwanie etykiety](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| Bieżący kanał: 1910+ <br /><br> Miesięczny kanał przedsiębiorstwa: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Tak               |
|[Obsługa wielu języków](create-sensitivity-labels.md#additional-label-settings-with-security--compliance-powershell)| Bieżący kanał: 1910+ <br /><br> Miesięczny kanał przedsiębiorstwa: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+ | 4.7.1+ | 4.0.39+ | Tak |
|[Stosowanie etykiety domyślnej](sensitivity-labels.md#what-label-policies-can-do)                                         | Bieżący kanał: 1910+ <br /><br> Miesięczny kanał przedsiębiorstwa: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Tak               |
|[Wymagaj uzasadnienia, aby zmienić etykietę](sensitivity-labels.md#what-label-policies-can-do)                     | Bieżący kanał: 1910+ <br /><br> Miesięczny kanał przedsiębiorstwa: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Tak               |
|[Podaj link pomocy do niestandardowej strony pomocy](sensitivity-labels.md#what-label-policies-can-do)                       | Bieżący kanał: 1910+ <br /><br> Miesięczny kanał przedsiębiorstwa: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Tak               |
|[Oznaczanie zawartości](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | Bieżący kanał: 1910+ <br /><br> Miesięczny kanał przedsiębiorstwa: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Tak               |
|[Oznaczenia dynamiczne ze zmiennymi](#dynamic-markings-with-variables)                                              | Bieżący kanał: 1910+ <br /><br> Miesięczny kanał przedsiębiorstwa: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Tak               |
|[Przypisz teraz uprawnienia](encryption-sensitivity-labels.md#assign-permissions-now)                                 | Bieżący kanał: 1910+ <br /><br> Miesięczny kanał przedsiębiorstwa: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Tak               |
|[Zezwalaj użytkownikom na przypisywanie uprawnień: <br /> — nie przesyłaj dalej](encryption-sensitivity-labels.md#let-users-assign-permissions)                     | Bieżący kanał: 1910+ <br /><br> Miesięczny kanał przedsiębiorstwa: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Tak               |
|[Zezwalaj użytkownikom na przypisywanie uprawnień: <br /> — tylko szyfrowanie](encryption-sensitivity-labels.md#let-users-assign-permissions)  | Bieżący kanał: 2011+ <br /><br> Miesięczny kanał przedsiębiorstwa: 2011+ <br /><br> Semi-Annual Enterprise Channel: 2108+ | 16.48+ <sup>\*</sup> | 4.2112.0+  | 4.2112.0+ | Tak |
|[Wymaganie od użytkowników zastosowania etykiety do poczty e-mail i dokumentów](#require-users-to-apply-a-label-to-their-email-and-documents)   | Bieżący kanał: 2101+ <br /><br> Miesięczny kanał przedsiębiorstwa: 2101+ <br /><br> Semi-Annual Enterprise Channel: 2108+ | 16.43+ <sup>\*</sup>                    | 4.2111+            | 4.2111+                | Tak                |
|[Inspekcja działania użytkownika związanego z etykietami](#auditing-labeling-activities) | Bieżący kanał: 2011+ <br /><br> Miesięczny kanał przedsiębiorstwa: 2011+ <br /><br> Semi-Annual Enterprise Channel: 2108+ | 16.51+ <sup>\*</sup> | 4.2126+ | 4.2126+ | Tak |
|[Automatyczne stosowanie etykiety poufności do zawartości](apply-sensitivity-label-automatically.md) <br /> — Używanie typów informacji poufnych                    | Bieżący kanał: 2009+ <br /><br> Miesięczny kanał przedsiębiorstwa: 2009+ <br /><br> Semi-Annual Enterprise Channel: 2102+ | 16.44+ <sup>\*</sup>                    | W trakcie przeglądu           | W trakcie przeglądu               | Tak |
|[Automatyczne stosowanie etykiety poufności do zawartości](apply-sensitivity-label-automatically.md) <br /> — Używanie klasyfikatorów z możliwością trenowania                    | Bieżący kanał: 2105+ <br /><br> Miesięczny kanał przedsiębiorstwa: 2105+ <br /><br> Semi-Annual Enterprise Channel: 2108+ | 16.49+ | W trakcie przeglądu           | W trakcie przeglądu               | Tak |
|[Różne ustawienia etykiety domyślnej i obowiązkowego etykietowania](#outlook-specific-options-for-default-label-and-mandatory-labeling)                    | Bieżący kanał: 2105+ <br /><br> Miesięczny kanał przedsiębiorstwa: 2105+ <br /><br> Semi-Annual Enterprise Channel: 2108+ | 16.43+ <sup>\*</sup>                   | 4.2111+           | 4.2111+               | Tak |
|[Obsługa plików PDF](#pdf-support) | W trakcie przeglądu|  W trakcie przeglądu | W trakcie przeglądu | W trakcie przeglądu | W trakcie przeglądu |
|[Stosowanie ochrony S/MIME](#configure-a-label-to-apply-smime-protection-in-outlook)                    | W trakcie przeglądu | Wdrażanie: 16.61+ <sup>\*</sup>                   | Wdrażanie: 4.2208+ | Wdrażanie: 4.2203+ | W trakcie przeglądu |

**Przypisy dolne:**

<sup>\*</sup>Wymaga [nowego Outlook dla komputerów Mac](https://support.microsoft.com/office/the-new-outlook-for-mac-6283be54-e74d-434e-babb-b70cefc77439)

## <a name="office-built-in-labeling-client-and-the-azure-information-protection-client"></a>Wbudowany klient etykietowania pakietu Office i klient usługi Azure Information Protection

Jeśli użytkownicy mają zainstalowanego [klienta usługi Azure Information Protection (AIP)](/azure/information-protection/rms-client/aip-clientv2) na swoich komputerach z systemem Windows, domyślnie wbudowane etykiety są wyłączone w [aplikacjach pakietu Windows Office, które je obsługują](#labeling-client-for-desktop-apps). Ponieważ wbudowane etykiety nie korzystają z dodatku pakietu Office używanego przez klienta usługi AIP, mają one korzyści z większej stabilności i lepszej wydajności. Obsługują one również najnowsze funkcje, takie jak zaawansowane klasyfikatory. 

> [!NOTE]
> Jeśli nie widzisz funkcji etykietowania oczekiwanych na komputerach z systemem Windows, pomimo potwierdzenia minimalnej obsługiwanej wersji kanału aktualizacji pakietu Office, może to być spowodowane [koniecznością wyłączenia dodatku AIP](sensitivity-labels-aip.md#how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps).

Aby dowiedzieć się więcej na temat obsługi etykietowania za pomocą klienta usługi AIP i sposobu wyłączania tego klienta tylko w aplikacjach pakietu Office, zobacz [Dlaczego warto wybrać wbudowane etykietowanie w dodatku AIP dla aplikacji pakietu Office](sensitivity-labels-aip.md).

## <a name="if-you-need-to-turn-off-built-in-labeling-in-office-apps-on-windows"></a>Jeśli musisz wyłączyć wbudowane etykietowanie w aplikacjach pakietu Office w systemie Windows

Wbudowany klient etykietowania pakietu Office pobiera etykiety poufności i ustawienia zasad etykiet poufności z portal zgodności Microsoft Purview.

Aby korzystać z wbudowanego klienta etykietowania pakietu Office, musisz mieć co najmniej jedną [zasadę etykiety opublikowaną](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) dla użytkowników z portal zgodności Microsoft Purview i [obsługiwaną wersję pakietu Office](#support-for-sensitivity-label-capabilities-in-apps).

Jeśli oba te warunki są spełnione, ale musisz wyłączyć wbudowane etykiety w aplikacjach pakietu Windows Office, użyj następującego ustawienia zasady grupy:

1. Przejdź do pozycji **Konfiguracja użytkownika/Szablony administracyjne/Microsoft Office 2016/Ustawienia zabezpieczeń**.

2. Ustaw **opcję Użyj funkcji poufności w pakiecie Office, aby zastosować i wyświetlić etykiety poufności** na **wartość 0**.

Jeśli później trzeba przywrócić tę konfigurację, zmień wartość na **1**. Może być również konieczne zmianę tej wartości na 1, jeśli przycisk **Czułość** nie jest wyświetlany na wstążce zgodnie z oczekiwaniami. Na przykład poprzedni administrator wyłączył to ustawienie etykietowania.
 
Wdróż to ustawienie przy użyciu zasady grupy lub za pomocą [usługi zasad w chmurze pakietu Office](/DeployOffice/overview-office-cloud-policy-service). To ustawienie wchodzi w życie po ponownym uruchomieniu tych aplikacji pakietu Office. 

Ponieważ to ustawienie jest specyficzne dla aplikacji pakietu Windows Office, nie ma wpływu na inne aplikacje w systemie Windows obsługujące etykiety poufności (takie jak Power BI) lub inne platformy (takie jak macOS, urządzenia przenośne i Office dla sieci web). Jeśli nie chcesz, aby niektórzy lub wszyscy użytkownicy widzieli etykiety poufności i korzystali z nich we wszystkich aplikacjach i na wszystkich platformach, nie przypisuj tych użytkowników zasad etykiet poufności.

## <a name="office-file-types-supported"></a>Obsługiwane typy plików pakietu Office

Aplikacje pakietu Office, które mają wbudowane etykietowanie plików programów Word, Excel i PowerPoint, obsługują format Open XML (na przykład .docx i .xlsx), ale nie format pakietu Microsoft Office 97-2003 (na przykład .doc i .xls), format open document (np. odt i ods) lub inne formaty. Jeśli typ pliku nie jest obsługiwany na potrzeby wbudowanego etykietowania, przycisk **Poufności** nie jest dostępny w aplikacji pakietu Office.

Klient ujednoliconego etykietowania platformy Azure Information Protection obsługuje zarówno format Open XML, jak i format pakietu Microsoft Office 97-2003. Aby uzyskać więcej informacji, zobacz [Typy plików obsługiwane przez klienta ujednoliconego etykietowania usługi Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-file-types) z przewodnika administratora tego klienta.

W przypadku innych rozwiązań do etykietowania zapoznaj się z dokumentacją dotyczącą obsługiwanych typów plików.

## <a name="protection-templates-and-sensitivity-labels"></a>Szablony ochrony i etykiety poufności

[Szablony ochrony zdefiniowane przez administratora](/azure/information-protection/configure-policy-templates), takie jak te zdefiniowane na potrzeby Office 365 szyfrowania komunikatów, nie są widoczne w aplikacjach pakietu Office, gdy używasz wbudowanego etykietowania. To uproszczone środowisko odzwierciedla, że nie ma potrzeby wybierania szablonu ochrony, ponieważ te same ustawienia są dołączone do etykiet poufności z włączonym szyfrowaniem.

Istniejący szablon można przekonwertować na etykietę poufności, gdy używasz polecenia cmdlet [New-Label](/powershell/module/exchange/new-label) z *parametrem EncryptionTemplateId* .

## <a name="information-rights-management-irm-options-and-sensitivity-labels"></a>Opcje i etykiety poufności usługi Information Rights Management (IRM)

Etykiety poufności skonfigurowane w celu zastosowania szyfrowania usuwają złożoność od użytkowników w celu określenia własnych ustawień szyfrowania. W wielu aplikacjach pakietu Office te indywidualne ustawienia szyfrowania nadal mogą być konfigurowane ręcznie przez użytkowników przy użyciu opcji zarządzania prawami do informacji (IRM). Na przykład w przypadku aplikacji systemu Windows:

- W przypadku dokumentu:**Informacje o** >  **pliku** > **Ochrona dokumentu** > **— ograniczanie dostępu**
- dla wiadomości e-mail: na **karcie Opcje** > **Encrypt** 
  
Gdy użytkownicy początkowo oznaczą dokument lub wiadomość e-mail etykietą, mogą zastąpić ustawienia konfiguracji etykiet własnymi ustawieniami szyfrowania. Przykład:

- Użytkownik stosuje etykietę **Poufne \ Wszyscy pracownicy** do dokumentu i ta etykieta jest skonfigurowana do stosowania ustawień szyfrowania dla wszystkich użytkowników w organizacji. Następnie ten użytkownik ręcznie konfiguruje ustawienia usługi IRM, aby ograniczyć dostęp do użytkownika spoza organizacji. Wynikiem końcowym jest dokument z etykietą **Poufne \ Wszyscy pracownicy i zaszyfrowane** , ale użytkownicy w organizacji nie mogą otworzyć go zgodnie z oczekiwaniami.

- Użytkownik stosuje etykietę **Poufne \ Adresaci tylko** do wiadomości e-mail, a ta wiadomość e-mail jest skonfigurowana do stosowania ustawienia szyfrowania **Nie przesyłaj dalej**. W aplikacji Outlook ten użytkownik ręcznie wybiera ustawienie IRM dla opcji Tylko szyfrowanie. Efektem końcowym jest to, że wiadomość e-mail pozostaje zaszyfrowana, ale może zostać przesłana dalej przez adresatów, pomimo posiadania **etykiety Poufne \ Tylko adresaci** .
    
    Jako wyjątek dla Outlook w sieci Web opcje z menu **Szyfruj** nie są dostępne dla użytkownika, aby wybrać, kiedy aktualnie wybrana etykieta stosuje szyfrowanie.

- Użytkownik stosuje etykietę **Ogólne** do dokumentu, a ta etykieta nie jest skonfigurowana do stosowania szyfrowania. Następnie ten użytkownik ręcznie konfiguruje ustawienia usługi IRM w celu ograniczenia dostępu do dokumentu. Wynikiem końcowym jest dokument z etykietą **Ogólne** , ale który stosuje również szyfrowanie, aby niektórzy użytkownicy nie mogli go otworzyć zgodnie z oczekiwaniami.

Jeśli dokument lub wiadomość e-mail jest już oznaczona etykietą, użytkownik może wykonać dowolną z tych akcji, jeśli zawartość nie jest jeszcze zaszyfrowana lub ma [prawo do użycia](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) eksportu lub pełnej kontroli. 

Aby zapewnić bardziej spójne środowisko etykietowania z zrozumiałym raportowaniem, podaj odpowiednie etykiety i wskazówki dla użytkowników, aby stosować tylko etykiety w celu ochrony dokumentów i wiadomości e-mail. Przykład:

- W przypadkach wyjątków, w których użytkownicy muszą przypisywać własne uprawnienia, podaj etykiety, które [umożliwiają użytkownikom przypisywanie własnych uprawnień](encryption-sensitivity-labels.md#let-users-assign-permissions). 

- Zamiast ręcznie usuwać szyfrowanie przez użytkowników po wybraniu etykiety, która stosuje szyfrowanie, podaj etykietę alternatywną, gdy użytkownicy potrzebują etykiety o tej samej klasyfikacji, ale bez szyfrowania. Takie jak:
    - **Poufne \ Wszyscy pracownicy**
    - **Poufne \ Każdy (bez szyfrowania)**

- Rozważ wyłączenie ustawień usługi IRM, aby uniemożliwić użytkownikom ich wybieranie:
    - Outlook dla systemu Windows: 
        - Klucze `DWORD:00000001` rejestru *DisableDNF* i *DisableEO* from `HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Common\DRM`
        - Upewnij się, że ustawienie zasady grupy **Konfigurowanie domyślnej opcji szyfrowania dla przycisku Szyfruj** nie jest skonfigurowane
    - Outlook dla komputerów Mac: 
        - Ustawienia zabezpieczeń *DisableEncryptOnly* i *DisableDoNotForward* opisane w temacie [Ustawianie preferencji dla Outlook dla komputerów Mac](/DeployOffice/mac/preferences-outlook)
    - Outlook w sieci Web: 
        - Parametry *SimplifiedClientAccessDoNotForwardDisabled* i *SimplifiedClientAccessEncryptOnlyDisabled* udokumentowane dla [polecenia Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration)
    - Outlook dla systemów iOS i Android: te aplikacje nie obsługują użytkowników stosujących szyfrowanie bez etykiet, więc nie można ich wyłączyć.

> [!NOTE]
> Jeśli użytkownicy ręcznie usuną szyfrowanie z dokumentu z etykietą przechowywanego w programie SharePoint lub OneDrive i [włączono etykiety poufności dla plików pakietu Office w programach SharePoint i OneDrive](sensitivity-labels-sharepoint-onedrive-files.md), szyfrowanie etykiet zostanie automatycznie przywrócone po następnym uzyskaniu dostępu do dokumentu lub pobraniu go. 


## <a name="apply-sensitivity-labels-to-files-emails-and-attachments"></a>Stosowanie etykiet poufności do plików, wiadomości e-mail i załączników

Użytkownicy mogą stosować tylko jedną etykietę naraz dla każdego dokumentu lub wiadomości e-mail.

Po oznaczeniu wiadomości e-mail zawierającej załączniki załączniki dziedziczą etykietę tylko wtedy, gdy etykieta stosowana do wiadomości e-mail stosuje szyfrowanie, a załącznik jest dokumentem pakietu Office, który nie jest jeszcze zaszyfrowany. Ponieważ dziedziczona etykieta stosuje szyfrowanie, załącznik staje się nowo szyfrowany.

Załącznik nie dziedziczy etykiet z wiadomości e-mail, gdy etykieta zastosowana do wiadomości e-mail nie stosuje szyfrowania lub załącznik jest już zaszyfrowany.

Przykłady dziedziczenia etykiet, w których etykieta **Poufne** stosuje szyfrowanie, a etykieta **Ogólne** nie stosuje szyfrowania:

- Użytkownik tworzy nową wiadomość e-mail i stosuje etykietę **Poufne** do tej wiadomości. Następnie dodają dokument programu Word, który nie jest oznaczony etykietą ani szyfrowany. W wyniku dziedziczenia dokument ma nowo etykietę **Poufne** i ma teraz zastosowane szyfrowanie z tej etykiety.

- Użytkownik tworzy nową wiadomość e-mail i stosuje etykietę **Poufne** do tej wiadomości. Następnie dodają dokument programu Word z etykietą **Ogólne** , a ten plik nie jest szyfrowany. W wyniku dziedziczenia dokument jest ponownie oznaczany jako **poufny** i ma teraz zastosowane szyfrowanie z tej etykiety.

## <a name="sensitivity-label-compatibility"></a>Zgodność etykiet poufności

**Aplikacje obsługujące usługę RMS**: jeśli otworzysz dokument lub wiadomość e-mail z etykietami lub zaszyfrowaną wiadomością [e-mail w aplikacji obsługującego usługę RMS](/azure/information-protection/requirements-applications#rms-enlightened-applications) , która nie obsługuje etykiet poufności, aplikacja nadal wymusza szyfrowanie i zarządzanie prawami.

**Klient usługi Azure Information Protection**: możesz wyświetlać i zmieniać etykiety poufności stosowane do dokumentów i wiadomości e-mail za pomocą wbudowanego klienta etykietowania pakietu Office przy użyciu klienta usługi Azure Information Protection i na odwrót.

**W przypadku innych wersji pakietu Office**: każdy autoryzowany użytkownik może otwierać oznaczone dokumenty i wiadomości e-mail w innych wersjach pakietu Office. Można jednak wyświetlać lub zmieniać etykiety tylko w obsługiwanych wersjach pakietu Office lub przy użyciu klienta usługi Azure Information Protection. Obsługiwane wersje aplikacji pakietu Office są wymienione w [poprzedniej sekcji](#support-for-sensitivity-label-capabilities-in-apps).

## <a name="support-for-sharepoint-and-onedrive-files-protected-by-sensitivity-labels"></a>Obsługa plików programu SharePoint i OneDrive chronionych etykietami poufności

Aby użyć wbudowanego klienta etykietowania pakietu Office z Office w sieci Web dla dokumentów w programie SharePoint lub OneDrive, upewnij się, że [włączono etykiety poufności dla plików pakietu Office w programach SharePoint i OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

## <a name="support-for-external-users-and-labeled-content"></a>Obsługa użytkowników zewnętrznych i zawartości oznaczonej etykietami

Etykieta dokumentu lub wiadomości e-mail jest przechowywana jako metadane zawierające dzierżawę i identyfikator GUID etykiety. Gdy dokument lub wiadomość e-mail z etykietą jest otwierana przez aplikację pakietu Office, która obsługuje etykiety poufności, te metadane są odczytywane i tylko wtedy, gdy użytkownik należy do tej samej dzierżawy, etykieta jest wyświetlana w aplikacji. Na przykład w przypadku wbudowanego etykietowania dla programów Word, PowerPoint i Excel nazwa etykiety jest wyświetlana na pasku stanu. 

Oznacza to, że jeśli udostępniasz dokumenty innej organizacji używającej różnych nazw etykiet, każda organizacja może zastosować i zobaczyć własną etykietę zastosowaną do dokumentu. Jednak następujące elementy z zastosowanej etykiety są widoczne dla użytkowników spoza organizacji:

- Oznaczenia zawartości. Gdy etykieta stosuje nagłówek, stopkę lub znak wodny, są one dodawane bezpośrednio do zawartości i pozostają widoczne, dopóki ktoś ich nie zmodyfikuje lub nie usunie.

- Nazwa i opis bazowego szablonu ochrony z etykiety, która zastosowała szyfrowanie. Te informacje są wyświetlane na pasku komunikatów w górnej części dokumentu, aby podać informacje o tym, kto jest upoważniony do otwierania dokumentu, oraz o prawach użytkowania tego dokumentu.

### <a name="sharing-encrypted-documents-with-external-users"></a>Udostępnianie zaszyfrowanych dokumentów użytkownikom zewnętrznym

Oprócz ograniczania dostępu do użytkowników we własnej organizacji można rozszerzyć dostęp do każdego innego użytkownika, który ma konto w usłudze Azure Active Directory. Jeśli jednak organizacja korzysta z zasad dostępu warunkowego, zapoznaj się z [następną sekcją](#conditional-access-policies) , aby uzyskać dodatkowe informacje.

Wszystkie aplikacje pakietu Office i inne [aplikacje obsługują usługę RMS](/azure/information-protection/requirements-applications#rms-enlightened-applications) mogą otwierać zaszyfrowane dokumenty po pomyślnym uwierzytelnieniu użytkownika. 

Jeśli użytkownicy zewnętrzni nie mają konta w usłudze Azure Active Directory, mogą uwierzytelniać się przy użyciu kont gościa w dzierżawie. Te konta gościa mogą być również używane do uzyskiwania dostępu do dokumentów udostępnionych w programie SharePoint lub OneDrive po [włączeniu etykiet poufności dla plików pakietu Office w programach SharePoint i OneDrive](sensitivity-labels-sharepoint-onedrive-files.md):

- Jedną z opcji jest samodzielne utworzenie tych kont gościa. Możesz określić dowolny adres e-mail, którego ci użytkownicy już używają. Na przykład ich adres Gmail.
    
    Zaletą tej opcji jest to, że można ograniczyć dostęp i prawa do określonych użytkowników, określając ich adres e-mail w ustawieniach szyfrowania. Minusem jest obciążenie administracyjne związane z tworzeniem konta i koordynacją z konfiguracją etykiety.

- Inną opcją jest użycie [integracji programu SharePoint i usługi OneDrive z usługą Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration), aby konta gościa były tworzone automatycznie, gdy użytkownicy udostępniają łącza.
    
    Zaletą tej opcji jest minimalne obciążenie administracyjne, ponieważ konta są tworzone automatycznie i prostsza konfiguracja etykiet. W tym scenariuszu należy wybrać opcję szyfrowania [Dodaj uwierzytelnionego użytkownika](encryption-sensitivity-labels.md#requirements-and-limitations-for-add-any-authenticated-users) , ponieważ adresy e-mail nie będą wcześniej znane. Minusem jest to, że to ustawienie nie pozwala ograniczyć dostępu i praw użytkowania do określonych użytkowników.

Użytkownicy zewnętrzni mogą również używać konta Microsoft do otwierania zaszyfrowanych dokumentów, gdy korzystają z systemu Windows i Aplikacje Microsoft 365 ([dawniej Office 365 aplikacji](/deployoffice/name-change)) lub autonomicznej wersji pakietu Office 2019. Niedawno obsługiwane w przypadku innych platform konta Microsoft są również obsługiwane w przypadku otwierania zaszyfrowanych dokumentów w systemach macOS (Aplikacje Microsoft 365, wersja 16.42+), Android (wersja 16.0.13029+) i iOS (wersja 2.42+). Na przykład użytkownik w organizacji udostępnia zaszyfrowany dokument użytkownikowi spoza organizacji, a ustawienia szyfrowania określają adres e-mail Gmail dla użytkownika zewnętrznego. Ten użytkownik zewnętrzny może utworzyć własne konto Microsoft, które używa swojego adresu e-mail Gmail. Następnie po zalogowaniu się przy użyciu tego konta mogą otworzyć dokument i edytować go zgodnie z określonymi dla nich ograniczeniami użycia. Aby zapoznać się z przykładem tego scenariusza, zobacz [Otwieranie i edytowanie chronionego dokumentu](/azure/information-protection/secure-collaboration-documents#opening-and-editing-the-protected-document).

> [!NOTE]
> Adres e-mail konta Microsoft musi być zgodny z adresem e-mail określonym w celu ograniczenia dostępu do ustawień szyfrowania.

Gdy użytkownik z kontem Microsoft otworzy w ten sposób zaszyfrowany dokument, automatycznie utworzy konto gościa dla dzierżawy, jeśli konto gościa o tej samej nazwie jeszcze nie istnieje. Gdy konto gościa istnieje, można go następnie użyć do otwierania dokumentów w programach SharePoint i OneDrive przy użyciu Office w sieci Web, oprócz otwierania zaszyfrowanych dokumentów z obsługiwanych aplikacji klasycznych i mobilnych pakietu Office.

Jednak automatyczne konto gościa nie jest tworzone natychmiast w tym scenariuszu z powodu opóźnienia replikacji. Jeśli określisz osobiste adresy e-mail w ramach ustawień szyfrowania etykiet, zalecamy utworzenie odpowiednich kont gościa w usłudze Azure Active Directory. Następnie poinformuj tych użytkowników, że muszą oni użyć tego konta, aby otworzyć zaszyfrowany dokument z Organizacji.

> [!TIP]
> Ponieważ nie możesz mieć pewności, że użytkownicy zewnętrzni będą używać obsługiwanej aplikacji klienckiej pakietu Office, udostępnianie linków z programu SharePoint i usługi OneDrive po utworzeniu kont gościa (dla określonych użytkowników) lub podczas korzystania [z integracji programu SharePoint i usługi OneDrive z usługą Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview) (dla każdego uwierzytelnionego użytkownika) jest bardziej niezawodną metodą obsługi bezpiecznej współpracy z użytkownikami zewnętrznymi.

### <a name="conditional-access-policies"></a>Zasady dostępu warunkowego

Jeśli Organizacja zaimplementowała [zasady dostępu warunkowego usługi Azure Active Directory](/azure/active-directory/conditional-access/overview), sprawdź konfigurację tych zasad. Jeśli zasady obejmują usługę **Microsoft Azure Information Protection**, a zasady rozszerzają się na użytkowników zewnętrznych, ci użytkownicy zewnętrzni muszą mieć konto gościa w dzierżawie, nawet jeśli mają konto Azure AD we własnej dzierżawie.

Bez tego konta gościa nie mogą otworzyć zaszyfrowanego dokumentu i zobaczyć komunikatu o błędzie. Tekst wiadomości może poinformować ich, że ich konto musi zostać dodane jako użytkownik zewnętrzny w dzierżawie, z nieprawidłową instrukcją dla tego scenariusza, aby **wylogować się i zalogować się ponownie przy użyciu innego konta użytkownika usługi Azure Active Directory**.

Jeśli nie możesz tworzyć i konfigurować kont gości w dzierżawie dla użytkowników zewnętrznych, którzy muszą otwierać dokumenty zaszyfrowane za pomocą etykiet, musisz usunąć usługę Azure Information Protection z zasad dostępu warunkowego lub wykluczyć użytkowników zewnętrznych z zasad.

Aby uzyskać więcej informacji na temat dostępu warunkowego i usługi Azure Information Protection, usługi szyfrowania używanej przez etykiety poufności, zobacz często zadawane pytanie. [Widzę, że usługa Azure Information Protection jest wymieniona jako dostępna aplikacja w chmurze na potrzeby dostępu warunkowego — jak to działa?](/azure/information-protection/faqs#i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work)

## <a name="when-office-apps-apply-content-marking-and-encryption"></a>Kiedy aplikacje pakietu Office stosują znakowanie i szyfrowanie zawartości

Aplikacje pakietu Office inaczej stosują znakowanie zawartości i szyfrowanie przy użyciu etykiety poufności, w zależności od używanej aplikacji.

| Aplikacja | Oznaczanie zawartości | Szyfrowanie |
| --- | --- | --- |
| Word, Excel, PowerPoint na wszystkich platformach | Natychmiast | Natychmiast |
| Program Outlook dla komputerów PC i Mac | Po wysłaniu wiadomości e-mail Exchange Online | Natychmiast |
| Outlook w sieci Web, iOS i Android | Po wysłaniu wiadomości e-mail Exchange Online | Po wysłaniu wiadomości e-mail Exchange Online |
|

Rozwiązania, które stosują etykiety poufności do plików spoza aplikacji pakietu Office, umożliwiają stosowanie metadanych etykietowania do pliku. W tym scenariuszu oznaczanie zawartości z konfiguracji etykiety nie jest wstawiane do pliku, ale jest stosowane szyfrowanie. 

Po otwarciu tych plików w aplikacji klasycznej pakietu Office oznaczenia zawartości są automatycznie stosowane przez klienta ujednoliconego etykietowania usługi Azure Information Protection podczas pierwszego zapisywania pliku. Oznaczenia zawartości nie są automatycznie stosowane w przypadku używania wbudowanych etykiet dla aplikacji klasycznych, mobilnych lub internetowych.

Scenariusze, które obejmują stosowanie etykiety poufności poza aplikacjami pakietu Office, obejmują:

- Skaner, Eksplorator plików i program PowerShell z poziomu klienta ujednoliconego etykietowania usługi Azure Information Protection 

- Zasady automatycznego etykietowania dla programu SharePoint i usługi OneDrive

- Wyeksportowane dane oznaczone etykietami i zaszyfrowane z usługi Power BI

- Microsoft Defender for Cloud Apps

W tych scenariuszach, korzystając z aplikacji pakietu Office, użytkownik z wbudowanym etykietowaniem może zastosować oznaczenia zawartości etykiety, tymczasowo usuwając lub zastępując bieżącą etykietę, a następnie ponownie stosując oryginalną etykietę.

### <a name="dynamic-markings-with-variables"></a>Oznaczenia dynamiczne ze zmiennymi

> [!IMPORTANT]
> Jeśli aplikacje pakietu Office nie obsługują tej możliwości, stosują oznaczenia jako oryginalny tekst określony w konfiguracji etykiety, zamiast rozwiązywać zmienne.
> 
> Klient ujednoliconego etykietowania platformy Azure Information Protection obsługuje oznaczenia dynamiczne. Aby uzyskać informacje na temat etykietowania wbudowanego w pakiet Office, zobacz [tabele](#support-for-sensitivity-label-capabilities-in-apps) w sekcji możliwości na tej stronie, aby zapoznać się z obsługiwanymi minimalnymi wersjami.

Podczas konfigurowania etykiety poufności dla oznaczeń zawartości można użyć następujących zmiennych w ciągu tekstowym dla nagłówka, stopki lub znaku wodnego:

| Zmienna | Opis | Przykład zastosowania etykiety |
| -------- | ----------- | ------- |
| `${Item.Label}` | Nazwa wyświetlana etykiety zastosowanej etykiety | **Ogólne**|
| `${Item.Name}` | Nazwa pliku lub temat wiadomości e-mail o treści oznaczonej etykietą | **Sales.docx** |
| `${Item.Location}` | Ścieżka i nazwa pliku dokumentu oznaczonego etykietą lub temat wiadomości e-mail dla wiadomości e-mail oznaczonej etykietą | **\\\Sales\2020\Q3\Report.docx**|
| `${User.Name}` | Nazwa wyświetlana użytkownika stosującego etykietę | **Richard Simone** |
| `${User.PrincipalName}` | Azure AD główną nazwą użytkownika (UPN) użytkownika stosującego etykietę | **rsimone\@contoso.com** |
| `${Event.DateTime}` | Data i godzina etykietowania zawartości w lokalnej strefie czasowej użytkownika stosującego etykietę w aplikacjach platformy Microsoft 365 lub utc (uniwersalny czas koordynowany) dla usługi Office Online i zasady automatycznego etykietowania | **10.08.2020 13:30** |

> [!NOTE]
> Składnia tych zmiennych uwzględnia wielkość liter.

#### <a name="setting-different-visual-markings-for-word-excel-powerpoint-and-outlook"></a>Ustawianie różnych oznaczeń wizualnych dla programów Word, Excel, PowerPoint i Outlook

Jako dodatkową zmienną można skonfigurować oznaczenia wizualne dla typu aplikacji pakietu Office przy użyciu instrukcji zmiennej "If.App" w ciągu tekstowym i zidentyfikować typ aplikacji przy użyciu wartości **Word**, **Excel**, **PowerPoint** lub **Outlook**. Możesz również skrócić te wartości, co jest konieczne, jeśli chcesz określić więcej niż jedną w tej samej instrukcji If.App.

Należy stosować następującą składnię:

```
${If.App.<application type>}<your visual markings text> ${If.End}
```

Podobnie jak w przypadku innych dynamicznych oznaczeń wizualnych, składnia uwzględnia wielkość liter, która zawiera skróty dla każdego typu aplikacji (WEPO).

Przykłady:

- **Ustaw tekst nagłówka tylko dla dokumentów programu Word:**

    `${If.App.Word}This Word document is sensitive ${If.End}`

    Tylko w nagłówkach dokumentów programu Word etykieta stosuje tekst nagłówka "Ten dokument programu Word jest poufny". Do innych aplikacji pakietu Office nie jest stosowany żaden tekst nagłówka.

- **Ustaw tekst stopki dla programów Word, Excel i Outlook oraz inny tekst stopki dla programu PowerPoint:**

    `${If.App.WXO}This content is confidential. ${If.End}${If.App.PowerPoint}This presentation is confidential. ${If.End}`

    W programach Word, Excel i Outlook etykieta stosuje tekst stopki "Ta zawartość jest poufna". W programie PowerPoint etykieta stosuje tekst stopki "Ta prezentacja jest poufna".

- **Ustaw określony tekst znaku wodnego dla programów Word i PowerPoint, a następnie tekst znaku wodnego dla programów Word, Excel i PowerPoint:**

    `${If.App.WP}This content is ${If.End}Confidential`

    W programach Word i PowerPoint etykieta stosuje tekst znaku wodnego "Ta zawartość jest poufna". W programie Excel etykieta stosuje tekst znaku wodnego "Poufne". W programie Outlook etykieta nie stosuje żadnego tekstu znaku wodnego, ponieważ znaki wodne jako oznaczenia wizualne nie są obsługiwane w programie Outlook.

## <a name="require-users-to-apply-a-label-to-their-email-and-documents"></a>Wymaganie od użytkowników zastosowania etykiety do poczty e-mail i dokumentów

> [!IMPORTANT]
> 
> [Klient ujednoliconego etykietowania platformy Azure Information Protection](/azure/information-protection/rms-client/install-unifiedlabelingclient-app) obsługuje tę konfigurację, która jest również znana jako obowiązkowe etykietowanie. Aby uzyskać informacje o etykietowaniu wbudowanym w aplikacje pakietu Office, zobacz [tabele](#support-for-sensitivity-label-capabilities-in-apps) w sekcji możliwości na tej stronie, aby zapoznać się z minimalnymi wersjami.
>
> Aby użyć obowiązkowego etykietowania dokumentów, ale nie wiadomości e-mail, zobacz instrukcje w następnej sekcji, w których wyjaśniono, jak skonfigurować opcje specyficzne dla programu Outlook.
> 
> Aby użyć obowiązkowego etykietowania dla usługi Power BI, zobacz [Obowiązkowe zasady etykiet dla usługi Power BI](/power-bi/admin/service-security-sensitivity-label-mandatory-label-policy).

Po wybraniu ustawienia zasad **Wymagaj od użytkowników zastosowania etykiety do poczty e-mail i dokumentów** użytkownicy, do których przypisano zasady, muszą wybrać i zastosować etykietę poufności w następujących scenariuszach:

- W przypadku klienta ujednoliconego etykietowania usługi Azure Information Protection:
    - W przypadku dokumentów (Word, Excel, PowerPoint): po zapisaniu nieoznakowanego dokumentu lub zamknięciu dokumentu przez użytkowników.
    - W przypadku wiadomości e-mail (Outlook): w momencie wysyłania przez użytkowników wiadomości bez etykiet.

- W przypadku etykietowania wbudowanego w aplikacje pakietu Office:
    - W przypadku dokumentów (Word, Excel, PowerPoint): po otwarciu lub zapisaniu nieoznakowanego dokumentu.
    - W przypadku wiadomości e-mail (Outlook): w momencie wysyłania przez użytkowników wiadomości e-mail bez etykiet.

Dodatkowe informacje dotyczące wbudowanego etykietowania:

- Gdy użytkownicy zostaną poproszeni o dodanie etykiety poufności, ponieważ otwierają dokument bez etykiet, mogą dodać etykietę lub otworzyć dokument w trybie tylko do odczytu.

- Gdy obowiązuje obowiązkowe etykietowanie, użytkownicy nie mogą usuwać etykiet poufności z dokumentów, ale mogą zmienić istniejącą etykietę.

- Po włączeniu obowiązkowego etykietowania opcja drukowania w formacie PDF będzie niedostępna, gdy dokument zostanie oznaczony etykietą lub zaszyfrowany. Aby uzyskać więcej informacji, zobacz sekcję [pomocy technicznej dla plików PDF](#pdf-support) na tej stronie.

Aby uzyskać wskazówki dotyczące korzystania z tego ustawienia, zobacz informacje o [ustawieniach zasad](sensitivity-labels.md#what-label-policies-can-do).

> [!NOTE]
> Jeśli oprócz obowiązkowego etykietowania używasz domyślnego ustawienia zasad etykiet dla dokumentów i wiadomości e-mail: 
>
> Etykieta domyślna zawsze ma priorytet niż obowiązkowe etykietowanie. Jednak w przypadku dokumentów klient ujednoliconego etykietowania usługi Azure Information Protection stosuje etykietę domyślną do wszystkich nieoznakowanych dokumentów, podczas gdy wbudowane etykietowanie stosuje etykietę domyślną do nowych dokumentów, a nie do istniejących dokumentów, które nie są oznaczone etykietami. Ta różnica w zachowaniu oznacza, że w przypadku korzystania z obowiązkowego etykietowania z domyślnym ustawieniem etykiety użytkownicy prawdopodobnie będą monitować o stosowanie etykiety poufności częściej, gdy używają wbudowanego etykietowania niż w przypadku korzystania z klienta ujednoliconego etykietowania usługi Azure Information Protection.
> 
> Teraz wprowadzanie: aplikacje pakietu Office, które używają wbudowanego etykietowania i obsługują etykietę domyślną dla istniejących dokumentów. Aby uzyskać szczegółowe informacje, zobacz [tabelę możliwości](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) dla programów Word, Excel i PowerPoint.

## <a name="outlook-specific-options-for-default-label-and-mandatory-labeling"></a>Opcje specyficzne dla programu Outlook dla etykiety domyślnej i obowiązkowego etykietowania

W przypadku etykietowania wbudowanego zidentyfikuj minimalne wersje programu Outlook, które obsługują te funkcje, korzystając z [tabeli możliwości programu Outlook](#sensitivity-label-capabilities-in-outlook) na tej stronie oraz **wiersza Różne ustawienia etykiety domyślnej i obowiązkowego etykietowania**. Wszystkie wersje klienta ujednoliconego etykietowania usługi Azure Information Protection obsługują te opcje specyficzne dla programu Outlook.

Gdy aplikacja Outlook obsługuje domyślne ustawienie etykiety, które różni się od domyślnego ustawienia etykiety dla dokumentów:

- W konfiguracji zasad etykiet z portal zgodności Microsoft Purview na stronie **Zastosuj etykietę domyślną do wiadomości e-mail**: możesz określić wybór etykiety poufności, która będzie stosowana do wszystkich nieoznakowanych wiadomości e-mail lub bez etykiety domyślnej. To ustawienie jest niezależne od ustawienia **Zastosuj tę etykietę domyślnie do dokumentów** na poprzedniej stronie **Ustawienia zasad dla dokumentów** konfiguracji.

Gdy aplikacja Outlook nie obsługuje domyślnego ustawienia etykiety, które różni się od domyślnego ustawienia etykiety dla dokumentów: program Outlook zawsze będzie używać wartości określonej **dla opcji Zastosuj tę etykietę domyślnie do dokumentów** na stronie **Ustawienia zasad dla dokumentów** konfiguracji zasad etykiety.

Gdy aplikacja Outlook obsługuje wyłączanie obowiązkowego etykietowania:

- W konfiguracji zasad etykiet z portal zgodności Microsoft Purview na stronie **Ustawienia zasad**: wybierz pozycję **Wymagaj od użytkowników zastosowania etykiety do poczty e-mail lub dokumentów**. Następnie wybierz pozycję **Dalej** > **i** wyczyść pole wyboru **Wymagaj od użytkowników zastosowania etykiety do swoich wiadomości e-mail**. Zaznacz pole wyboru, jeśli chcesz, aby obowiązkowe etykietowanie było stosowane do wiadomości e-mail i dokumentów.

Gdy aplikacja Outlook nie obsługuje wyłączania obowiązkowego etykietowania: jeśli wybierzesz opcję **Wymagaj od użytkowników zastosowania etykiety do poczty e-mail lub dokumentów** jako ustawienia zasad, program Outlook zawsze będzie monitować użytkowników o wybranie etykiety dla wiadomości e-mail bez etykiet.

> [!NOTE]
> Jeśli skonfigurowano ustawienia zaawansowane programu **PowerShell OutlookDefaultLabel** i **DisableMandatoryInOutlook** przy użyciu poleceń cmdlet [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy) lub [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy) :
> 
> Wybrane wartości dla tych ustawień programu PowerShell są odzwierciedlone w konfiguracji zasad etykiet w portal zgodności Microsoft Purview i automatycznie działają w przypadku aplikacji Outlook, które obsługują te ustawienia. Inne zaawansowane ustawienia programu PowerShell pozostają obsługiwane tylko dla klienta usługi Azure Information Protection ujednoliconego etykietowania.

## <a name="configure-a-label-to-apply-smime-protection-in-outlook"></a>Konfigurowanie etykiety w celu zastosowania ochrony S/MIME w programie Outlook

> [!NOTE]
> Ta funkcja jest obecnie wdrażana na potrzeby wbudowanego etykietowania. Zidentyfikuj minimalne wersje programu Outlook obsługujące tę funkcję przy użyciu [tabeli możliwości programu Outlook](#sensitivity-label-capabilities-in-outlook) na tej stronie i wiersza **Zastosuj ochronę S/MIME**.
> 
> Jeśli skonfigurujesz etykietę do stosowania ochrony S/MIME, ale aplikacja Outlook jeszcze jej nie obsługuje, etykieta będzie nadal wyświetlana w programie Outlook i może zostać zastosowana, ale ustawienia S/MIME zostaną zignorowane. Nie będzie można wybrać tej etykiety dla zasad automatycznego etykietowania programu Exchange.

Ta konfiguracja nie jest dostępna w Centrum zgodności usługi Microsoft Purview. Po [nawiązaniu połączenia z programem Office 365 Security & Compliance Center programu PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell) należy użyć ustawień zaawansowanych programu PowerShell z poleceniem cmd [Set-Label](/powershell/module/exchange/set-label) lub [New-Label](/powershell/module/exchange/new-label).

Tych ustawień należy używać tylko wtedy, gdy masz działające [wdrożenie S/MIME](/microsoft-365/security/office-365-security/s-mime-for-message-signing-and-encryption) i chcesz, aby etykieta automatycznie zastosowała tę metodę ochrony dla wiadomości e-mail, a nie [domyślnej ochrony korzystającej z szyfrowania usługi Rights Management z usługi Azure Information Protection](encryption-sensitivity-labels.md). Wynikowa ochrona będzie taka sama, jak wtedy, gdy użytkownik ręcznie wybierze opcje S/MIME z programu Outlook.

|Konfiguracja  |Klucz/wartość ustawienia zaawansowanego |
|---------|---------|
|**Podpis cyfrowy S/MIME** | SMimeSign="True" |
|**Szyfrowanie S/MIME** | SMimeEncrypt="True"|

Etykieta skonfigurowana dla tych ustawień nie musi być skonfigurowana pod kątem szyfrowania w portalu zgodności. Jeśli jednak tak jest, ochrona S/MIME zastępuje szyfrowanie usługi Rights Management tylko w programie Outlook. W przypadku innych aplikacji etykieta stosuje ustawienia szyfrowania określone w portal zgodności Microsoft Purview.

Przykładowe polecenia programu PowerShell, w których identyfikator GUID etykiety poufności to **8faca7b8-8d20-48a3-8ea2-0f96310a848e**:

```PowerShell
Set-Label -Identity "8faca7b8-8d20-48a3-8ea2-0f96310a848e" -AdvancedSettings @{SMimeSign="True"}

Set-Label -Identity "8faca7b8-8d20-48a3-8ea2-0f96310a848e" -AdvancedSettings @{SMimeEncrypt="True"}
```

Aby uzyskać więcej pomocy w określaniu ustawień zaawansowanych programu [PowerShell, zobacz Porady programu PowerShell dotyczące określania ustawień zaawansowanych](create-sensitivity-labels.md#powershell-tips-for-specifying-the-advanced-settings).

## <a name="pdf-support"></a>Obsługa plików PDF

Aby uzyskać wbudowane etykietowanie, użyj tabel w sekcji [możliwości](#support-for-sensitivity-label-capabilities-in-apps) na tej stronie, aby zidentyfikować obsługiwane minimalne wersje. Klient ujednoliconego etykietowania platformy Azure Information Protection nie obsługuje formatu PDF w aplikacjach pakietu Office.

Programy Word, Excel i PowerPoint obsługują następujące metody konwertowania dokumentu pakietu Office na dokument PDF:

- Plik > zapisz jako > PDF 
- Eksport > plików w formacie PDF >
- Udostępnianie > wysyłanie kopii > PDF

Ta akcja jest rejestrowana przy użyciu zdarzenia inspekcji **Zmieniono nazwę pliku** z grupy inspekcji [Działania plików i stron](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities) . W wynikach wyszukiwania inspekcji w portalu zgodności zostaną wyświetlone szczegóły tego zdarzenia inspekcji **zawierające wartość SensitivityLabeledFileRenamed** dla pola **Działanie** .

Po utworzeniu pliku PDF dziedziczy etykietę za pomocą wszelkich oznaczeń zawartości i szyfrowania. Zaszyfrowane pliki PDF można otwierać przy użyciu przeglądarki Microsoft Edge w systemie Windows lub Mac. Aby uzyskać więcej informacji i alternatywnych czytelników, zobacz [Które czytniki PDF są obsługiwane dla chronionych plików PDF?](/azure/information-protection/rms-client/protected-pdf-readers#viewing-protected-pdfs-in-microsoft-edge-on-windows-or-mac)

Scenariusze pdf nie są obsługiwane:

- Drukowanie w formacie PDF
    
    Jeśli użytkownicy wybiorą tę opcję, zostaną ostrzeżeni, że dokument utraci ochronę etykiety i szyfrowania (jeśli zostanie zastosowany) i musi potwierdzić kontynuowanie. Jeśli zasady etykiet poufności wymagają uzasadnienia, aby usunąć etykietę lub obniżyć jej klasyfikację, zobaczą ten monit.
    
    Ponieważ ta opcja usuwa etykietę poufności, ta opcja nie będzie dostępna dla użytkowników, jeśli używasz obowiązkowego etykietowania. Ta konfiguracja odnosi się do ustawienia zasad etykiet poufności, które wymaga od użytkowników zastosowania etykiety do wiadomości e-mail i dokumentów.

- Format i szyfrowanie plików PDF/A
    
     Ten format PDF przeznaczony do archiwizacji długoterminowej nie jest obsługiwany, gdy etykieta stosuje szyfrowanie i uniemożliwi użytkownikom konwertowanie dokumentów pakietu Office na format PDF. Aby uzyskać informacje o konfiguracji, zobacz dokumentację zasady grupy [dotyczącą wymuszania zgodności plików PDF z normą ISO 19005-1 (PDF/A)](https://admx.help/?Category=Office2016&Policy=office16.Office.Microsoft.Policies.Windows::L_EnforcePDFcompliancewithISO190051PDFA).
    
- Ochrona haseł i szyfrowanie
    
    Opcja **Ochrona szyfrowania****dokumentów** >  za **pomocą hasła** **informacji o** >  pliku  >  nie jest obsługiwana, gdy etykieta dokumentu stosuje szyfrowanie. W tym scenariuszu opcja szyfrowania przy użyciu hasła staje się niedostępna dla użytkowników.

Aby uzyskać więcej informacji na temat tej funkcji, zobacz ogłoszenie [Stosowanie etykiet poufności do plików PDF utworzonych za pomocą aplikacji pakietu Office](https://insider.office.com/blog/apply-sensitivity-labels-to-pdfs-created-with-office-apps).

## <a name="auditing-labeling-activities"></a>Inspekcja działań etykietowania

Aby uzyskać informacje o zdarzeniach inspekcji generowanych przez działania etykiet poufności, zobacz sekcję [Działania etykiet poufności](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) w sekcji [Wyszukaj dziennik inspekcji w portal zgodności Microsoft Purview](search-the-audit-log-in-security-and-compliance.md).

Te informacje inspekcji są wizualnie reprezentowane w [eksploratorze zawartości](data-classification-content-explorer.md) i [eksploratorze działań](data-classification-activity-explorer.md) , aby ułatwić zrozumienie sposobu użycia etykiet poufności i lokalizacji tej zawartości oznaczonej etykietą. 

Możesz również tworzyć raporty niestandardowe z wybranym oprogramowaniem do zarządzania informacjami o zabezpieczeniach i zdarzeniami (SIEM) podczas [eksportowania i konfigurowania rekordów dziennika inspekcji](export-view-audit-log-records.md). Aby uzyskać więcej rozwiązań do raportowania na większą skalę, zobacz [dokumentację interfejsu API działania zarządzania Office 365](/office/office-365-management-api/office-365-management-activity-api-reference).

> [!TIP]
> Aby ułatwić tworzenie raportów niestandardowych, zobacz następujące wpisy w blogu:
> - [Działania dziennika inspekcji usługi Microsoft Purview za pośrednictwem interfejsu API zarządzania usługi O365 — część 1](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/microsoft-365-compliance-audit-log-activities-via-o365/ba-p/2957171)
> - [Działania dziennika inspekcji usługi Microsoft Purview za pośrednictwem interfejsu API zarządzania O365 — część 2](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/microsoft-365-compliance-audit-log-activities-via-o365/ba-p/2957297)

## <a name="end-user-documentation"></a>Dokumentacja użytkownika końcowego

- [Stosowanie etykiet wrażliwości do plików i wiadomości e-mail w pakiecie Office](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
    - [Znane problemy z etykietami poufności w pakiecie Office](https://support.microsoft.com/en-us/office/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [Automatyczne stosowanie lub rekomendowanie etykiet poufności do plików i wiadomości e-mail w pakiecie Office](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)
    - [Znane problemy z automatycznym stosowaniem lub zalecaniem etykiet poufności](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)
