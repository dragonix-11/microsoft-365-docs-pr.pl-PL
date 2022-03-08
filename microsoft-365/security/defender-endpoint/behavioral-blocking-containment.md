---
title: Blokowanie i blokowanie zachowań
description: Dowiedz się więcej o możliwościach blokowania i blokowania zachowania w programie Microsoft Defender dla punktu końcowego
keywords: Program Microsoft Defender dla punktu końcowego, EDR w trybie blokowania, blokowanie w trybie pasywnym
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.localizationpriority: medium
ms.custom:
- next-gen
- edr
- admindeeplinkDEFENDER
ms.collection: m365-security-compliance
ms.technology: mde
ms.openlocfilehash: bab766fd69b9227f10ba897040faff79e65b1722
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63325785"
---
# <a name="behavioral-blocking-and-containment"></a>Blokowanie i blokowanie zachowań

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>Omówienie

W dzisiejszych czasach zagrożenie jest przekroczenie [](/windows/security/threat-protection/intelligence/fileless-threats) przez złośliwe oprogramowanie bez plików, które znajduje się na tej ziemi, wysoce wielomorphiczne zagrożenia, które mnożyć szybciej niż tradycyjne rozwiązania, oraz ataki obsługiwane przez człowieka, które dostosowują się do tego, co mogą znaleźć adwersiści na naruszonych urządzeniach. Tradycyjne rozwiązania zabezpieczeń nie są wystarczające do zatrzymania takich ataków. potrzebujesz sztucznej inteligencji i funkcji do nauki urządzeń (ML) z możliwościami, takimi jak blokowanie zachowań i zawieranie, zawarte w programie [Defender for Endpoint](/windows/security).

Możliwości blokowania i blokowania zachowań mogą ułatwić identyfikowanie i zatrzymywanie zagrożeń na podstawie ich zachowań i drzew procesowych, nawet gdy zagrożenie rozpoczęło się. Składniki i funkcje ochrony następnej generacji, programu EDR i usługi Defender for Endpoint współpracują ze sobą w zakresie możliwości blokowania i blokowania zachowań.

:::image type="content" source="images/mdatp-next-gen-EDR-behavblockcontain.png" alt-text="Blokowanie i blokowanie zachowań.":::

Możliwości blokowania i blokowania zachowań działają z wieloma składnikami i funkcjami usługi Defender for Endpoint, aby natychmiast przerywać ataki i zapobiec postępowi ataków.

- [Ochrona następnej generacji](microsoft-defender-antivirus-in-windows-10.md) (która obejmuje Program antywirusowy Microsoft Defender) może wykrywać zagrożenia przez analizowanie zachowań i zatrzymywać uruchomione zagrożenia.

- [Wykrywanie punktu końcowego i](overview-endpoint-detection-response.md) odpowiedź (EDR) odbiera sygnały zabezpieczeń w Twojej sieci, urządzeniach i zachowaniu kernelu. W przypadku wykrycia zagrożeń są tworzone alerty. Wiele alertów tego samego typu jest agregowane w zdarzenia, co ułatwia zespołowi ds. zabezpieczeń badanie i odpowiadanie na nie.

- [Program Defender for Endpoint](overview-endpoint-detection-response.md) ma szeroką gamę sterowników tożsamości, poczty e-mail, danych i aplikacji, a także sygnały zachowania sieci, punktu końcowego i kernelu odbieranych za pośrednictwem EDR. Składnik programu [Microsoft 365 Defender](../defender/microsoft-365-defender.md), procesów programu Defender for Endpoint i skoreluje te sygnały, podnosi alerty wykrywania i łączy powiązane alerty w zdarzeniach.

Dzięki tym możliwościom można zapobiegać lub blokować więcej zagrożeń, nawet jeśli zaczną one działać. W przypadku wykrycia podejrzanych zachowań zagrożenia są zawarte, tworzone są alerty i zagrożenia są zatrzymywane na ich torze.

Na poniższej ilustracji przedstawiono przykładowy alert wyzwolony przez funkcje blokowania zachowania i blokowania:

