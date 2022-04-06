---
title: Omówienie planu Ochrona punktu końcowego w usłudze Microsoft Defender 1
description: Zapoznaj się z omówieniem usługi Defender for Endpoint Plan 1. Dowiedz się więcej o funkcjach i możliwościach zawartych w tej subskrypcji programu Endpoint Protection.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 01/19/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.custom: intro-overview
ms.openlocfilehash: 774d54aee080fbe3d6f5576fb29c85d887717b70
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663517"
---
# <a name="overview-of-microsoft-defender-for-endpoint-plan-1"></a>Omówienie planu Ochrona punktu końcowego w usłudze Microsoft Defender 1

**Dotyczy**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Ochrona punktu końcowego w usłudze Microsoft Defender to platforma zabezpieczeń punktów końcowych przedsiębiorstwa, która ułatwia organizacjom takim jak Twoje zapobieganie zaawansowanym zagrożeniom, wykrywanie ich, badanie i reagowanie na nie. Z przyjemnością informujemy, że usługa Defender for Endpoint jest teraz dostępna w dwóch planach: 

- **Defender for Endpoint Plan 1**, opisany w tym artykule; I 
- **[Usługa Defender for Endpoint Plan 2](microsoft-defender-endpoint.md)**, ogólnie dostępna i wcześniej znana jako [Defender for Endpoint](microsoft-defender-endpoint.md).

Zielone pola na poniższej ilustracji przedstawiają elementy zawarte w usłudze Defender for Endpoint Plan 1:

:::image type="content" source="../../media/mde-p1/mde-p1-overview-diagram.png" alt-text="Co jest zaszczepione za pomocą usługi Defender for Endpoint Plan 1" lightbox="../../media/mde-p1/mde-p1-overview-diagram.png":::

Skorzystaj z tego przewodnika, aby:

- [Zapoznaj się z omówieniem elementów uwzględnionych w usłudze Defender for Endpoint Plan 1](#defender-for-endpoint-plan-1-capabilities)
- [Porównanie planu 1 ochrony punktu końcowego w usłudze Defender z planem 2](defender-endpoint-plan-1-2.md)
- [Dowiedz się, jak skonfigurować i skonfigurować usługę Defender for Endpoint Plan 1](mde-p1-setup-configuration.md)
- [Wprowadzenie przy użyciu portalu Microsoft 365 Defender, w którym można wyświetlać zdarzenia i alerty, zarządzać urządzeniami i korzystać z raportów dotyczących wykrytych zagrożeń](mde-plan1-getting-started.md)
- [Omówienie konserwacji i operacji](mde-p1-maintenance-operations.md)

> [!TIP]
> [Dowiedz się więcej o różnicach między usługą Defender for Endpoint Plan 1 i Planem 2](defender-endpoint-plan-1-2.md).

## <a name="defender-for-endpoint-plan-1-capabilities"></a>Możliwości usługi Defender for Endpoint Plan 1

Usługa Defender for Endpoint Plan 1 obejmuje następujące możliwości:

- **[Ochrona nowej generacji](#next-generation-protection)** , która obejmuje wiodącą w branży, niezawodną ochronę przed złośliwym kodem i ochronę antywirusową
- **[Ręczne akcje reagowania](#manual-response-actions)**, takie jak wysyłanie pliku do kwarantanny, które zespół ds. zabezpieczeń może podjąć na urządzeniach lub plikach po wykryciu zagrożeń
- **[Możliwości zmniejszania obszaru ataków](#attack-surface-reduction)** , które wzmacniają zabezpieczenia urządzeń, zapobiegają atakom zerowym i zapewniają szczegółową kontrolę nad dostępem do punktów końcowych i zachowaniami
- **[Scentralizowana konfiguracja i zarządzanie](#centralized-management)** za pomocą portalu Microsoft 365 Defender i integracja z Microsoft Endpoint Manager
- **[Ochrona różnych platform](#cross-platform-support)**, w tym urządzeń z systemem Windows, macOS, iOS i Android

Poniższe sekcje zawierają więcej szczegółów na temat tych możliwości. 

## <a name="next-generation-protection"></a>Ochrona nowej generacji

Ochrona nowej generacji obejmuje niezawodny program antywirusowy i ochronę przed złośliwym kodem. Dzięki ochronie nowej generacji otrzymujesz następujące elementy: 

- Ochrona antywirusowa oparta na zachowaniu, heurystycznym i w czasie rzeczywistym 
- Ochrona dostarczana przez chmurę, która obejmuje niemal natychmiastowe wykrywanie i blokowanie nowych i pojawiających się zagrożeń 
- Dedykowana ochrona i aktualizacje produktów, w tym aktualizacje związane z Program antywirusowy Microsoft Defender 

Aby dowiedzieć się więcej, zobacz [Omówienie ochrony nowej generacji](next-generation-protection.md).

## <a name="manual-response-actions"></a>Ręczne akcje odpowiedzi

Ręczne akcje reagowania to akcje, które zespół ds. zabezpieczeń może wykonać w przypadku wykrycia zagrożeń w punktach końcowych lub plikach. Usługa Defender for Endpoint zawiera pewne [ręczne akcje reagowania, które można wykonać na urządzeniu](respond-machine-alerts.md) , które jest wykrywane jako potencjalnie zagrożone lub ma podejrzaną zawartość. Można również uruchamiać [akcje reagowania na pliki](respond-file-alerts.md) , które są wykrywane jako zagrożenia. W poniższej tabeli podsumowano akcje ręcznej odpowiedzi dostępne w usłudze Defender for Endpoint Plan 1. <br/><br/>

| Plik/urządzenie | Akcja | Opis |
|:---|:---|:---|
| Urządzenie | Uruchomiono skanowanie antywirusowe | Uruchamia skanowanie antywirusowe. W przypadku wykrycia jakichkolwiek zagrożeń na urządzeniu te zagrożenia są często rozwiązywane podczas skanowania antywirusowego. |
| Urządzenie | Izolowanie urządzenia | Odłącza urządzenie od sieci organizacji przy zachowaniu łączności z usługą Defender for Endpoint. Ta akcja umożliwia monitorowanie urządzenia i w razie potrzeby podjęcie dalszych działań. |
| Plik | Zatrzymywanie i kwarantanna |Uniemożliwia uruchamianie procesów i kwarantannę skojarzonych plików. |
| Plik | Dodawanie wskaźnika w celu zablokowania lub zezwolenia na plik | Wskaźniki blokują możliwość odczytywania, zapisu lub wykonywania przenośnych plików wykonywalnych na urządzeniach. <p>Zezwalaj na wskaźniki uniemożliwiające blokowanie lub korygowanie plików. |

Aby dowiedzieć się więcej, zobacz następujące artykuły:

- [Akcje reagowania na urządzeniach](respond-machine-alerts.md) 
- [Akcje reagowania na pliki](respond-file-alerts.md)

## <a name="attack-surface-reduction"></a>Zmniejszanie obszaru podatnego na ataki

Powierzchnie ataków organizacji to wszystkie miejsca, w których jesteś narażony na cyberataki. Dzięki usłudze Defender for Endpoint Plan 1 możesz zmniejszyć obszar ataków, chroniąc urządzenia i aplikacje używane przez organizację. Możliwości zmniejszania obszaru ataków zawarte w usłudze Defender for Endpoint Plan 1 zostały opisane w poniższych sekcjach.

- [Reguły zmniejszania obszaru podatnego na ataki](#attack-surface-reduction-rules)
- [Ograniczanie ryzyka wymuszania okupu](#ransomware-mitigation)
- [Sterowanie urządzeniem](#device-control)
- [Ochrona sieci Web](#web-protection)
- [Ochrona sieci](#web-protection)
- [Zapora sieciowa](#network-firewall)
- [Kontrola aplikacji](#application-control)

Aby dowiedzieć się więcej na temat możliwości zmniejszania obszaru podatnego na ataki w usłudze Defender for Endpoint, zobacz [Omówienie zmniejszania obszaru ataków](overview-attack-surface-reduction.md).

### <a name="attack-surface-reduction-rules"></a>Reguły zmniejszania obszaru podatnego na ataki

Reguły zmniejszania obszaru ataków dotyczą pewnych zachowań oprogramowania, które są uważane za ryzykowne. Takie zachowania obejmują:

- Uruchamianie plików wykonywalnych i skryptów, które próbują pobrać lub uruchomić inne pliki
- Uruchamianie zaciemnionych lub w inny sposób podejrzanych skryptów
- Inicjowanie zachowań, których aplikacje zwykle nie inicjują podczas normalnej pracy

Uzasadnione aplikacje biznesowe mogą wykazywać takie zachowania programowe; Jednak te zachowania są często uważane za ryzykowne, ponieważ są często nadużywane przez osoby atakujące przez złośliwe oprogramowanie. Reguły zmniejszania obszaru podatnego na ataki mogą ograniczać ryzykowne zachowania i pomagać w zachowaniu bezpieczeństwa organizacji.

Aby dowiedzieć się więcej, zobacz [Używanie reguł zmniejszania obszaru ataków w celu zapobiegania infekcji złośliwym oprogramowaniem](attack-surface-reduction.md).

### <a name="ransomware-mitigation"></a>Ograniczanie ryzyka wymuszania okupu

Dzięki kontrolowanej kontroli dostępu do folderów uzyskasz środki zaradcze wymuszające okup. Kontrolowany dostęp do folderów umożliwia tylko zaufanym aplikacjom dostęp do chronionych folderów w punktach końcowych. Aplikacje są dodawane do listy zaufanych aplikacji na podstawie ich częstości występowania i reputacji. Twój zespół ds. operacji zabezpieczeń może również dodawać lub usuwać aplikacje z listy zaufanych aplikacji.

Aby dowiedzieć się więcej, zobacz [Protect important folders with controlled folder access (Ochrona ważnych folderów przy użyciu kontrolowanego dostępu do folderów](controlled-folders.md)).

### <a name="device-control"></a>Sterowanie urządzeniem

Czasami zagrożenia dla urządzeń organizacji mają postać plików na dyskach wymiennych, takich jak dyski USB. Usługa Defender for Endpoint oferuje możliwości, które pomagają zapobiegać zagrożeniom, które mogą uniknąć naruszenia urządzeń przez nieautoryzowane urządzenia peryferyjne. Usługę Defender for Endpoint można skonfigurować tak, aby blokowała lub zezwalała na wymienne urządzenia i pliki na urządzeniach wymiennych. 

Aby dowiedzieć się więcej, zobacz [Sterowanie urządzeniami USB i nośnikami wymiennymi](control-usb-devices-using-intune.md).

### <a name="web-protection"></a>Ochrona sieci Web

Dzięki ochronie w Internecie można chronić urządzenia organizacji przed zagrożeniami internetowymi i niepożądaną zawartością. Ochrona w Internecie obejmuje ochronę przed zagrożeniami w Internecie i filtrowanie zawartości internetowej.

- [Ochrona przed zagrożeniami](web-threat-protection.md) internetowymi uniemożliwia dostęp do witryn wyłudzających informacje, wektorów złośliwego oprogramowania, witryn wykorzystujących luki w zabezpieczeniach, witryn niezaufanych lub o niskiej reputacji oraz witryn, które jawnie blokujesz.
- [Filtrowanie zawartości internetowej](web-content-filtering.md) uniemożliwia dostęp do niektórych witryn na podstawie ich kategorii. Kategorie mogą obejmować treści dla dorosłych, witryny rekreacyjne, witryny odpowiedzialności prawnej i inne.

Aby dowiedzieć się więcej, zobacz [Ochrona w Internecie](web-protection-overview.md).

### <a name="network-protection"></a>Ochrona sieci

Dzięki ochronie sieci możesz uniemożliwić organizacji dostęp do niebezpiecznych domen, które mogą hostować wyłudzanie informacji, luki w zabezpieczeniach i inną złośliwą zawartość w Internecie. 

Aby dowiedzieć się więcej, zobacz [Ochrona sieci](network-protection.md).

### <a name="network-firewall"></a>Zapora sieciowa

Dzięki ochronie zapory sieciowej można ustawić reguły określające, który ruch sieciowy może przepływać do lub z urządzeń organizacji. Za pomocą zapory sieciowej i zaawansowanych zabezpieczeń, które można uzyskać w usłudze Defender for Endpoint, możesz:

- Zmniejszanie ryzyka zagrożeń bezpieczeństwa sieci
- Ochrona poufnych danych i własności intelektualnej
- Rozszerzanie inwestycji w zabezpieczenia

Aby dowiedzieć się więcej, zobacz [Windows Defender Firewall with advanced security (Zapora Windows Defender z zaawansowanymi zabezpieczeniami](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)).

### <a name="application-control"></a>Kontrola aplikacji

Kontrola aplikacji chroni punkty końcowe Windows, uruchamiając tylko zaufane aplikacje i kod w rdzeniu systemowym (jądrze). Twój zespół ds. zabezpieczeń może zdefiniować reguły kontroli aplikacji, które uwzględniają atrybuty aplikacji, takie jak kodowanie certyfikatów, reputacja, proces uruchamiania i nie tylko. Kontrola aplikacji jest dostępna w Windows 10 lub nowszym.

Aby dowiedzieć się więcej, zobacz [Kontrola aplikacji dla Windows](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control).

## <a name="centralized-management"></a>Scentralizowane zarządzanie

Usługa Defender for Endpoint Plan 1 obejmuje portal Microsoft 365 Defender, który umożliwia zespołowi ds. zabezpieczeń wyświetlanie bieżących informacji o wykrytych zagrożeniach, wykonywanie odpowiednich działań w celu wyeliminowania zagrożeń i centralne zarządzanie ustawieniami ochrony przed zagrożeniami w organizacji.

Aby dowiedzieć się więcej, zobacz [omówienie portalu Microsoft 365 Defender](portal-overview.md).

### <a name="role-based-access-control"></a>Kontrola dostępu oparta na rolach

Korzystając z kontroli dostępu opartej na rolach (RBAC), administrator zabezpieczeń może tworzyć role i grupy w celu udzielenia odpowiedniego dostępu do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Dzięki kontroli RBAC masz szczegółową kontrolę nad tym, kto może uzyskać dostęp do Defender dla Chmury i co widzą i robią. 

Aby dowiedzieć się więcej, zobacz [Zarządzanie dostępem do portalu przy użyciu kontroli dostępu opartej na rolach](rbac.md).

### <a name="reporting"></a>Raportowanie

Portal Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) zapewnia łatwy dostęp do informacji o wykrytych zagrożeniach i akcjach w celu rozwiązania tych zagrożeń. 

- Strona **główna** zawiera karty pokazujące, którzy użytkownicy lub urządzenia są narażeni na ryzyko, ile zagrożeń zostało wykrytych oraz jakie alerty/zdarzenia zostały utworzone.
- Sekcja **Zdarzenia & alerty** zawiera listę wszystkich zdarzeń, które zostały utworzone w wyniku wyzwolonych alertów. Alerty i zdarzenia są generowane w miarę wykrywania zagrożeń na różnych urządzeniach.
- Centrum **akcji** zawiera listę wykonanych akcji korygowania. Jeśli na przykład plik zostanie wysłany do kwarantanny lub adres URL zostanie zablokowany, każda akcja zostanie wyświetlona w Centrum akcji na karcie **Historia** .
- Sekcja **Raporty** zawiera raporty pokazujące wykryte zagrożenia i ich stan. 

Aby dowiedzieć się więcej, zobacz [Wprowadzenie z Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](mde-plan1-getting-started.md).

### <a name="apis"></a>Interfejsów api

Za pomocą interfejsów API usługi Defender for Endpoint można zautomatyzować przepływy pracy i zintegrować je z niestandardowymi rozwiązaniami organizacji. 

Aby dowiedzieć się więcej, zobacz [Defender for Endpoint APIs (Interfejsy API usługi Defender for Endpoint](management-apis.md)). 

## <a name="cross-platform-support"></a>Obsługa wielu platform

Większość organizacji korzysta z różnych urządzeń i systemów operacyjnych. Obecnie usługa Defender for Endpoint Plan 1 obsługuje następujące systemy operacyjne:

- Windows 7 (wymagana ESU)
- Windows 8.1
- Windows 10, wersja 1709 lub nowsza
- macOS: 11.5 (Big Sur), 10.15.7 (Catalina) lub 10.14.6 (Mojave)
- iOS
- System operacyjny Android

## <a name="next-steps"></a>Następne kroki

- [Porównanie planu Ochrona punktu końcowego w usłudze Microsoft Defender 1 z planem 2](defender-endpoint-plan-1-2.md)
- [Instalowanie i konfigurowanie ochrony punktu końcowego w usłudze Defender (plan 1)](mde-p1-setup-configuration.md)
- [Wprowadzenie z usługą Defender for Endpoint Plan 1](mde-plan1-getting-started.md)
- [Zarządzanie usługą Defender for Endpoint Plan 1](mde-p1-maintenance-operations.md)
