---
title: Tworzenie wskaźników dla plików
ms.reviewer: ''
description: Tworzenie wskaźników dla skrótu plików definiującego wykrywanie, zapobieganie i wykluczenie obiektów.
keywords: file, hash, manage, allowed, blocked, block, clean, malicious, file hash, ip address, urls, domain
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 2ee262e2a42bcf4bd03a6d1204b60412d60740d5
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2022
ms.locfileid: "63015824"
---
# <a name="create-indicators-for-files"></a>Tworzenie wskaźników dla plików

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Zapobiegaj dalszej propagacji ataków w organizacji, aby zablokować potencjalnie złośliwe pliki lub podejrzewane złośliwe oprogramowanie. Jeśli znasz potencjalnie złośliwy plik wykonywalny (PE, Portable Wykonywalna), możesz go zablokować. Ta operacja uniemożliwi jej odczytanie, napisane lub wykonanie na urządzeniach w Twojej organizacji.

Istnieją trzy sposoby tworzenia wskaźników dla plików:

- Tworząc wskaźnik za pośrednictwem strony ustawień
- Tworząc wskaźnik kontekstowy za pomocą przycisku dodaj wskaźnik na stronie szczegółów pliku
- Tworzenie wskaźnika przy użyciu interfejsu [API wskaźnika](ti-indicator.md)

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed utworzeniem wskaźników dla plików należy poznać następujące wymagania wstępne:

- Ta funkcja jest dostępna, jeśli Twoja **organizacja Program antywirusowy Microsoft Defender (** w trybie aktywnym) i jest włączona **ochrona oparta na chmurze**. Aby uzyskać więcej informacji, zobacz [Zarządzanie ochroną opartą na chmurze](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus).

- Wersja klienta ochrony przed złośliwym oprogramowaniem musi mieć wersję 4.18.1901.x lub nowszą. Zobacz [Wersje miesięcznej platformy i aparatu](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions)

- Obsługiwane na urządzeniach z systemem Windows 10 w wersji 1703 lub nowszej, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 i Windows Server 2022.
    
   >[!NOTE]
    >Windows Server 2016 i Windows Server 2012 R2 muszą zostać naniesone zgodnie z instrukcjami podanymi w te sposób: Windows [onboard](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016), aby ta funkcja działała. 

- Aby rozpocząć blokowanie plików, musisz najpierw włączyć funkcję blokowania lub zezwalania [w programie](advanced-features.md) Ustawienia.

Ta funkcja ma na celu zapobieganie pobieraniu z sieci Web potencjalnie złośliwego oprogramowania (lub potencjalnie złośliwych plików). Obecnie obsługuje przenośne pliki wykonywalne (PE), w tym pliki .exe i .dll pe. Zakres będzie z czasem rozszerzany.

## <a name="create-an-indicator-for-files-from-the-settings-page"></a>Tworzenie wskaźnika dla plików na stronie ustawień

1. W okienku nawigacji wybierz pozycję Wskaźnik **Ustawienia** \> **punktów** \> **końcowych** (w obszarze **Reguły**).

2. Wybierz **kartę Skróty** plików.

3. Wybierz **wskaźnik Dodaj**.

4. Określ następujące szczegóły:
    - Wskaźnik — określ szczegóły jednostki i zdefiniuj wygasanie wskaźnika.
    - Akcja — określ akcję, która ma zostać wykonane, i podaj opis.
    - Zakres — definiowanie zakresu grupy urządzeń.

5. Przejrzyj szczegóły na karcie Podsumowanie, a następnie wybierz pozycję **Zapisz**.

## <a name="create-a-contextual-indicator-from-the-file-details-page"></a>Tworzenie wskaźnika kontekstowego na stronie szczegółów pliku

Jedną z opcji podczas robienia [akcji odpowiedzi na plik](respond-file-alerts.md) jest dodanie wskaźnika dla pliku. Po dodaniu skrótu wskaźnika dla pliku możesz podnieść alert i zablokować plik za każdym razem, gdy urządzenie w organizacji spróbuje go uruchomić.