:::image type="content" alt-text="Przykład alertu w przypadku blokowania i blokowania zachowania." source="images/blocked-behav-alert.png" lightbox="images/blocked-behav-alert.png":::

## <a name="components-of-behavioral-blocking-and-containment"></a>Składniki blokowania i blokowania zachowania

- **Reguły ograniczania powierzchni ataków oparte na klientach oparte na [zasadach](attack-surface-reduction.md)** Zgodnie z regułami ograniczania powierzchni ataków wstępnie typowe zachowania ataków nie mogą być wykonywane. Gdy takie zachowania próbują wykonać, są one widoczne w programie <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender jako</a> alerty informacyjne. Reguły zmniejszania powierzchni ataków nie są domyślnie włączone. zasady konfigurujesz w portalu [Microsoft 365 Defender sieci.](/microsoft-365/security/defender/microsoft-365-defender)

- **[Blokowanie zachowania klienta](client-behavioral-blocking.md)** Zagrożenia dotyczące punktów końcowych są wykrywane za pośrednictwem uczenia maszynowego, a następnie blokowane i usuwane automatycznie. (Blokowanie zachowania klienta jest domyślnie włączone).

- **[Blokowanie pętli opinii](feedback-loop-blocking.md)** (nazywane również szybką ochroną) Wykrywanie zagrożeń jest obserwowane za pośrednictwem analizy zachowania. Zagrożenia są zatrzymywane i nie można ich uruchamiać dla innych punktów końcowych. (Blokowanie pętli opinii jest domyślnie włączone).

- **[Wykrywanie punktu końcowego i odpowiedź (EDR)](edr-in-block-mode.md)** w trybie blokowania Złośliwe artefakty lub zachowania obserwowane w ramach ochrony po naruszeniu zabezpieczeń są blokowane i blokowane. EDR trybie blokowania działa nawet Program antywirusowy Microsoft Defender nie jest podstawowym rozwiązaniem antywirusowym. (EDR w trybie blokowania nie jest domyślnie włączone; ta funkcja jest włączona w programie Microsoft 365 Defender).

