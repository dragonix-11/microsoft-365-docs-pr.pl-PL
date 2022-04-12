---
title: Dlaczego ochrona w chmurze powinna być włączona dla Program antywirusowy Microsoft Defender
description: Zobacz, dlaczego ochrona w chmurze powinna być włączona dla Program antywirusowy Microsoft Defender. Ułatwia to działanie wielu funkcji zabezpieczeń w Ochrona punktu końcowego w usłudze Microsoft Defender
keywords: Program antywirusowy Microsoft Defender, ochrona w chmurze, funkcje zabezpieczeń, przykładowe przesyłanie
search.product: ''
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.date: 10/22/2021
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 6a0667e52474fe5e04f547d12b1f53ca47c6ea6e
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787583"
---
# <a name="why-cloud-protection-should-be-enabled-for-microsoft-defender-antivirus"></a>Dlaczego ochrona w chmurze powinna być włączona dla Program antywirusowy Microsoft Defender

**Dotyczy:**

- Program antywirusowy Microsoft Defender
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

**Platformy**
- System Windows

Program antywirusowy Microsoft Defender ochrona w chmurze pomaga chronić przed złośliwym oprogramowaniem w punktach końcowych i w sieci. Zalecamy włączenie ochrony w chmurze, ponieważ niektóre funkcje zabezpieczeń i funkcje w Ochrona punktu końcowego w usłudze Microsoft Defender działają tylko po włączeniu ochrony w chmurze. 

