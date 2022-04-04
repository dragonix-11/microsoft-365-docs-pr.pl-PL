---
title: Omówienie Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1
description: Uzyskaj omówienie usługi Defender dla punktu końcowego (plan 1). Poznaj funkcje i możliwości zawarte w tej subskrypcji ochrony punktu końcowego.
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
ms.openlocfilehash: d7e7f7d7c22da007187db5df8bd773dca798597c
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466306"
---
# <a name="overview-of-microsoft-defender-for-endpoint-plan-1"></a>Omówienie Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1

**Dotyczy**

- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Ochrona punktu końcowego w usłudze Microsoft Defender to platforma zabezpieczeń punktów końcowych przedsiębiorstwa zaprojektowana tak, aby pomagać organizacjom, jak Twoja, zapobiegać zaawansowanym zagrożeniam, wykrywać je i badać oraz odpowiadać na nie. Z prosimy o ogłaszanie, że program Defender for Endpoint jest teraz dostępny w dwóch planach: 

- **Defender for Endpoint Plan 1**, described in this article; i 
- **[Program Defender for Endpoint Plan 2, ogólnie](microsoft-defender-endpoint.md)** dostępny i wcześniej znany jako [Defender for Endpoint](microsoft-defender-endpoint.md).

Zielone pola na poniższej ilustracji przedstawiają elementy zawarte w programie Defender for Endpoint Plan 1:

:::image type="content" source="../../media/mde-p1/mde-p1-overview-diagram.png" alt-text="Co jest inculded with Defender for Endpoint Plan 1" lightbox="../../media/mde-p1/mde-p1-overview-diagram.png":::

Skorzystaj z tego przewodnika, aby:

- [Uzyskaj omówienie funkcji dostępnych w programie Defender dla punktu końcowego (plan 1)](#defender-for-endpoint-plan-1-capabilities)
- [Porównanie planu 1 ochrony punktu końcowego w usłudze Defender z planem 2](defender-endpoint-plan-1-2.md)
- [Dowiedz się, jak skonfigurować usługę Defender dla punktu końcowego (plan 1)](mde-p1-setup-configuration.md)
- [Wprowadzenie za pomocą portalu Microsoft 365 Defender, w którym możesz wyświetlać zdarzenia i alerty, zarządzać urządzeniami i korzystać z raportów o wykrytych zagrożeniach](mde-plan1-getting-started.md)
- [Omówienie konserwacji i operacji](mde-p1-maintenance-operations.md)

> [!TIP]
> [Dowiedz się więcej o różnicach między programem Defender dla planu punktu końcowego 1 i planu 2](defender-endpoint-plan-1-2.md).

## <a name="defender-for-endpoint-plan-1-capabilities"></a>Funkcje programu Defender dla punktu końcowego (plan 1)

Program Defender for Endpoint Plan 1 obejmuje następujące funkcje:

- **[Ochrona następnej generacji,](#next-generation-protection)** która zawiera najnowszą w branży, niezawodną ochronę przed złośliwym oprogramowaniem i oprogramowaniem antywirusowym
- **[Ręczne akcje odpowiedzi](#manual-response-actions)**, takie jak wysyłanie pliku do kwarantanny, które zespół zabezpieczeń może podjąć na urządzeniach lub plikach w przypadku wykrycia zagrożeń
- **[Funkcje ograniczania powierzchni ataków](#attack-surface-reduction)** , które urządzenia są w nich dostępne, zapobiegają atakom bezdniowym oraz oferują szczegółową kontrolę nad dostępem do punktów końcowych i zachowaniami.
- **[Scentralizowane konfigurowanie i zarządzanie za](#centralized-management)** pomocą portalu Microsoft 365 Defender i integracji z Microsoft Endpoint Manager
- **[Ochrona na różnych platformach](#cross-platform-support)**, w tym na urządzeniach z systemem Windows, macOS, iOS i Android

Poniższe sekcje zawierają więcej szczegółowych informacji o tych możliwościach. 

## <a name="next-generation-protection"></a>Ochrona nowej generacji

Ochrona następnej generacji obejmuje niezawodną ochronę przed złośliwym oprogramowaniem i oprogramowaniem antywirusowym. Ochrona następnej generacji zapewnia: 

- Ochrona antywirusowa oparta na zachowaniu, heuristic i w czasie rzeczywistym 
- Ochrona dostarczana w chmurze, która obejmuje natychmiastowe wykrywanie i blokowanie nowych i pojawiających się zagrożeń 
- Dedykowana ochrona i aktualizacje produktów, w tym aktualizacje związane z Program antywirusowy Microsoft Defender 

Aby dowiedzieć się więcej, zobacz [Omówienie ochrony następnej generacji](next-generation-protection.md).

## <a name="manual-response-actions"></a>Ręczne akcje odpowiedzi

Ręczne akcje odpowiedzi to akcje, które twój zespół zabezpieczeń może podjąć w przypadku wykrycia zagrożeń w punktach końcowych lub plikach. Program Defender for Endpoint [zawiera pewne akcje](respond-machine-alerts.md) ręcznej odpowiedzi, które można podjąć na urządzeniu, które zostało wykryte jako potencjalnie naruszone lub zawiera podejrzaną zawartość. Możesz również uruchamiać [akcje odpowiedzi dotyczące plików wykrytych](respond-file-alerts.md) jako zagrożenia. W poniższej tabeli podsumowano ręczne akcje dotyczące odpowiedzi dostępne w programie Defender dla punktu końcowego (plan 1). <br/><br/>

| Plik/urządzenie | Akcja | Opis |
|:---|:---|:---|
| Urządzenie | Uruchom skanowanie antywirusowe | Umożliwia rozpoczęcie skanowania antywirusowego. W przypadku wykrycia na urządzeniu jakichkolwiek zagrożeń są one często wykrywane podczas skanowania antywirusowego. |
| Urządzenie | Wyizoluj urządzenie | Odłącza urządzenie od sieci organizacji przy zachowaniu łączności z usługą Defender for Endpoint. Ta akcja umożliwia monitorowanie urządzenia i w razie potrzeby dalsze działanie. |
| Plik | Zatrzymywanie i kwarantanna |Zatrzymuje uruchamianie procesów i kwarantannę skojarzonych plików. |
| Plik | Dodawanie wskaźnika blokowania lub zezwalania na plik | Wskaźniki blokowania uniemożliwiają odczytywanie, redasowane lub wykonywanie przenośnych plików wykonywalnych na urządzeniach. <p>Wskaźniki zezwalaj uniemożliwiają blokowanie lub korygowanie plików. |

Aby dowiedzieć się więcej, zobacz następujące artykuły:

- [Akcje dotyczące odpowiedzi na urządzeniach](respond-machine-alerts.md) 
- [Akcje dotyczące odpowiedzi dotyczące plików](respond-file-alerts.md)

## <a name="attack-surface-reduction"></a>Zmniejszanie obszaru podatnego na ataki

Powierzchnie ataków Twojej organizacji to wszystkie miejsca, w których jest narażona na cyberataki. Za pomocą usługi Defender for Endpoint Plan 1 możesz zmniejszyć liczbę punktów ataków, chroniąc urządzenia i aplikacje używane przez Twoją organizację. Funkcje ograniczania powierzchni ataków zawarte w programie Defender dla planu punktu końcowego 1 opisano w poniższych sekcjach.

- [Reguły zmniejszania obszaru podatnego na ataki](#attack-surface-reduction-rules)
- [Ograniczanie oprogramowania wymuszającego okup](#ransomware-mitigation)
- [Sterowanie urządzeniem](#device-control)
- [Ochrona sieci Web](#web-protection)
- [Ochrona sieci](#web-protection)
- [Zapora sieciowa](#network-firewall)
- [Kontrolka aplikacji](#application-control)

Aby dowiedzieć się więcej o możliwościach zmniejszania powierzchni ataków w programie Defender dla punktu końcowego, zobacz [Omówienie ograniczania powierzchni ataków](overview-attack-surface-reduction.md).

### <a name="attack-surface-reduction-rules"></a>Reguły zmniejszania obszaru podatnego na ataki

Reguły zmniejszania powierzchni ataków mają na celu określone zachowania oprogramowania, które są uznawane za ryzykowne. Do tych zachowań należą:

- Uruchamianie plików wykonywalnych i skryptów próbujących pobrać lub uruchomić inne pliki
- Uruchamianie skryptów zasłoconych lub w inny sposób podejrzanych skryptów
- Inicjowanie zachowań, których aplikacje zwykle nie inicjują podczas normalnej pracy

Wiarygodne aplikacje biznesowe mogą być w sposób zgodny z takim zachowaniem oprogramowania; Takie zachowania są często uznawane za ryzykowne, ponieważ są często wykorzystywane przez atakujących za pośrednictwem złośliwego oprogramowania. Reguły ograniczania powierzchni ataków mogą ograniczać ryzykowne zachowania i pomagać chronić organizację.

Aby dowiedzieć się więcej, zobacz [Stosowanie reguł usuwania powierzchni ataków w celu zapobiegania zainfekowaniu złośliwym oprogramowaniem](attack-surface-reduction.md).

### <a name="ransomware-mitigation"></a>Ograniczanie oprogramowania wymuszającego okup

Kontrolowany dostęp do folderu umożliwia zaradczy przed oprogramowaniem wymuszającym okup. Kontrolowany dostęp do folderu umożliwia tylko zaufanym aplikacjom uzyskiwanie dostępu do chronionych folderów na Twoich punktach końcowych. Aplikacje są dodawane do listy zaufanych aplikacji na podstawie ich reputacji i reputacji. Zespół operacyjny ds. zabezpieczeń może także dodawać lub usuwać aplikacje z listy zaufanych aplikacji.

Aby dowiedzieć się więcej, zobacz [Ochrona ważnych folderów za pomocą kontrolowanego dostępu do folderów](controlled-folders.md).

### <a name="device-control"></a>Sterowanie urządzeniem

Czasami zagrożenia dla urządzeń organizacji występują w postaci plików na dyskach wymiennych, takich jak dyski USB. Program Defender for Endpoint oferuje możliwości zapobiegania nieautoryzowanemu dostępowi do urządzeń peryferyjnych przed zagrożeniami. Możesz skonfigurować usługę Defender for Endpoint, aby blokować lub zezwalać na urządzenia przenośne i pliki na urządzeniach wymiennych. 

Aby dowiedzieć się więcej, zobacz [Sterowanie urządzeniami USB i nośnikami wymiennymi](control-usb-devices-using-intune.md).

### <a name="web-protection"></a>Ochrona sieci Web

Dzięki ochronie sieci Web możesz chronić urządzenia organizacji przed zagrożeniami internetowymi i niepożądaną zawartością. Ochrona sieci Web obejmuje ochronę przed zagrożeniami internetowymi i filtrowanie zawartości sieci Web.

- [Ochrona przed zagrożeniami](web-threat-protection.md) internetowymi zapobiega dostępowi do witryn wyłudzających informacje, wektorów złośliwego oprogramowania, witryn wykorzystujących luki w witrynach, niezaufanych lub o niskiej reputacji oraz witryn, które zostały jawnie zablokowane.
- [Filtrowanie zawartości sieci Web](web-content-filtering.md) uniemożliwia dostęp do określonych witryn na podstawie ich kategorii. Kategorie mogą obejmować m.in. treści dla dorosłych, witryny rozrywki i witryny odpowiedzialności prawnej.

Aby dowiedzieć się więcej, zobacz [Ochrona sieci Web](web-protection-overview.md).

### <a name="network-protection"></a>Ochrona sieci

Dzięki ochronie sieci możesz zapobiec uzyskiwaniu przez Twoją organizację dostępu do niebezpiecznych domen, które mogą czynami wyłudzania informacji, oszustwami i złośliwą zawartością w Internecie. 

Aby dowiedzieć się więcej, zobacz [Ochrona sieci](network-protection.md).

### <a name="network-firewall"></a>Zapora sieciowa

Dzięki ochronie zapory sieciowej możesz ustawić reguły, które określają, jaki ruch sieciowy może przepływać do lub z urządzeń organizacji. Dzięki zaporze sieciowej i zaawansowanym zabezpieczeniam, które można uzyskać za pomocą programu Defender for Endpoint, możesz:

- Zmniejszanie ryzyka wystąpienia zagrożeń bezpieczeństwa sieci
- Zabezpieczanie poufnych danych i własności intelektualnej
- Przedłuż inwestycję w bezpieczeństwo

Aby dowiedzieć się więcej, zobacz [Windows Defender z zaawansowanymi zabezpieczeniami](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security).

### <a name="application-control"></a>Kontrolka aplikacji

Kontrolka aplikacji chroni punkty Windows, uruchamiając tylko zaufane aplikacje i kod w podstawowym systemie (kernel). Zespół zabezpieczeń może zdefiniować reguły kontroli aplikacji uwzględniające atrybuty aplikacji, takie jak współtworowanie certyfikatów, reputacja, proces uruchamiania i nie tylko. Kontrolka aplikacji jest dostępna w Windows 10 lub nowszym.

Aby dowiedzieć się więcej, zobacz [Kontrolka aplikacji dla Windows](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control).

## <a name="centralized-management"></a>Scentralizowane zarządzanie

Program Defender for Endpoint Plan 1 obejmuje portal Microsoft 365 Defender, który umożliwia Twojemu zespołowi zabezpieczeń przeglądanie aktualnych informacji o wykrytych zagrożeniach, podjąć odpowiednie działania w celu ograniczenia zagrożeń oraz centralnie zarządzać ustawieniami ochrony przed zagrożeniami w Twojej organizacji.

Aby dowiedzieć się więcej, [zobacz Microsoft 365 Defender przegląd portalu](portal-overview.md).

### <a name="role-based-access-control"></a>Kontrola dostępu oparta na rolach

Za pomocą kontroli dostępu opartej na rolach administrator zabezpieczeń może tworzyć role i grupy w celu udzielenia odpowiedniego dostępu do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Dzięki RBAC masz pełną kontrolę nad tym, kto ma dostęp do Defender dla Chmury dostępu oraz co mogą oni widzieć i robić. 

Aby dowiedzieć się więcej, zobacz [Zarządzanie dostępem do portalu za pomocą kontroli dostępu opartej na rolach](rbac.md).

### <a name="reporting"></a>Raportowanie

Portal Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) zapewnia łatwy dostęp do informacji o wykrytych zagrożeniach i działaniach w celu ich rozwiązania. 

- Strona **główna** zawiera karty do szybkich pokazania, którzy użytkownicy lub urządzenia są zagrożenia, ilu zagrożeń zostało wykrytych oraz jakie alerty/zdarzenia zostały utworzone.
- Sekcja **Alerty & zawiera** listę zdarzeń utworzonych w wyniku wyzwolenia alertów. Alerty i zdarzenia są generowane w przypadku wykrycia zagrożeń na różnych urządzeniach.
- Centrum **akcji zawiera** listę działań naprawczych, które zostały wykonane. Jeśli na przykład plik zostanie wysłany do kwarantanny lub adres URL zostanie zablokowany, każda akcja będzie wymieniona w Centrum akcji na **karcie** Historia.
- Sekcja **Raporty** zawiera raporty, w których są wyświetlane informacje o wykrytych zagrożeniach i o ich stanie. 

Aby dowiedzieć się więcej, [zobacz Wprowadzenie z Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](mde-plan1-getting-started.md).

### <a name="apis"></a>Interfejsy API

Za pomocą interfejsów API usługi Defender for Endpoint możesz zautomatyzować przepływy pracy i zintegrować je z niestandardowymi rozwiązaniami Twojej organizacji. 

Aby dowiedzieć się więcej, zobacz [Defender for Endpoint API (Interfejsy API punktu końcowego](management-apis.md)). 

## <a name="cross-platform-support"></a>Obsługa międzyplatformowa

Większość organizacji używa różnych urządzeń i systemów operacyjnych. Obecnie program Defender for Endpoint Plan 1 obsługuje następujące systemy operacyjne:

- Windows 7 (wymagany ESU)
- Windows 8.1
- Windows 10, wersja 1709 lub nowsza
- macOS: 11.5 (Big Sur), 10.15.7 (Catalina) lub 10.14.6 (Mojave)
- iOS
- System operacyjny Android

## <a name="next-steps"></a>Następne kroki

- [Porównanie Ochrona punktu końcowego w usłudze Microsoft Defender plan 1 z planem 2](defender-endpoint-plan-1-2.md)
- [Instalowanie i konfigurowanie ochrony punktu końcowego w usłudze Defender (plan 1)](mde-p1-setup-configuration.md)
- [Wprowadzenie z programem Defender dla punktu końcowego (plan 1)](mde-plan1-getting-started.md)
- [Zarządzanie programem Defender dla punktu końcowego (plan 1)](mde-p1-maintenance-operations.md)
