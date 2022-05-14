---
title: Ochrona w chmurze i przesyłanie przykładów w Program antywirusowy Microsoft Defender
description: Dowiedz się więcej na temat ochrony i Program antywirusowy Microsoft Defender dostarczanej w chmurze
keywords: Program antywirusowy Microsoft Defender, technologie nowej generacji, przesyłanie przykładów oprogramowania antywirusowego, av nowej generacji, uczenie maszynowe, oprogramowanie chroniące przed złośliwym kodem, zabezpieczenia, defender, chmura, ochrona dostarczana w chmurze
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
ms.date: 02/24/2022
ms.collection: M365-security-compliance
ms.openlocfilehash: 08f8e0c861bfd19f11c5b011d0a8db41ce3e73bc
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419951"
---
# <a name="cloud-protection-and-sample-submission-at-microsoft-defender-antivirus"></a>Ochrona w chmurze i przesyłanie przykładów w Program antywirusowy Microsoft Defender

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Program antywirusowy Microsoft Defender używa wielu inteligentnych mechanizmów do wykrywania złośliwego oprogramowania. Jedną z najbardziej zaawansowanych możliwości jest możliwość zastosowania możliwości chmury do wykrywania złośliwego oprogramowania i przeprowadzania szybkiej analizy. Ochrona w chmurze i automatyczne przesyłanie przykładów współpracują z Program antywirusowy Microsoft Defender, aby chronić przed nowymi i pojawiającym się zagrożeniami. 

Jeśli zostanie wykryty podejrzany lub złośliwy plik, próbka zostanie wysłana do usługi w chmurze w celu analizy, podczas gdy Program antywirusowy Microsoft Defender blokuje plik. Natychmiast po dokonaniu ustalenia, co dzieje się szybko, plik jest zwalniany lub blokowany przez Program antywirusowy Microsoft Defender. 

Ten artykuł zawiera omówienie ochrony w chmurze i automatycznego przesyłania przykładów w Program antywirusowy Microsoft Defender. Aby dowiedzieć się więcej na temat ochrony w chmurze, zobacz [Ochrona w chmurze i Program antywirusowy Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md).

## <a name="how-cloud-protection-and-sample-submission-work-together"></a>Jak ochrona w chmurze i przesyłanie przykładów współpracują ze sobą

Aby zrozumieć, jak ochrona w chmurze współdziała z przykładowym przesyłaniem, warto zrozumieć, w jaki sposób usługa Defender for Endpoint chroni przed zagrożeniami. Usługa Microsoft Intelligent Security Graph monitoruje dane zagrożeń z rozległej sieci czujników. Firma Microsoft warstw opartych na chmurze modeli uczenia maszynowego, które mogą oceniać pliki na podstawie sygnałów od klienta i rozległej sieci czujników i danych w Graph Intelligent Security. Takie podejście daje usłudze Defender for Endpoint możliwość blokowania wielu nigdy wcześniej nie widzianych zagrożeń. 

Na poniższej ilustracji przedstawiono przepływ ochrony w chmurze i przykładowego przesyłania za pomocą Program antywirusowy Microsoft Defender:

:::image type="content" source="images/cloud-protection-flow.png" alt-text="Przepływ ochrony dostarczany przez chmurę" lightbox="images/cloud-protection-flow.png":::

Program antywirusowy Microsoft Defender i ochrona w chmurze automatycznie blokują większość nowych, nigdy wcześniej nie widzianych zagrożeń przy użyciu następujących metod:

1. Uproszczone modele uczenia maszynowego oparte na kliencie, blokujące nowe i nieznane złośliwe oprogramowanie.

2. Lokalna analiza zachowań, zatrzymywanie ataków opartych na plikach i bez plików.

3. Oprogramowanie antywirusowe o wysokiej precyzji, wykrywające typowe złośliwe oprogramowanie za pomocą technik ogólnych i heurystycznych.

