---
title: Microsoft Edge
description: W tym artykule wyjaśniono Microsoft Edge wdrażania i aktualizowania przeglądarki
keywords: przeglądarka, Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: aab02ec260f0131ab32d28834152f50b84abce21
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2022
ms.locfileid: "63016536"
---
# <a name="microsoft-edge"></a>Microsoft Edge

[Microsoft Edge](https://www.microsoft.com/edge) światowej klasy wydajność i wartość dzięki:

- Większa prywatność i ochrona przed zagrożeniami zewnętrznymi.
- Większa produktywność — szybki Office dostępu do aplikacji, plików, witryn i wbudowanych Microsoft Search.
- Bezproblemowa synchronizacja między urządzeniami za pomocą pomocy technicznej i profilów międzyplatformowych.

> [!IMPORTANT]
> 15 czerwca 2022 r. zostanie wycofana aplikacja komputerowa Internet Explorer 11 (aby uzyskać listę zakresów pomocy technicznej, zobacz Często zadawane [pytania](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/internet-explorer-11-desktop-app-retirement-faq/ba-p/2366549)). Te same aplikacje i witryny IE11, z których obecnie korzystasz, można otwierać w Microsoft Edge w trybie programu Internet Explorer. [Dowiedz się więcej tutaj](https://blogs.windows.com/windowsexperience/2021/05/19/the-future-of-internet-explorer-on-windows-10-is-in-microsoft-edge/).

## <a name="updates-to-microsoft-edge"></a>Aktualizacje Microsoft Edge

Microsoft Managed Desktop wdraża kanał [rozszerzonej stabilnej](/deployedge/microsoft-edge-channels#extended-stable-channel) wersji Microsoft Edge, który jest automatycznie aktualizowany co osiem tygodni. Aktualizacje na kanale rozszerzonej stabilnej wersji są stopniowo [](/deployedge/microsoft-edge-update-progressive-rollout) Microsoft Edge grupy produktów, aby zapewnić klientom najlepsze środowisko.

Kanał [Beta jest](/deployedge/microsoft-edge-channels#beta-channel) wdrożony na urządzeniach w grupie Test w celu weryfikacji reprezentatywnej w organizacji. Ten kanał jest w pełni obsługiwany i automatycznie aktualizowany o nowe funkcje co około cztery tygodnie.

> [!IMPORTANT]
> Aby zapewnić, Microsoft Edge aktualizacje są poprawne, nie modyfikuj zasad Microsoft Edge [aktualizacji](/deployedge/microsoft-edge-update-policies).

## <a name="settings-managed-by-microsoft-managed-desktop"></a>Ustawienia zarządzane przez firmę Microsoft Managed Desktop

Microsoft Managed Desktop został utworzony domyślny zestaw zasad dla aplikacji Microsoft Edge zabezpieczania przeglądarki. Domyślne ustawienia przeglądarki są następujące:

### <a name="microsoft-edge-extensions"></a>Microsoft Edge rozszerzenia

Plan bazowy zabezpieczeń dla Microsoft Edge na Microsoft Managed Desktop urządzeniach przenośnych ustawia dwie zasady w celu wyłączenia wszystkich rozszerzeń Chrome i bezpiecznego użytkowników. Aby włączyć i wdrożyć rozszerzenia w środowisku, Ustawienia [zarządzasz samodzielnie](#settings-you-manage).

| Ustawienie | Wartość domyślna | Opis |
| ------ | ------ | ------ |
| Lista zablokowanych instalacji rozszerzeń | Wszystkie | Microsoft Managed Desktop te zasady, aby zapobiec instalowaniu rozszerzeń Chrome w zarządzanych punktach końcowych. Z modelem rozszerzenia Chromium związane są znane zagrożenia, takie jak ochrona przed utratą danych, prywatność i inne zagrożenia, które mogą naruszyć urządzenia. |
| Zezwalanie na natywne hosty wiadomości na poziomie użytkownika (instalowane bez uprawnień administratora) | Wyłączone | W przypadku wyłączenia tych zasad Microsoft Edge używać tylko natywnych hostów wiadomości zainstalowanych na poziomie systemu. Natywne hosty wiadomości są częścią rozszerzeń przeglądarki Chrome, które umożliwiają przeglądarce interakcje z innymi częściami punktu końcowego użytkownika, tworząc różne problemy dotyczące zabezpieczeń. |

### <a name="secure-sockets-layer-tlsssl"></a>Secure Sockets Layer (TLS/SSL)

| Ustawienie | Wartość domyślna | Opis
| ------ | ------ | ------ |
| Minimalna wersja TLS | Minimalna obsługiwana wartość TLS 1,2 | Jeśli chcesz używać mniej bezpiecznej 1.1 TLS, możesz złożyć wniosek o ich użycie. |
| Zezwalaj użytkownikom na kontynuowanie ze strony z ostrzeżeniem SSL | Wyłączone | Nie zalecamy włączania tego ustawienia, ponieważ umożliwia ono użytkownikom odwiedzanie witryn z błędami TSL. |

### <a name="microsoft-defender-smartscreen"></a>Microsoft Defender SmartScreen

| Ustawienie | Wartość domyślna | Opis
| ------ | ------ | ------ |
| Konfigurowanie Windows Defender SmartScreen | Włączone | Domyślnie włączone, aby chronić użytkowników. |
| Windows Defender monitów filtru SmartScreen dla witryn | Włączone | Nie zalecamy wyłączania tego ustawienia, ponieważ pozwoliłoby to użytkownikom na ignorowanie ostrzeżeń i kontynuowanie do potencjalnie złośliwych witryn. |
| Zapobieganie pomijaniu ostrzeżeń filtru SmartScreen Windows Defender plików do pobrania | Włączone | Nie zalecamy wyłączania tego ustawienia, ponieważ umożliwiałoby użytkownikom ignorowanie ostrzeżeń i pobieranie niesprawdzonych plików do pobrania. |

### <a name="adobe-flash"></a>Adobe Flash

| Ustawienie | Wartość domyślna | Opis
| ------ | ------ | ------ |
| Domyślne ustawienie programu Adobe Flash | Wyłączone | Ze względu na związane z tym zagrożenia bezpieczeństwa nie zalecamy korzystania z programu Flash. <br><br> Jeśli nadal masz procesy, które zależą od programu Flash, ustaw zasady **[PluginsAllowedForUrls](/deployedge/microsoft-edge-policies#pluginsallowedforurls)** , aby włączyć program Flash dla witryn, które go potrzebują. Jeśli nie możesz zachować listy witryn dozwolonych do używania z lampą błyskową, poproś o zmianę wartości na Kliknij, aby odtworzyć **, co** pozwoli użytkownikom wybrać odpowiednią opcję uruchomienia flash. |

### <a name="password-manager"></a>Menedżer haseł

| Ustawienie | Wartość domyślna | Opis
| ------ | ------ | ------ |
| Włączanie zapisywania haseł w menedżerze haseł | Wyłączone | Menedżer haseł jest domyślnie wyłączony. Jeśli chcesz, aby ta funkcja była włączona, zamieć zgłoszenie do pomocy technicznej, a nasi inżynierowie usługi mogą włączyć to ustawienie w Twoim środowisku. |

### <a name="internet-explorer-mode-in-microsoft-edge"></a>Tryb programu Internet Explorer w programie Microsoft Edge

Tryb IE Microsoft Edge ułatwia korzystanie ze wszystkich witryn, których potrzebuje Twoja organizacja, w jednej przeglądarce. Korzysta on ze zintegrowanego Chromium witryn zgodnych z aparatem Chromium renderowania. Microsoft Edge korzysta z aparatu Trident MSHTML z programu Internet Explorer 11 (IE11) w przypadku witryn, które nie są lub mają zależności od funkcji programu Internet Explorer. [Dowiedz się więcej](/DeployEdge/edge-ie-mode)

Microsoft Managed Desktop domyślnie włącza tryb programu Internet Explorer dla urządzeń.

| Ustawienie | Wartość domyślna | Opis
| ------ | ------ | ------ |
| Integracja trybu programu Internet Explorer | Tryb programu Internet Explorer | Domyślnie urządzenia są ustawione do korzystania z trybu programu Internet Explorer, ale można je skonfigurować tak, aby zamiast tego otwierały witryny w autonomicznym oknie programu Internet Explorer 11. Aby zmienić to zachowanie, należy złożyć wniosek o pomoc techniczną. |
| Dodawanie witryn do Enterprise witryny w trybie online | Zobacz opis | Aby witryny otwierały się w trybie programu Internet Explorer, należy je uwzględnić na [Enterprise witryny](/DeployEdge/edge-ie-mode-sitelist). Za konserwację i wdrażanie Enterprise witryny sieci Web odpowiada Twoja odpowiedzialność. Aby uzyskać szczegółowe informacje, [zobacz Konfigurowanie przy użyciu zasad Enterprise Lista witryn w trybie online](/DeployEdge/edge-ie-mode-policies#configure-using-the-configure-the-enterprise-mode-site-list-policy). |

### <a name="other-settings"></a>Inne ustawienia

| Ustawienie | Wartość domyślna | Opis
| ------ | ------ | ------ |
| Włączanie izolacji witryny dla każdej witryny | Włączone | Gdy te zasady są włączone, użytkownicy nie mogą zrezygnować z domyślnego zachowania, w którym każda witryna działa w procesie własnym. |
| Obsługiwane schematy uwierzytelniania | NTLM, Wynegocjuj | Microsoft Managed Desktop nie obsługuje schematów uwierzytelniania podstawowego lub szyfrowanego. |
| Automatyczne importowanie danych i ustawień innej przeglądarki przy pierwszym uruchomieniu | Automatycznie zaimportuj wszystkie obsługiwane typy danych i ustawienia z domyślnej przeglądarki. | Po zastosowaniu tych zasad środowisko pierwszego uruchomienia pominie sekcję importowania, minimalizując interakcję użytkownika. Dane przeglądarki ze starszych wersji programu Microsoft Edge zawsze będą migrowane dyskretnie przy pierwszym uruchomieniu, niezależnie od tego ustawienia. |

## <a name="settings-you-manage"></a>Ustawienia zarządzasz

Możesz wdrożyć dowolne Microsoft Edge, które nie zostały wcześniej opisane, przy użyciu profilu Szablony administracyjne w programie Microsoft Intune. Aby uzyskać szczegółowe informacje, [zobacz Konfigurowanie Microsoft Edge zasad za pomocą Microsoft Intune](/deployedge/configure-edge-with-intune). Jeśli chcesz ocenić zasady, które nie są obecnie uwzględnione w szablonach administracyjnych usługi Microsoft Edge w usłudze Intune, możesz użyć ustawień niestandardowych dla Windows 10 w usłudze Intune.

| Ustawienie | Opis
| ------ | ------ |
| Włączanie określonych rozszerzeń Chrome | Szablon administracyjny oferuje ustawienie wdrażania określonych rozszerzeń Chrome z Microsoft Intune. Możesz to znaleźć w **tece Konfiguracja > Microsoft Edge > i > zezwalaj na instalowane określone rozszerzenia**. |
| Instalowanie rozszerzeń w trybie dyskretnym | Możesz również użyć szablonu administracyjnego, aby skonfigurować Microsoft Edge instalować rozszerzenia bez powiadamiania użytkownika. Możesz to znaleźć w te **sposób: Konfiguracja > Microsoft Edge > i rozszerzenia >, które mają być instalowane dyskretnie**. |
| Microsoft Edge zasad aktualizacji | Aby zapewnić, Microsoft Edge aktualizacje są poprawne, nie modyfikuj zasad Microsoft Edge [aktualizacji](/deployedge/microsoft-edge-update-policies). |
| Inne typowe zasady przedsiębiorstwa | Microsoft Edge oferuje wiele innych zasad. Poniżej przedstawiono niektóre z nich najbardziej typowych: <ul> <li> [Konfigurowanie witryn w trybie listy Enterprise witryny i w trybie plików IE](/deployedge/edge-ie-mode-sitelist)</li><li> [Konfigurowanie ustawień uruchamiania, strony głównej i strony nowej karty](/deployedge/microsoft-edge-policies#startup-home-page-and-new-tab-page)</li> <li> [Konfigurowanie ustawień gier Surf](/deployedge/microsoft-edge-policies#allowsurfgame)</li> <li> [Konfigurowanie ustawień serwera proxy](/deployedge/microsoft-edge-policies#proxy-server)</li></ul>
