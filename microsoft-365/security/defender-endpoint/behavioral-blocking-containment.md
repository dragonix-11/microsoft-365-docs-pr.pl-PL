---
title: Blokowanie i ograniczanie behawioralne
description: Dowiedz się więcej o możliwościach blokowania i powstrzymywania zachowań w Ochrona punktu końcowego w usłudze Microsoft Defender
keywords: Ochrona punktu końcowego w usłudze Microsoft Defender, EDR w trybie bloku, blokowanie trybu pasywnego
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
ms.openlocfilehash: 1f598fd1463b6e08c73d7db9ac6d1540a51d6841
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790619"
---
# <a name="behavioral-blocking-and-containment"></a>Blokowanie i ograniczanie behawioralne

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

> Chcesz poznać usługę Defender for Endpoint? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>Omówienie

Dzisiejszy krajobraz zagrożeń jest opanowany przez [złośliwe oprogramowanie bez plików](/windows/security/threat-protection/intelligence/fileless-threats) i które żyje poza ziemią, wysoce polimorficzne zagrożenia, które mutują szybciej niż tradycyjne rozwiązania, mogą nadążyć za atakami obsługiwanymi przez człowieka, które dostosowują się do tego, co przeciwnicy znajdują na zagrożonych urządzeniach. Tradycyjne rozwiązania zabezpieczeń nie są wystarczające do powstrzymania takich ataków; Potrzebne są możliwości wspierane przez sztuczną inteligencję (AI) i uczenie urządzeń (ML), takie jak blokowanie i powstrzymywanie zachowań, zawarte w [usłudze Defender for Endpoint](/windows/security).

Funkcje blokowania i powstrzymywania zachowań mogą pomóc w identyfikowaniu i zatrzymywaniu zagrożeń na podstawie ich zachowań i przetwarzania drzew nawet wtedy, gdy zagrożenie rozpoczęło wykonywanie. Funkcje i składniki i funkcje usługi Defender for Endpoint nowej generacj EDR i współpracują ze sobą w zakresie blokowania i powstrzymywania zachowań.

:::image type="content" source="images/mdatp-next-gen-EDR-behavblockcontain.png" alt-text="Blokowanie i powstrzymywanie zachowań w portalu usługi Microsoft Defender ATP" lightbox="images/mdatp-next-gen-EDR-behavblockcontain.png":::

Funkcje blokowania behawioralnego i powstrzymywania działają z wieloma składnikami i funkcjami usługi Defender for Endpoint, aby natychmiast zatrzymać ataki i zapobiec postępowi ataków.

- [Ochrona nowej generacji](microsoft-defender-antivirus-in-windows-10.md) (w tym Program antywirusowy Microsoft Defender) może wykrywać zagrożenia, analizując zachowania i zatrzymując zagrożenia, które zaczęły działać.

- [Wykrywanie i reagowanie na punkty końcowe](overview-endpoint-detection-response.md) (EDR) odbiera sygnały zabezpieczeń w sieci, urządzeniach i zachowaniu jądra. W miarę wykrywania zagrożeń tworzone są alerty. Wiele alertów tego samego typu jest agregowanych w zdarzenia, co ułatwia zespołowi ds. operacji zabezpieczeń badanie i reagowanie.

- [Usługa Defender for Endpoint](overview-endpoint-detection-response.md) ma szeroką gamę optyk w różnych tożsamościach, wiadomościach e-mail, danych i aplikacjach, a także sygnały dotyczące zachowania sieci, punktu końcowego i jądra odbierane za pośrednictwem EDR. Składnik [Microsoft 365 Defender](../defender/microsoft-365-defender.md), usługa Defender for Endpoint przetwarza i koreluje te sygnały, zgłasza alerty wykrywania i łączy powiązane alerty w zdarzeniach.

Dzięki tym możliwościom można zapobiec lub zablokować więcej zagrożeń, nawet jeśli zaczną one działać. Za każdym razem, gdy zostanie wykryte podejrzane zachowanie, zagrożenie zostanie ograniczone, alerty zostaną utworzone, a zagrożenia zostaną zatrzymane w ich śladach.