Spodziewaj się większej liczby obszarów blokowania i blokowania zachowań, ponieważ firma Microsoft stale ulepsza funkcje i możliwości ochrony przed zagrożeniami. Aby dowiedzieć się, co jest zaplanowane i które jest obecnie planowane, odwiedź Microsoft 365 [przewodnik po programie](https://www.microsoft.com/microsoft-365/roadmap).

## <a name="examples-of-behavioral-blocking-and-containment-in-action"></a>Przykłady blokowania zachowania i blokowania w działaniu

Możliwości blokowania i blokowania zachowań zablokowały techniki atakujących, takie jak:

- Credential aby uwierzytelnić z LSASS
- Inicjał procesu krzyżowego
- Wydrukianie procesu
- Obejście kontroli konta użytkownika
- Manipulowanie oprogramowaniem antywirusowym (na przykład jego wyłączenie lub dodanie złośliwego oprogramowania jako wykluczenia)
- Skontaktowanie się z poleceniami i kontrolkami (C&C) w celu pobrania ładów
- Wyszukiwanie monet
- Modyfikacja rekordu rozruchu
- Ataki typu "pass-the-hash"
- Instalacja certyfikatu głównego
- Próba wykorzystania różnych luk

Poniżej przedstawiono dwa przykłady blokowania zachowań i blokowania w działaniu w rzeczywistych życiach.

### <a name="example-1-credential-theft-attack-against-100-organizations"></a>Przykład 1. Ataki kradzieży poświadczeń względem 100 organizacji

Zgodnie z opisem w hot pochwał dla nieuchwytnych zagrożeń: Blokowanie oparte na zachowaniu oparte na [AI](https://www.microsoft.com/security/blog/2019/10/08/in-hot-pursuit-of-elusive-threats-ai-driven-behavior-based-blocking-stops-attacks-in-their-tracks) zatrzymuje na ich torze ataki kradzieży poświadczeń wobec 100 organizacji na całym świecie zostały zatrzymane przez funkcje blokowania zachowań i blokowania treści. Wiadomości e-mail służące do wyłudzania informacji, które zawierały dokument w celach docelowych. Jeśli adresat otworzył załącznik, powiązany dokument zdalny mógł wykonać kod na urządzeniu użytkownika i załadować złośliwe oprogramowanie Lokibot, które ukradziło poświadczenia, zfiltrował skradzione dane i czekało na dalsze instrukcje z serwera poleceń i kontrolek.

Modele nauki dotyczące urządzeń oparte na zachowaniu w programie Defender dla punktu końcowego, w których zatrzymano i zatrzymano techniki atakującego w dwóch punktach łańcucha ataków:

- Pierwsza warstwa ochrony wykryła exploit behavior. Klasyfikatory uczenia urządzeń w chmurze prawidłowo zidentyfikowały zagrożenie, tak jak i natychmiast poinstruowały urządzenie klienckie, aby zablokowało atak.
- Druga warstwa ochrony, która pomagała zatrzymać przypadki, w których atak został przerwany przez pierwszą warstwę, wykrył proces zawężony, zatrzymał ten proces i usunął odpowiadające im pliki (na przykład Lokibot).

Podczas wykrycia i zatrzymania ataków, alerty, takie jak "alert dostępu początkowego", zostały wyzwolone i pojawiły się w Microsoft 365 Defender [portalu](/microsoft-365/security/defender/microsoft-365-defender).

:::image type="content" source="images/behavblockcontain-initialaccessalert.png" alt-text="Alert dostępu początkowego w portalu Microsoft 365 Defender sieci.":::

W tym przykładzie pokazano, jak modele nauki urządzeń oparte na zachowaniu w chmurze dodają nowe warstwy ochrony przed atakami nawet po ich uruchomieniu.

### <a name="example-2-ntlm-relay---juicy-potato-malware-variant"></a>Przykład 2. Przekazywanie NTLM — wariant złośliwego oprogramowania z kartofelami

Jak opisano w ostatnim wpisie w blogu Blokowanie i blokowanie zachowania [:](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection) Przekształcanie sterowników w ochronę, w styczniu 2020 r. program Defender for Endpoint wykrył aktywność eskalacji uprawnień na urządzeniu w organizacji. Wyzwolono alert o nazwie "Możliwa eskalacja uprawnień przy użyciu przekazywania NTLM".

:::image type="content" alt-text="Alert NTLM o złośliwym oprogramowaniu do kartofelka." source="images/NTLMalertjuicypotato.png" lightbox="images/NTLMalertjuicypotato.png":::

Zagrożenie było złośliwym oprogramowaniem; było to nowe, widoczne przedtem wariant notornego narzędzia hackingowego o nazwie Togo kartofel, które jest używane przez atakujących do uzyskania eskalacji uprawnień na urządzeniu.

W minutach po wyzwoleniu alertu plik został przeanalizowany i potwierdzony jako złośliwy. Proces ten został zatrzymany i zablokowany, jak pokazano na poniższej ilustracji:

:::image type="content" alt-text="Artefakt zablokowany." source="images/Artifactblockedjuicypotato.png" lightbox="images/Artifactblockedjuicypotato.png":::

Kilka minut po zablokowaniu artefaktu na tym samym urządzeniu zablokowano wiele wystąpień tego samego pliku, uniemożliwiając wdrożenie na urządzeniu więcej atakujących lub innego złośliwego oprogramowania.

W tym przykładzie pokazano, że w przypadku funkcji blokowania zachowania i blokowania treści zagrożenia są wykrywane, blokowane i automatycznie blokowane.

## <a name="next-steps"></a>Następne kroki

- [Dowiedz się więcej o programie Defender dla punktu końcowego](overview-endpoint-detection-response.md)

- [Konfigurowanie reguł ograniczania powierzchni ataków](attack-surface-reduction.md)

- [Włączanie EDR w trybie blokowania](edr-in-block-mode.md)

- [Zobacz ostatnią aktywność globalną na temat zagrożeń](https://www.microsoft.com/wdsi/threats)

- [Omówienie funkcji Microsoft 365 Defender](../defender/microsoft-365-defender.md)
