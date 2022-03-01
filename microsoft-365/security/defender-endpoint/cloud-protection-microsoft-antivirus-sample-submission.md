---
title: Ochrona chmury i przesyłanie próbek w aplikacji Program antywirusowy Microsoft Defender
description: Informacje o zabezpieczeniach i zabezpieczeniach w chmurze Program antywirusowy Microsoft Defender
keywords: Program antywirusowy Microsoft Defender, technologie następnej generacji, przykładowe przesyłanie oprogramowania antywirusowego, audio/wideo następnej generacji, uczenie maszynowe, ochrona przed złośliwym kodem, zabezpieczenia, defender, chmura, ochrona dostarczana w chmurze
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
ms.date: 10/18/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: 3ffd18a0b2a0e81f2f3a425434f5e786d8dc598d
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2021
ms.locfileid: "62996760"
---
# <a name="cloud-protection-and-sample-submission-in-microsoft-defender-antivirus"></a>Ochrona chmury i przesyłanie próbek w aplikacji Program antywirusowy Microsoft Defender

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Program antywirusowy Microsoft Defender

Program antywirusowy Microsoft Defender korzysta z wielu inteligentnych mechanizmów wykrywania złośliwego oprogramowania. Jedną z najbardziej zaawansowanych możliwości jest możliwość korzystania z możliwości chmury w zakresie wykrywania złośliwego oprogramowania i wykonywania szybkich analiz. Ochrona chmury i automatyczne przesyłanie próbek współpracują z programem Program antywirusowy Microsoft Defender, aby chronić się przed nowymi i wyłaniających się zagrożeniami. 

W przypadku wykrycia podejrzanego lub złośliwego pliku do usługi w chmurze jest wysyłana próbka danych do analizy, Program antywirusowy Microsoft Defender blokuje plik. Zaraz po dokonanym określaniu, co się stanie szybko, plik zostanie wydany lub zablokowany przez Program antywirusowy Microsoft Defender. 

Ten artykuł zawiera omówienie ochrony chmury i automatycznego przesyłania próbek w aplikacji Program antywirusowy Microsoft Defender. Aby dowiedzieć się więcej o ochronie chmury, zobacz [Ochrona i ochrona Program antywirusowy Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md).

## <a name="how-cloud-protection-and-sample-submission-work-together"></a>Jak współpracują ze sobą ochrona chmury i przykładowe przesyłanie

Aby zrozumieć, jak ochrona chmury współpracuje z przykładowym przesyłaniem, warto zrozumieć, w jaki sposób usługa Defender for Endpoint chroni się przed zagrożeniami. Funkcja inteligentnego zabezpieczeń firmy Microsoft Graph monitoruje dane zagrożeń za pomocą bardzo dużej sieci czujnika. Modele maszynowego uczenia opartego na chmurze firmy Microsoft, które mogą oceniać pliki na podstawie sygnałów od klienta i rozległej sieci czujnika oraz danych w inteligentnym systemie zabezpieczeń, Graph. Takie podejście umożliwia programowi Defender for Endpoint blokowanie wielu nigdy wcześniej widocznych zagrożeń. 

Poniższy obraz przedstawia przepływ ochrony chmury i przykładowego przesyłania za pomocą Program antywirusowy Microsoft Defender:

:::image type="content" source="images/cloud-protection-flow.png" alt-text="Przepływ ochrony w chmurze":::

Program antywirusowy Microsoft Defender i ochrony chmury automatycznie blokują na pierwszy rzut oka większość nowych, nigdy wcześniej widocznych zagrożeń, używając następujących metod:

1. Uproszczone modele maszynowego uczenia opartego na klientach, blokujące nowe i nieznane złośliwe oprogramowanie.

2. Lokalna analiza zachowania, zatrzymywanie ataków opartych na plikach i bez plików.

3. Oprogramowanie antywirusowe o wysokiej dokładności, wykrywające typowe złośliwe oprogramowanie za pomocą ogólnych i heuristic technik.