Pliki automatycznie blokowane przez wskaźnik nie będą widoczne w Centrum akcji pliku, ale alerty będą nadal widoczne w kolejce alertów.

## <a name="public-preview-alerting-on-file-blocking-actions"></a>Podgląd publiczny: Alerty dotyczące akcji blokowania plików

> [!IMPORTANT]
> Informacje zawarte w tej sekcji (Publiczna wersja **zapoznawcza** automatycznego aparatu badań i rozwiązywania problemów) dotyczą produktu przedpremierowego, który może zostać znacznie zmodyfikowany przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

Obecnie obsługiwane są działania dotyczące tego typu plików, które można insektować, blokować i rekultywować. Po wybraniu opcji zablokowania pliku możesz zdecydować, czy jest konieczne wyzwalanie alertu. Dzięki temu można kontrolować liczbę alertów o uzyskiwaniu powiadomień do zespołów ds. bezpieczeństwa i upewnić się, że są podwyższone tylko wymagane alerty.

W Microsoft 365 Defender **przejdź do Ustawienia** >  EndpointsIndicatorsAdd >  >  **Nowy skrót pliku**.

Wybierz opcję Blokowanie i rozwiązywanie problemów z plikiem.

Wybierz opcję Wygeneruj alert dla zdarzenia blokowania plików i zdefiniuj ustawienia alertów:

- Tytuł alertu
- Ważność alertu
- Kategoria
- Opis
- Zalecane akcje

![Ustawienia alertów dotyczące wskaźników plików.](images/indicators-generate-alert.png)

> [!IMPORTANT]
>
> - Zazwyczaj bloki plików są wymuszane i usuwane w ciągu kilku minut, ale może potrwać do 30 minut w górę.
> - W przypadku konfliktu zasad pliku IoC z tym samym typem wymuszania i elementem docelowym zostaną zastosowane zasady bezpieczniejszego skrótu. Zasady IoC skrótu plików SHA-256 przejmą zasady IoC skrótu SHA-1, które przejmą zasady IoC skrótu pliku MD5, jeśli te typy skrótów definiują ten sam plik. Jest tak zawsze, niezależnie od grupy urządzeń.
> - We wszystkich innych przypadkach, jeśli zasady pliku IoC powodujące konflikt z tym samym elementem docelowym wymuszania zostaną zastosowane do wszystkich urządzeń i grupy urządzenia, wówczas w przypadku urządzenia zasady w grupie urządzeń zostaną zastosowane.
> - Jeśli zasady grupy EnableFileHashComputation są wyłączone, dokładność blokowania pliku IoC jest zmniejszana. Włączenie może jednak `EnableFileHashComputation` mieć wpływ na wydajność urządzenia. Na przykład kopiowanie dużych plików z udziału sieciowego na urządzenie lokalne, szczególnie przez połączenie VPN, może mieć wpływ na wydajność urządzenia.
>
> Aby uzyskać więcej informacji na temat zasad grupy EnableFileHashComputation, zobacz Program [CSP usługi Defender](/windows/client-management/mdm/defender-csp).

## <a name="public-preview-advanced-hunting-capabilities"></a>Publiczna wersja zapoznawcza: Zaawansowane możliwości chłoniania

> [!IMPORTANT]
> Informacje zawarte w tej sekcji (Publiczna wersja **zapoznawcza** automatycznego aparatu badań i rozwiązywania problemów) dotyczą produktu przedpremierowego, który może zostać znacznie zmodyfikowany przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

Możesz zapytanie dotyczące działania akcji reagowania z wyprzedzeniem. Poniżej przedstawiono przykładowy, przeszły kwerendę wyszukiwania:

```console
search in (DeviceFileEvents, DeviceProcessEvents, DeviceEvents, DeviceRegistryEvents, DeviceNetworkEvents, DeviceImageLoadEvents, DeviceLogonEvents)
Timestamp > ago(30d)
| where AdditionalFields contains "EUS:Win32/CustomEnterpriseBlock!cl"
```

Aby uzyskać więcej informacji na temat zaawansowanego wyszukiwania, zobacz [Aktywne wyszukiwanie zagrożeń za pomocą zaawansowanego wyszukiwania](advanced-hunting-overview.md).

Poniżej znajdują się dodatkowe nazwy wątków, których można używać w przykładowym zapytaniu powyżej:

Pliki:

- EUS:Win32/CustomEnterpriseBlock!cl
- EUS:Win32/CustomEnterpriseNoAlertBlock!cl

Certyfikaty:

- EUS:Win32/CustomCertEnterpriseBlock!cl

Działanie działania reagowania może być również widać na osi czasu urządzenia.

## <a name="policy-conflict-handling"></a>Obsługa konfliktów zasad

Konflikt zasad Cert i obsługi plików IoC będzie postępować zgodnie z poniższymi kolejnościami:

- Jeśli plik nie jest dozwolony przez Windows Defender i zasady trybu wymuszania funkcji AppLocker **, zablokuj**
- W innym przypadku, jeśli plik jest dozwolony przez Program antywirusowy Microsoft Defender wykluczeniu, a następnie wybierz **pozycję Zezwalaj**
- Inaczej, jeśli plik jest zablokowany lub ostrzegany przez blokadę lub ostrzeganie pliku o stanie IoC, a następnie **zablokuj/ostrzegaj**
- W innym przypadku, jeśli plik jest dozwolony przez zasady IoC zezwalania na plik, a następnie wybierz pozycję **Zezwalaj**
- Inaczej, jeśli plik jest zablokowany przez reguły ASR, CFA, AV, SmartScreen, a następnie **Zablokuj**
- Inaczej **zezwalaj** (przekazuje Windows Defender sterowania aplikacją & zasad AppLocker, do których nie mają zastosowania żadne reguły IoC)

W przypadku konfliktu zasad pliku IoC z tym samym typem wymuszania i elementem docelowym zostaną zastosowane zasady bezpieczniejszego (dłuższego) skrótu. Na przykład zasady IoC skrótu pliku SHA-256 będą przejmować zasady IoC skrótu MD5, jeśli oba typy skrótów definiują ten sam plik.

> [!WARNING]
> Obsługa konfliktów zasad dla plików i certyfikatów różni się od obsługi konfliktów zasad dla domen/adresów URL/adresów IP.

W celu zarządzanie lukami w zabezpieczeniach zagrożenia i zablokowanie blokady aplikacji, która jest podatna na zagrożenia, na komputerach IoC plików są używane wymuszenia i są one zgodne z powyższymi kolejnościami obsługi konfliktów.

### <a name="examples"></a>Przykłady

<br>

****

|Składnik|Wymuszanie składników|Wskaźnik pliku Akcja|Result (Wynik)|
|---|---|---|---|
|Wykluczenie ścieżki zmniejszania powierzchni ataków|Zezwalaj|Blokuj|Blokuj|
|Reguła zmniejszania powierzchni ataków|Blokuj|Zezwalaj|Zezwalaj|
|Windows Defender kontrolki aplikacji|Zezwalaj|Blokuj|Zezwalaj|
|Windows Defender kontrolki aplikacji|Blokuj|Zezwalaj|Blokuj|
|Program antywirusowy Microsoft Defender wykluczenia|Zezwalaj|Blokuj|Zezwalaj|
|

## <a name="see-also"></a>Zobacz też

- [Tworzenie wskaźników](manage-indicators.md)
- [Tworzenie wskaźników adresów IP oraz adresów URL/domen](indicator-ip-domain.md)
- [Tworzenie wskaźników na podstawie certyfikatów](indicator-certificates.md)
- [Zarządzanie wskaźnikami](indicator-manage.md)