Na poniższej ilustracji przedstawiono przykład alertu, który został wyzwolony przez funkcję blokowania i powstrzymywania zachowań:

:::image type="content" source="images/blocked-behav-alert.png" alt-text="Strona Alerty z alertem poprzez blokowanie i hermetyzację zachowań" lightbox="images/blocked-behav-alert.png":::

## <a name="components-of-behavioral-blocking-and-containment"></a>Składniki blokowania behawioralnego i hermetyzowania

- **[Reguły zmniejszania obszaru ataków](attack-surface-reduction.md) na kliencie oparte na zasadach** Wstępnie zdefiniowane typowe zachowania związane z atakiem nie mogą być wykonywane zgodnie z regułami zmniejszania obszaru ataków. Gdy takie zachowania próbują zostać wykonane, można je zobaczyć w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> jako alerty informacyjne. Reguły zmniejszania obszaru ataków nie są domyślnie włączone; zasady można skonfigurować w [portalu Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender).

- **[Blokowanie zachowania klienta](client-behavioral-blocking.md)** Zagrożenia w punktach końcowych są wykrywane za pośrednictwem uczenia maszynowego, a następnie są automatycznie blokowane i korygowane. (Blokowanie zachowania klienta jest domyślnie włączone).

- **[Blokowanie pętli sprzężenia zwrotnego](feedback-loop-blocking.md)** (nazywane również szybką ochroną) Wykrywanie zagrożeń jest obserwowane za pośrednictwem analizy behawioralnej. Zagrożenia są zatrzymywane i nie mogą działać w innych punktach końcowych. (Blokowanie pętli opinii jest domyślnie włączone).

- **[Wykrywanie i reagowanie na punkty końcowe (EDR) w trybie bloku](edr-in-block-mode.md)** Złośliwe artefakty lub zachowania obserwowane przez ochronę po naruszeniu zabezpieczeń są blokowane i zawarte. EDR w trybie bloku działa, nawet jeśli Program antywirusowy Microsoft Defender nie jest podstawowym rozwiązaniem antywirusowym. (EDR w trybie bloku nie jest domyślnie włączona; włączasz ją w Microsoft 365 Defender).