[![alt-text="Diagram przedstawiający elementy, które zależą od ochrony chmury](images/mde-cloud-protection.png#lightbox)](enable-cloud-protection-microsoft-defender-antivirus.md)

Poniższa tabela zawiera podsumowanie funkcji i możliwości, które zależą od ochrony w chmurze: <br/><br/>

| Funkcja/możliwość  | Wymaganie subskrypcji |  Opis  |
|---------|---------|--------|
| Sprawdzanie metadanych w chmurze  | Ochrona punktu końcowego w usłudze Microsoft Defender plan 1 lub plan 2 (autonomiczny lub uwzględniony w planie, takim jak Microsoft 365 E3 lub E5) | Usługa Program antywirusowy Microsoft Defender w chmurze używa modeli uczenia maszynowego jako dodatkowej warstwy obrony. Te modele uczenia maszynowego obejmują metadane, więc po wykryciu podejrzanego lub złośliwego pliku jego metadane są sprawdzane. <br/><br/>Aby dowiedzieć się więcej, zobacz [Blog: Poznaj zaawansowane technologie w centrum Ochrona punktu końcowego w usłudze Microsoft Defender ochrony nowej generacji](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/)  |
| Ochrona w chmurze i przesyłanie próbek | Ochrona punktu końcowego w usłudze Microsoft Defender plan 1 lub plan 2 (autonomiczny lub uwzględniony w planie, takim jak Microsoft 365 E3 lub E5) | Pliki i pliki wykonywalne mogą być wysyłane do usługi w chmurze Program antywirusowy Microsoft Defender w celu detonacji i analizy. <br/><br/>Aby dowiedzieć się więcej, zobacz [Ochrona w chmurze i przykładowe przesyłanie w Program antywirusowy Microsoft Defender](cloud-protection-microsoft-antivirus-sample-submission.md).<br/><br/>**UWAGA**: Automatyczne przesyłanie przykładów opiera się na ochronie chmury, chociaż można ją również skonfigurować jako ustawienie autonomiczne.         |
| Ochrona przed naruszeniami | Ochrona punktu końcowego w usłudze Microsoft Defender plan 2 (autonomiczny lub uwzględniony w planie, takim jak Microsoft 365 E5) | Ochrona przed naruszeniami pomaga chronić przed niepożądanymi zmianami ustawień zabezpieczeń organizacji. Aby wymusić ochronę przed naruszeniami w portalu Microsoft 365 Defender, należy włączyć ochronę w chmurze. <br/><br/>Aby dowiedzieć się więcej, zobacz [Ochrona ustawień zabezpieczeń za pomocą ochrony przed naruszeniami](prevent-changes-to-security-settings-with-tamper-protection.md).        |
| Blokuj od pierwszego wejrzenia | Ochrona punktu końcowego w usłudze Microsoft Defender plan 1 lub plan 2 (autonomiczny lub uwzględniony w planie, takim jak Microsoft 365 E3 lub E5) | Pozycja Blokuj od pierwszego wejrzenia wykrywa nowe złośliwe oprogramowanie i blokuje go w ciągu kilku sekund. Po wykryciu podejrzanego lub złośliwego pliku zablokuj możliwości od pierwszego wejrzenia, prześlij zapytania do zaplecza ochrony chmury i zastosuje algorytm heurystykę, uczenie maszynowe i zautomatyzowaną analizę pliku, aby ustalić, czy jest to zagrożenie.<br/><br/>Aby dowiedzieć się więcej, zobacz [Co to jest "blokuj od pierwszego wejrzenia"?](configure-block-at-first-sight-microsoft-defender-antivirus.md#what-is-block-at-first-sight)   |
| Aktualizacje sygnatur awaryjnych | Ochrona punktu końcowego w usłudze Microsoft Defender plan 2 (autonomiczny lub uwzględniony w planie, takim jak Microsoft 365 E5) | Po wykryciu złośliwej zawartości są wdrażane aktualizacje i poprawki sygnatur awaryjnych. Zamiast czekać na następną regularną aktualizację, możesz otrzymać te poprawki i aktualizacje w ciągu kilku minut.   |
| Wykrywanie i reagowanie na punkty końcowe (EDR) w trybie bloku | Ochrona punktu końcowego w usłudze Microsoft Defender plan 2 (autonomiczny lub uwzględniony w planie, takim jak Microsoft 365 E5) | EDR w trybie bloku zapewnia dodatkową ochronę, gdy Program antywirusowy Microsoft Defender nie jest podstawowym produktem antywirusowym na urządzeniu. EDR w trybie bloku koryguje artefakty znalezione podczas skanowania wygenerowanego przez EDR, które mogło zostać pominięte przez podstawowe rozwiązanie antywirusowe spoza firmy Microsoft. Po włączeniu dla urządzeń z Program antywirusowy Microsoft Defender jako podstawowym rozwiązaniem antywirusowym EDR w trybie bloku zapewnia dodatkową korzyść automatycznego korygowania artefaktów zidentyfikowanych podczas skanowania wygenerowanego EDR. <br/><br/>Aby dowiedzieć się więcej, zobacz [EDR w trybie bloku](edr-in-block-mode.md).|
| Reguły zmniejszania obszaru podatnego na ataki | Ochrona punktu końcowego w usłudze Microsoft Defender plan 1 lub plan 2 (autonomiczny lub uwzględniony w planie, takim jak Microsoft 365 E3 lub E5) | Zmniejszenie obszaru podatnego na ataki polega na zmniejszeniu liczby miejsc i sposobów narażenia punktów końcowych organizacji na cyberataki. Reguły zmniejszania obszaru ataków to inteligentne reguły, które można skonfigurować w celu powstrzymania złośliwego oprogramowania. Niektóre reguły wymagają włączenia ochrony w chmurze w celu pełnego działania. Te reguły obejmują: <br/>— Blokuj uruchamianie plików wykonywalnych, chyba że spełniają kryteria występowania, wieku lub listy zaufanych <br/>— Korzystanie z zaawansowanej ochrony przed oprogramowaniem wymuszającym okup <br/>— Blokowanie uruchamiania niezaufanych programów z dysków wymiennych <br/><br/>Aby dowiedzieć się więcej, zobacz [Używanie reguł zmniejszania obszaru ataków w celu zapobiegania infekcji złośliwym oprogramowaniem](attack-surface-reduction.md).  |
| Wskaźniki kompromisu (IoCs) | Ochrona punktu końcowego w usłudze Microsoft Defender plan 2 (autonomiczny lub uwzględniony w planie, takim jak Microsoft 365 E5) | Kontrolery IoCs w usłudze Defender dla punktu końcowego można skonfigurować do definiowania wykrywania, zapobiegania i wykluczania jednostek. Na przykład wskaźniki "zezwalaj" mogą służyć do definiowania wyjątków Program antywirusowy Microsoft Defender skanów i akcji korygowania w usłudze Defender for Endpoint. W innym przykładzie wskaźniki "alertów i bloków" mogą służyć do zapobiegania wykonywaniu plików lub procesów oraz do śledzenia tych działań za pomocą alertów, które można wyświetlać w portalu Microsoft 365 Defender. <br/><br/>Aby dowiedzieć się więcej, zobacz [Tworzenie wskaźników](manage-indicators.md).    |

> [!TIP]
> Aby dowiedzieć się więcej na temat planów usługi Defender for Endpoint, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1 i Plan 2](defender-endpoint-plan-1-2.md).

## <a name="next-steps"></a>Następne kroki

Teraz, gdy masz omówienie ochrony w chmurze i jej roli w Program antywirusowy Microsoft Defender, oto kilka następnych kroków:

1. **[Włącz ochronę chmury](enable-cloud-protection-microsoft-defender-antivirus.md)**. Ochronę w chmurze można włączyć za pomocą Microsoft Endpoint Manager (w tym Microsoft Endpoint Configuration Manager i Microsoft Intune), zasady grupy lub poleceń cmdlet programu PowerShell.

2. **[Określ poziom ochrony w chmurze](specify-cloud-protection-level-microsoft-defender-antivirus.md)**. Poziom ochrony oferowany przez chmurę można określić przy użyciu Microsoft Endpoint Manager lub zasady grupy. Poziom ochrony ma wpływ na ilość informacji udostępnianych w chmurze i na sposób agresywnego blokowania nowych plików.

3. **[Skonfiguruj i zweryfikuj połączenia sieciowe dla Program antywirusowy Microsoft Defender](configure-network-connections-microsoft-defender-antivirus.md)**. Istnieją pewne adresy URL firmy Microsoft, z którymi sieć i punkty końcowe muszą być w stanie nawiązać połączenie, aby ochrona w chmurze działała efektywnie. W tym artykule wymieniono adresy URL, które powinny być dozwolone za pośrednictwem reguł filtrowania zapory lub sieci, oraz instrukcje dotyczące potwierdzania, że sieć jest prawidłowo zarejestrowana w ramach ochrony w chmurze.

4. **[Skonfiguruj funkcję "blokuj od pierwszego wejrzenia"](configure-block-at-first-sight-microsoft-defender-antivirus.md)**. Funkcja "blokuj od pierwszego wejrzenia" może blokować nowe złośliwe oprogramowanie w ciągu kilku sekund bez konieczności czekania godzinami na tradycyjną analizę zabezpieczeń. Można ją włączyć i skonfigurować przy użyciu Microsoft Endpoint Manager lub zasady grupy.

5. **[Skonfiguruj okres limitu czasu bloku chmury](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md)**. Program antywirusowy Microsoft Defender może blokować uruchamianie podejrzanych plików podczas wykonywania zapytań dotyczących naszej usługi ochrony w chmurze. Czas działania pliku można skonfigurować przy użyciu Microsoft Endpoint Manager lub zasady grupy.

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)