4. Zaawansowana ochrona oparta na chmurze jest zapewniana w przypadkach, gdy Program antywirusowy Microsoft Defender uruchomiony w punkcie końcowym wymaga większej analizy w celu zweryfikowania intencji podejrzanego pliku.

   1. W przypadku, gdy Program antywirusowy Microsoft Defender nie może jasno określić, metadane pliku są wysyłane do usługi ochrony w chmurze. Często w milisekundach usługa ochrony w chmurze może określić na podstawie metadanych, czy plik jest złośliwy, czy nie jest zagrożeniem.  

      - Zapytanie w chmurze dotyczące metadanych pliku może być wynikiem zachowania, znaku sieci Web lub innych cech, w których nie określono jasnego werdyktu.
      - Wysyłany jest mały ładunek metadanych, którego celem jest osiągnięcie werdyktu dotyczącego złośliwego oprogramowania lub nie zagrożenia. Metadane nie zawierają danych osobowych(PII). Informacje, takie jak nazwy plików, są skrótami.
      - Może być synchroniczny lub asynchroniczny. W przypadku synchronicznego pliku nie zostanie otwarty, dopóki chmura nie wyrenderuje werdyktu. W przypadku asynchronicznego pliku zostanie otwarty podczas wykonywania analizy ochrony w chmurze.
      - Metadane mogą obejmować atrybuty PE, statyczne atrybuty plików, atrybuty dynamiczne i kontekstowe i nie tylko (zobacz [Przykłady metadanych wysyłanych do usługi ochrony w chmurze](#examples-of-metadata-sent-to-the-cloud-protection-service)).

   2. Po zbadaniu metadanych, jeśli Program antywirusowy Microsoft Defender ochrona w chmurze nie może osiągnąć jednoznacznego werdyktu, może zażądać próbki pliku do dalszej kontroli. To żądanie uwzględnia konfigurację ustawień dla przykładowego przesyłania:

      1. **Automatyczne wysyłanie bezpiecznych próbek** (wartość domyślna)
         - Sejf przykłady to przykłady, które często nie zawierają danych osobowych, takich jak: .bat, scr, .dll, .exe.
         - Jeśli plik prawdopodobnie zawiera identyfikator PII, użytkownik otrzyma żądanie zezwalania na przesyłanie przykładowych plików.
         - Ta opcja jest domyślna w systemach Windows, macOS i Linux.

      2. **Zawsze monituj**
         - W przypadku skonfigurowania użytkownik zawsze będzie monitowany o zgodę przed przesłaniem pliku
         - To ustawienie nie jest dostępne w macOS ochrony w chmurze

      3. **Automatycznie wysyłaj wszystkie przykłady**
         - W przypadku skonfigurowania wszystkie przykłady zostaną wysłane automatycznie
         - Jeśli chcesz, aby przykładowe przesyłanie zawierało makra osadzone w dokumentacji programu Word, musisz wybrać opcję "Automatycznie wyślij wszystkie przykłady"
         - To ustawienie nie jest dostępne w macOS ochrony w chmurze

      4. **Nie wysyłaj**
         - Zapobiega "blokuj od pierwszego wejrzenia" na podstawie analizy przykładowej pliku
         - Ustawienie "Nie wysyłaj" jest odpowiednikiem ustawienia "Wyłączone" w zasadach macOS
         - Metadane są wysyłane do wykrywania nawet wtedy, gdy przesyłanie przykładowe jest wyłączone

   3. Po przesłaniu metadanych i/lub plików do ochrony w chmurze możesz użyć **przykładów**, **detonacji** lub modeli uczenia maszynowego **analizy danych big data** , aby uzyskać werdykt. Wyłączenie ochrony dostarczanej w chmurze ograniczy analizę tylko do tego, co klient może zapewnić za pośrednictwem lokalnych modeli uczenia maszynowego i podobnych funkcji.

> [!IMPORTANT]
> [Ustawienie Blokuj od pierwszego wejrzenia (BAFS)](configure-block-at-first-sight-microsoft-defender-antivirus.md) zapewnia detonację i analizę w celu ustalenia, czy plik lub proces jest bezpieczny. BAFS może chwilowo opóźnić otwarcie pliku, dopóki nie zostanie osiągnięty werdykt. Jeśli wyłączysz przesyłanie przykładowe, bafs jest również wyłączony, a analiza plików jest ograniczona tylko do metadanych. Zalecamy włączenie przesyłania przykładów i bafs. Aby dowiedzieć się więcej, zobacz [Co to jest "blokuj od pierwszego wejrzenia"?](configure-block-at-first-sight-microsoft-defender-antivirus.md#what-is-block-at-first-sight)

## <a name="cloud-protection-levels"></a>Poziomy ochrony chmury

Ochrona w chmurze jest domyślnie włączona w Program antywirusowy Microsoft Defender. Zalecamy zachowanie włączonej ochrony w chmurze, chociaż można skonfigurować poziom ochrony dla organizacji. Zobacz [Określanie poziomu ochrony dostarczanej w chmurze dla Program antywirusowy Microsoft Defender](specify-cloud-protection-level-microsoft-defender-antivirus.md).

## <a name="sample-submission-settings"></a>Ustawienia przykładowego przesyłania

Oprócz konfigurowania poziomu ochrony w chmurze można skonfigurować ustawienia przykładowego przesyłania. Możesz wybrać jedną z kilku opcji:

- **Automatyczne wysyłanie bezpiecznych próbek (zachowanie domyślne**  )
- **Automatycznie wysyłaj wszystkie przykłady**  
- **Nie wysyłaj przykładów**  

Aby uzyskać informacje o opcjach konfiguracji przy użyciu Intune, Configuration Manager, obiektu zasad grupy lub programu PowerShell, zobacz [Włączanie ochrony w chmurze w Program antywirusowy Microsoft Defender](enable-cloud-protection-microsoft-defender-antivirus.md).

## <a name="examples-of-metadata-sent-to-the-cloud-protection-service"></a>Przykłady metadanych wysyłanych do usługi ochrony w chmurze

:::image type="content" source="images/cloud-protection-metadata-sample.png" alt-text="Przykłady metadanych wysyłanych do ochrony w chmurze w portalu Program antywirusowy Microsoft Defender" lightbox="images/cloud-protection-metadata-sample.png":::

W poniższej tabeli wymieniono przykłady metadanych wysłanych do analizy przez ochronę w chmurze:

| Wpisać | Atrybut |
|:---|:---|
| Atrybuty maszyny | `OS version` <br/> `Processor` <br/> `Security settings` |
| Atrybuty dynamiczne i kontekstowe | **Proces i instalacja** <br/> `ProcessName` <br/> `ParentProcess` <br/> `TriggeringSignature` <br/> `TriggeringFile` <br/> `Download IP and url` <br/> `HashedFullPath` <br/> `Vpath` <br/> `RealPath` <br/> `Parent/child relationships` <br/><br/>**Behawioralne** <br/> `Connection IPs` <br/> `System changes` <br/> `API calls` <br/> `Process injection` <br/><br/>**Ustawień regionalnych** <br/> `Locale setting` <br/> `Geographical location` |
| Atrybuty plików statycznych | **Częściowe i pełne skróty** <br/> `ClusterHash` <br/> `Crc16` <br/> `Ctph` <br/> `ExtendedKcrcs` <br/> `ImpHash` <br/> `Kcrc3n` <br/> `Lshash` <br/> `LsHashs` <br/> `PartialCrc1` <br/> `PartialCrc2` <br/> `PartialCrc3` <br/> `Sha1` <br/> `Sha256` <br/><br/>**Właściwości pliku** <br/>`FileName` <br/> `FileSize` <br/><br/> **Informacje o podpisie** <br/> `AuthentiCodeHash` <br/> `Issuer` <br/> `IssuerHash` <br/> `Publisher` <br/> `Signer` <br/> `SignerHash` |

## <a name="samples-are-treated-as-customer-data"></a>Przykłady są traktowane jako dane klienta

Na wszelki wypadek, gdy zastanawiasz się, co się dzieje z przykładowymi przesłaniami, usługa Defender for Endpoint traktuje wszystkie przykłady plików jako dane klienta. Firma Microsoft honoruje opcje przechowywania danych i geograficzne wybrane przez organizację podczas dołączania do usługi Defender for Endpoint. 

Ponadto usługa Defender for Endpoint otrzymała wiele certyfikatów zgodności, co świadczy o ciągłym przestrzeganiu zaawansowanego zestawu mechanizmów kontroli zgodności:

- ISO 27001
- ISO 27018
- SOC I, II, III
- PCI

Aby uzyskać więcej informacji, zapoznaj się z następującymi zasobami:

- [Oferty zgodności platformy Azure](/azure/storage/common/storage-compliance-offerings) 
- [Portal zaufania usługi](https://servicetrust.microsoft.com)
- [Ochrona punktu końcowego w usłudze Microsoft Defender magazyn danych i prywatność](data-storage-privacy.md#data-storage-location)

## <a name="other-file-sample-submission-scenarios"></a>Inne przykładowe scenariusze przesyłania plików

Istnieją jeszcze dwa scenariusze, w których usługa Defender for Endpoint może zażądać przykładu pliku, który nie jest związany z ochroną w chmurze w Program antywirusowy Microsoft Defender. Te scenariusze opisano w poniższej tabeli:

| Scenariusz | Opis |
|:---|:---|
|Ręczne zbieranie przykładowych plików w portalu Microsoft 365 Defender | Podczas dołączania urządzeń do usługi Defender for Endpoint można skonfigurować ustawienia dla [wykrywanie i reagowanie w punktach końcowych (EDR)](overview-endpoint-detection-response.md). Na przykład istnieje ustawienie umożliwiające włączenie przykładowych kolekcji z urządzenia, które można łatwo pomylić z przykładowymi ustawieniami przesyłania opisanymi w tym artykule. <br/><br/>Ustawienie EDR kontroluje zbieranie przykładowych plików z urządzeń w przypadku żądania za pośrednictwem portalu Microsoft 365 Defender i podlega już ustalonym rolom i uprawnieniom. To ustawienie może zezwalać na zbieranie plików z punktu końcowego lub blokować go dla funkcji, takich jak analiza szczegółowa w portalu Microsoft 365 Defender. Jeśli to ustawienie nie jest skonfigurowane, ustawieniem domyślnym jest włączenie kolekcji przykładowej. <br/><br/>Dowiedz się więcej o ustawieniach konfiguracji usługi Defender for Endpoint, zobacz: [Dołączanie narzędzi i metod dla urządzeń Windows 10 w usłudze Defender for Endpoint](configure-endpoints.md) |
| Zautomatyzowane badanie i analiza zawartości odpowiedzi | Gdy na urządzeniach są uruchamiane [zautomatyzowane badania](automated-investigations.md) (skonfigurowane do automatycznego uruchamiania w odpowiedzi na alert lub uruchamianie ręcznie), pliki zidentyfikowane jako podejrzane mogą być zbierane z punktów końcowych w celu dalszej inspekcji. W razie potrzeby w portalu Microsoft 365 Defender można wyłączyć funkcję analizy zawartości plików dla zautomatyzowanych badań. <br/><br/> Nazwy rozszerzeń plików można również modyfikować w celu dodawania lub usuwania rozszerzeń dla innych typów plików, które zostaną automatycznie przesłane podczas zautomatyzowanego badania. <br/><br/> Aby dowiedzieć się więcej, zobacz [Zarządzanie przekazywaniem plików automatyzacji](manage-automation-file-uploads.md). |

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)

## <a name="see-also"></a>Zobacz też

[Omówienie ochrony nowej generacji](next-generation-protection.md)

[Skonfiguruj korygowanie pod kątem wykrywania Program antywirusowy Microsoft Defender.](configure-remediation-microsoft-defender-antivirus.md)