Spodziewaj się więcej w obszarze blokowania i powstrzymywania zachowań, ponieważ firma Microsoft nadal ulepsza funkcje i możliwości ochrony przed zagrożeniami. Aby zobaczyć, co jest planowane i wdrażane teraz, odwiedź [Microsoft 365 harmonogram](https://www.microsoft.com/microsoft-365/roadmap).

## <a name="examples-of-behavioral-blocking-and-containment-in-action"></a>Przykłady blokowania i powstrzymywania zachowań w działaniu

Funkcje blokowania i powstrzymywania zachowań zablokowały techniki atakujące, takie jak:

- Dumping poświadczeń z LSASS
- Wstrzykiwanie krzyżowe
- Wydrążanie procesów
- Obejście kontroli konta użytkownika
- Manipulowanie programem antywirusowym (na przykład wyłączanie go lub dodawanie złośliwego oprogramowania jako wykluczenia)
- Kontaktowanie się z poleceniem i kontrolą (C&C) w celu pobrania ładunków
- Wydobywanie monet
- Modyfikacja rekordu rozruchowego
- Ataki typu pass-the-hash
- Instalacja certyfikatu głównego
- Próba wykorzystania różnych luk w zabezpieczeniach

Poniżej przedstawiono dwa rzeczywiste przykłady blokowania i powstrzymywania zachowań w działaniu.

### <a name="example-1-credential-theft-attack-against-100-organizations"></a>Przykład 1: Atak kradzieży poświadczeń na 100 organizacji

Jak opisano w artykule [W pogoni za nieuchwytnymi zagrożeniami: blokowanie oparte na zachowaniu oparte na sztucznej inteligencji zatrzymuje ataki na swoich torach](https://www.microsoft.com/security/blog/2019/10/08/in-hot-pursuit-of-elusive-threats-ai-driven-behavior-based-blocking-stops-attacks-in-their-tracks), atak kradzieży poświadczeń na 100 organizacji na całym świecie został zatrzymany przez blokowanie zachowań i możliwości powstrzymywania. Wiadomości e-mail z wyłudzaniem informacji, które zawierały dokument przynęty, zostały wysłane do organizacji docelowych. Jeśli odbiorca otworzył załącznik, powiązany dokument zdalny był w stanie wykonać kod na urządzeniu użytkownika i załadować złośliwe oprogramowanie Lokibot, które ukradło poświadczenia, eksfiltrowane skradzione dane i czekało na dalsze instrukcje z serwera poleceń i kontroli.

Oparte na zachowaniu modele uczenia urządzeń w usłudze Defender for Endpoint złapały i zatrzymały techniki atakującego w dwóch punktach łańcucha ataków:

- Pierwsza warstwa ochrony wykryła zachowanie luki w zabezpieczeniach. Klasyfikatory uczenia urządzeń w chmurze prawidłowo zidentyfikowały zagrożenie jako i natychmiast poinstruowały urządzenie klienckie, aby zablokowało atak.
- Druga warstwa ochrony, która pomogła zatrzymać przypadki, w których atak przeszedł obok pierwszej warstwy, wykryła wydrążenie procesu, zatrzymała ten proces i usunęła odpowiednie pliki (takie jak Lokibot).

Gdy atak został wykryty i zatrzymany, alerty, takie jak "początkowy alert dostępu", zostały wyzwolone i wyświetlone w [portalu Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender).

:::image type="content" source="images/behavblockcontain-initialaccessalert.png" alt-text="Alert dostępu początkowego w portalu Microsoft 365 Defender" lightbox="images/behavblockcontain-initialaccessalert.png":::

W tym przykładzie pokazano, jak oparte na zachowaniu modele uczenia urządzeń w chmurze dodają nowe warstwy ochrony przed atakami, nawet po rozpoczęciu działania.

### <a name="example-2-ntlm-relay---juicy-potato-malware-variant"></a>Przykład 2: Przekaźnik NTLM — wariant złośliwego oprogramowania Juicy Potato

Jak opisano w ostatnim wpisie w blogu [, blokowanie i powstrzymywanie zachowań: przekształcanie optyki w ochronę](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection), w styczniu 2020 r. usługa Defender for Endpoint wykryła działanie eskalacji uprawnień na urządzeniu w organizacji. Wyzwolono alert o nazwie "Możliwa eskalacja uprawnień przy użyciu przekaźnika NTLM".

:::image type="content" source="images/NTLMalertjuicypotato.png" alt-text="Alert NTLM dotyczący złośliwego oprogramowania Juicy Potato" lightbox="images/NTLMalertjuicypotato.png":::

Zagrożeniem okazało się złośliwe oprogramowanie. Był to nowy, niewyjaśniany wcześniej wariant znanego narzędzia hakerskiego o nazwie Juicy Potato, które jest używane przez atakujących do uzyskania eskalacji uprawnień na urządzeniu.

Kilka minut po wyzwoleniu alertu plik został przeanalizowany i potwierdzony jako złośliwy. Proces został zatrzymany i zablokowany, jak pokazano na poniższej ilustracji:

:::image type="content" source="images/Artifactblockedjuicypotato.png" alt-text="Artefakt zablokowany"  lightbox="images/Artifactblockedjuicypotato.png":::

Kilka minut po zablokowaniu artefaktu wiele wystąpień tego samego pliku zostało zablokowanych na tym samym urządzeniu, co uniemożliwia wdrażanie większej liczby osób atakujących lub innego złośliwego oprogramowania na urządzeniu.

W tym przykładzie pokazano, że dzięki możliwościom blokowania i powstrzymywania zachowań zagrożenia są wykrywane, zawarte i blokowane automatycznie.

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)

## <a name="next-steps"></a>Następne kroki

- [Dowiedz się więcej o usłudze Defender for Endpoint](overview-endpoint-detection-response.md)

- [Konfigurowanie reguł zmniejszania obszaru ataków](attack-surface-reduction.md)

- [Włączanie EDR w trybie bloku](edr-in-block-mode.md)

- [Zobacz ostatnie globalne działanie dotyczące zagrożeń](https://www.microsoft.com/wdsi/threats)

- [Omówienie Microsoft 365 Defender](../defender/microsoft-365-defender.md)