4. Zaawansowana ochrona oparta na chmurze jest zapewniana w przypadku Program antywirusowy Microsoft Defender uruchomionych w punkcie końcowym wymaga większej analizy w celu zweryfikowania intencji podejrzanego pliku.

   1. Jeśli nie Program antywirusowy Microsoft Defender jasnego określenia, metadane plików są wysyłane do usługi ochrony chmury. Często w ciągu kilku milisekund usługa ochrony chmury może na podstawie metadanych określić, czy plik jest złośliwy, czy nie.  

      - Zapytanie w chmurze metadanych plików może być wynikiem zachowania, znaku sieci Web lub innych cech, w przypadku których nie jest określony wyraźny werdykt.
      - Wysyłane są niewielkie metadane, których celem jest osiągnięcie werdyktu złośliwego oprogramowania lub zagrożenia. Metadane nie obejmują informacji umożliwiających identyfikację użytkownika. Informacje, takie jak nazwy plików, są skrótami.
      - Może być synchroniczny lub asynchroniczny. W przypadku synchronizacji plik nie będzie otwierany do czasu wyrenderowania werdyktu w chmurze. W przypadku asynchronicznego otwierania pliku podczas wykonywania analizy przez ochronę chmury.
      - Metadane mogą zawierać między innymi atrybuty PE, statyczne atrybuty plików, atrybuty dynamiczne i kontekstowe (zobacz Przykłady metadanych wysyłanych do usługi [ochrony chmury](#examples-of-metadata-sent-to-the-cloud-protection-service)).

   2. Po przeanalizowaniu metadanych, Program antywirusowy Microsoft Defender ochrona chmury nie może uzyskać bardziej szczegółowego werdyktu, może zażądać próbki pliku do dalszej inspekcji. To żądanie szanuje konfigurację ustawień przykładowego żądania przesłania:

      1. **Automatyczne wysyłanie bezpiecznych próbek** (domyślnie)
         - Sejf próbek uważa się, że nie zawierają często danych PII, takich jak: .bat, scr, .dll, .exe.
         - Jeśli plik prawdopodobnie zawiera identyfikator PII, użytkownik otrzyma żądanie umożliwienia przesłania przykładu pliku.
         - Jest to opcja domyślna dla systemów Windows, macOS i Linux.

      2. **Zawsze monituj**
         - Jeśli plik jest skonfigurowany, użytkownik zawsze będzie monitowany o zgodę przed przesłaniem pliku
         - To ustawienie nie jest dostępne w ochronie w chmurze systemu macOS

      3. **Automatyczne wysyłanie wszystkich próbek**
         - Jeśli wszystkie próbki zostały skonfigurowane, zostaną wysłane automatycznie
         - Jeśli chcesz, aby przykładowe przesyłanie zawierało makra osadzone w dokumentach programu Word, musisz wybrać pozycję Automatycznie wyślij wszystkie przykłady.
         - To ustawienie nie jest dostępne w przypadku ochrony w chmurze systemu macOS

      4. **Nie wysyłaj**
         - Zapobiega "blokowaniu na pierwszy rzut oka" na podstawie analizy próbki pliku
         - "Nie wysyłaj" jest równoważne z ustawieniem "Wyłączone" w zasadach macOS.
         - Metadane są wysyłane do wykrywania nawet wtedy, gdy przesyłanie przykładowe jest wyłączone

   3. Po przesłaniu metadanych i/lub plików do ochrony chmury możesz wykorzystać próbki **,** **detonację** lub modele  maszynowego uczenia maszynowego do analizy dużych danych, aby osiągnąć werdykt. Wyłączenie ochrony w chmurze ogranicza analizę wyłącznie do tego, co klient może zapewnić za pośrednictwem lokalnych modeli uczenia maszynowego i podobnych funkcji.

> [!IMPORTANT]
> [Blokowanie na pierwszy rzut oka (BAFS)](configure-block-at-first-sight-microsoft-defender-antivirus.md) zapewnia detonację i analizę w celu określenia, czy plik lub proces jest bezpieczny. Usługi BAFS mogą chwilę opóźnić otwieranie pliku do czasu jego werdyktu. Jeśli wyłączysz przesyłanie przykładowe, usługi BAFS również będą wyłączone, a analiza plików będzie ograniczona tylko do metadanych. Zalecamy, aby włączyć przesyłanie przykładowe i usługi BAFS. Aby dowiedzieć się więcej, [zobacz Co to jest "blok na pierwszy rzut oka"?](configure-block-at-first-sight-microsoft-defender-antivirus.md#what-is-block-at-first-sight)

## <a name="cloud-protection-levels"></a>Poziomy ochrony w chmurze

Ochrona chmury jest domyślnie włączona w Program antywirusowy Microsoft Defender. Zalecamy, aby włączyć ochronę w chmurze, chociaż można skonfigurować poziom ochrony dla organizacji. Zobacz [Określanie poziomu ochrony przed wiadomościami w chmurze Program antywirusowy Microsoft Defender](specify-cloud-protection-level-microsoft-defender-antivirus.md).

## <a name="sample-submission-settings"></a>Przykładowe ustawienia przesyłania

Oprócz konfigurowania poziomu ochrony w chmurze możesz skonfigurować przykładowe ustawienia przesyłania. Możesz wybrać jedną z kilku opcji:

- **Automatyczne wysyłanie bezpiecznych próbek**  (zachowanie domyślne)
- **Automatyczne wysyłanie wszystkich próbek**  
- **Nie wysyłaj próbek**  

Aby uzyskać informacje o opcjach konfiguracji przy użyciu usługi Intune, Menedżer konfiguracji, GPO lub PowerShell, zobacz Włączanie ochrony chmury w [Program antywirusowy Microsoft Defender](enable-cloud-protection-microsoft-defender-antivirus.md).

## <a name="examples-of-metadata-sent-to-the-cloud-protection-service"></a>Przykłady metadanych wysyłanych do usługi ochrony w chmurze

:::image type="content" source="images/cloud-protection-metadata-sample.png" alt-text="obraz przedstawiający przykłady metadanych wysyłanych do ochrony chmury w aplikacji Program antywirusowy Microsoft Defender":::

W poniższej tabeli podano przykłady metadanych wysyłanych do analizy za pomocą ochrony chmury:

| Wpisać | Atrybut |
|:---|:---|
| Atrybuty komputera | `OS version` <br/> `Processor` <br/> `Security settings` |
| Atrybuty dynamiczne i kontekstowe | **Proces i instalacja** <br/> `ProcessName` <br/> `ParentProcess` <br/> `TriggeringSignature` <br/> `TriggeringFile` <br/> `Download IP and url` <br/> `HashedFullPath` <br/> `Vpath` <br/> `RealPath` <br/> `Parent/child relationships` <br/><br/>**Behavioral** <br/> `Connection IPs` <br/> `System changes` <br/> `API calls` <br/> `Process injection` <br/><br/>**Locale** <br/> `Locale setting` <br/> `Geographical location` |
| Atrybuty plików statycznych | **Częściowe i pełne skróty** <br/> `ClusterHash` <br/> `Crc16` <br/> `Ctph` <br/> `ExtendedKcrcs` <br/> `ImpHash` <br/> `Kcrc3n` <br/> `Lshash` <br/> `LsHashs` <br/> `PartialCrc1` <br/> `PartialCrc2` <br/> `PartialCrc3` <br/> `Sha1` <br/> `Sha256` <br/><br/>**Właściwości pliku** <br/>`FileName` <br/> `FileSize` <br/><br/> **Informacje o podpisie** <br/> `AuthentiCodeHash` <br/> `Issuer` <br/> `IssuerHash` <br/> `Publisher` <br/> `Signer` <br/> `SignerHash` |

## <a name="samples-are-treated-as-customer-data"></a>Próbki są traktowane jako dane klienta

Jeśli tylko zastanawiasz się, co się dzieje z przykładami przesyłania, program Defender for Endpoint traktuje wszystkie przykłady plików jako dane klienta. Firma Microsoft szanuje zarówno opcje przechowywania danych geograficznych, jak i geograficznych wybrane przez Twoją organizację podczas dołączania do programu Defender dla punktu końcowego. 

Ponadto program Defender for Endpoint otrzymał wiele certyfikatów zgodności, przedstawiających nadal owacyjną odpowiedzialność za zaawansowany zestaw kontrolek zgodności:

- ISO 27001
- ISO 27018
- SOC I, II, III
- i PCI

Aby uzyskać więcej informacji, zapoznaj się z następującymi zasobami:

- [Oferty dotyczące zgodności z platformą Azure](/azure/storage/common/storage-compliance-offerings) 
- [Portal zaufania usług](https://servicetrust.microsoft.com)
- [Usługa Microsoft Defender for Endpoint data storage and privacy](data-storage-privacy.md#data-storage-location)

## <a name="other-file-sample-submission-scenarios"></a>Inne przykładowe scenariusze przesyłania plików

Istnieją jeszcze dwa scenariusze, w których usługa Defender for Endpoint może zażądać przykładu pliku, który nie jest związany z ochroną chmury w Program antywirusowy Microsoft Defender. Te scenariusze opisano w poniższej tabeli:

| Scenariusz | Opis |
|:---|:---|
|Ręczna kolekcja przykładowych plików w Microsoft 365 Defender pliku | Podczas dołączania urządzeń do usługi Defender for Endpoint możesz skonfigurować ustawienia programu [wykrywanie i reagowanie w punktach końcowych (EDR)](overview-endpoint-detection-response.md). Na przykład istnieje ustawienie umożliwiające włączenie przykładowych kolekcji z urządzenia, które można łatwo pomylić z ustawieniami przykładowego przesyłania opisanymi w tym artykule. <br/><br/>Ustawienie EDR określa przykładowe kolekcje plików z urządzeń w przypadku zażądania za pośrednictwem portalu Microsoft 365 Defender i podlega już ustalona rolam i uprawnieniami. To ustawienie może zezwalać na zbieranie plików z punktu końcowego lub blokować takie funkcje, jak analiza dogłębna w portalu Microsoft 365 Defender sieci Web. Jeśli to ustawienie nie jest skonfigurowane, domyślnie jest włączone przykładowe kolekcje. <br/><br/>Aby uzyskać informacje na temat ustawień konfiguracji programu Defender dla punktu końcowego, zobacz: Narzędzia i metody dołączania do Windows 10 [w programie Defender for Endpoint](configure-endpoints.md) |
| Zautomatyzowane badanie i analiza zawartości odpowiedzi | [Gdy na](automated-investigations.md) urządzeniach są uruchomione zautomatyzowane badania (po skonfigurowaniu automatycznego uruchamiania w odpowiedzi na alert lub uruchomienie ręczne), z punktów końcowych można zbierać pliki zidentyfikowane jako podejrzane w celu dalszej inspekcji. W razie potrzeby funkcję analizy zawartości plików dla zautomatyzowanych analiz można wyłączyć w portalu Microsoft 365 Defender plikach. <br/><br/> Nazwy rozszerzeń plików można też modyfikować w celu dodania lub usunięcia rozszerzeń dla innych typów plików, które będą automatycznie przesyłane podczas automatycznego badania. <br/><br/> Aby dowiedzieć się więcej, zobacz [Zarządzanie przekazywaniem plików automatyzacji](manage-automation-file-uploads.md). |

## <a name="see-also"></a>Zobacz też

[Omówienie ochrony następnej generacji](next-generation-protection.md)
