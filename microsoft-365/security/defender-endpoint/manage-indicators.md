---
title: Utwórz wskaźniki
ms.reviewer: ''
description: Tworzenie wskaźników dla skrótu pliku, adresu IP, adresów URL lub domen definiujących wykrywanie, zapobieganie i wykluczanie jednostek.
keywords: zarządzanie, dozwolone, zablokowane, blokowe, czyste, złośliwe, skróty plików, adres IP, adresy URL, domena
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
ms.openlocfilehash: 55f9529d511435eb66f2791fe8a177a9fa35a8a5
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666333"
---
# <a name="create-indicators"></a>Utwórz wskaźniki

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
>
> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Wskaźnik kompromisu (IoCs) jest istotną funkcją w każdym rozwiązaniu ochrony punktu końcowego. Ta funkcja zapewnia usłudze SecOps możliwość ustawiania listy wskaźników wykrywania i blokowania (zapobieganie i reagowanie).

Tworzenie wskaźników definiujących wykrywanie, zapobieganie i wykluczanie jednostek. Możesz zdefiniować akcję do wykonania, a także czas trwania, kiedy zastosować akcję, a także zakres grupy urządzeń, do których ma zostać zastosowana.

Obecnie obsługiwane źródła to aparat wykrywania w chmurze usługi Defender for Endpoint, zautomatyzowany aparat badania i korygowania oraz aparat zapobiegania punktom końcowym (Program antywirusowy Microsoft Defender).

## <a name="cloud-detection-engine"></a>Aparat wykrywania chmury

Aparat wykrywania chmury usługi Defender for Endpoint regularnie skanuje zebrane dane i próbuje dopasować ustawione wskaźniki. W przypadku dopasowania akcja zostanie wykonana zgodnie z ustawieniami określonymi dla IoC.

## <a name="endpoint-prevention-engine"></a>Aparat zapobiegania punktom końcowym

Ta sama lista wskaźników jest honorowana przez agenta zapobiegania. Oznacza to, że jeśli usługa Microsoft Defender AV jest podstawową usługą AV skonfigurowaną, dopasowane wskaźniki będą traktowane zgodnie z ustawieniami. Jeśli na przykład akcja to "Alert and Block", usługa Microsoft Defender AV uniemożliwi wykonywanie plików (blokuj i koryguj), a odpowiedni alert zostanie zgłoszony. Z drugiej strony, jeśli akcja ma wartość "Zezwalaj", usługa Microsoft Defender AV nie wykryje ani nie zablokuje uruchamiania pliku.

## <a name="automated-investigation-and-remediation-engine"></a>Aparat zautomatyzowanego badania i korygowania

Zautomatyzowane badanie i korygowanie zachowują się tak samo. Jeśli wskaźnik ma wartość "Zezwalaj", automatyczne badanie i korygowanie zignoruje "zły" werdykt. Jeśli ustawiono opcję "Blokuj", automatyczne badanie i korygowanie będą traktować je jako "złe".

Ustawienie EnableFileHashComputation oblicza skrót pliku dla certyfikatu i pliku IoC podczas skanowania plików. Obsługuje wymuszanie IoC skrótów i certyfikatów należą do zaufanych aplikacji. Zostanie ona włączona współbieżnie i wyłączona z ustawieniem pliku zezwalania lub blokowania. Funkcja EnableFileHashComputation jest włączona ręcznie za pośrednictwem zasady grupy i jest domyślnie wyłączona.

Podczas tworzenia nowego wskaźnika (IoC) jest dostępna co najmniej jedna z następujących akcji:

- Zezwalaj — usługa IoC będzie mogła działać na urządzeniach.
- Inspekcja — alert zostanie wyzwolony po uruchomieniu usługi IoC.
- Ostrzeżenie — usługa IoC wyświetli ostrzeżenie, że użytkownik może pominąć 
- Blokuj wykonywanie — nie będzie można uruchomić usługi IoC.
- Blokuj i koryguj — usługa IoC nie będzie mogła działać, a akcja korygowania zostanie zastosowana do IoC.

>[!NOTE]
> Użycie trybu ostrzeżenia spowoduje wyświetlenie monitu dla użytkowników z ostrzeżeniem, jeśli otworzą ryzykowną aplikację. Monit nie zablokuje korzystania z aplikacji, ale możesz podać niestandardowy komunikat i linki do strony firmowej opisującej odpowiednie użycie aplikacji. Użytkownicy nadal mogą pominąć ostrzeżenie i nadal korzystać z aplikacji, jeśli zajdzie taka potrzeba. Aby uzyskać więcej informacji, zobacz [Zarządzanie aplikacjami odnalezionych przez Ochrona punktu końcowego w usłudze Microsoft Defender](/cloud-app-security/mde-govern).

Możesz utworzyć wskaźnik dla:

- [Pliki](indicator-file.md)
- [Adresy IP, adresy URL/domeny](indicator-ip-domain.md)
- [Certyfikaty](indicator-certificates.md)

W poniższej tabeli przedstawiono dokładnie, które akcje są dostępne dla każdego typu wskaźnika (IoC):

| Typ IoC | Dostępne akcje |
|:---|:---|
| [Pliki](indicator-file.md) | Zezwalaj <br> Inspekcji <br> Blokuj i koryguj |
| [Adresy IP](indicator-ip-domain.md) | Zezwalaj <br> Inspekcji <br> Blokuj wykonywanie <br> Ostrzec |
| [Adresy URL i domeny](indicator-ip-domain.md) | Zezwalaj <br> Inspekcji <br> Blokuj wykonywanie<br> Ostrzec |
| [Certyfikaty](indicator-certificates.md) | Zezwalaj <br> Blokuj i koryguj |

Funkcjonalność istniejących wcześniej IoCs nie ulegnie zmianie. Zmieniono jednak nazwę wskaźników tak, aby odpowiadały bieżącym obsługiwanym akcjom odpowiedzi:

- Nazwa akcji odpowiedzi "tylko alert" została zmieniona na "inspekcja" z włączonym ustawieniem generowania alertu.
- Nazwa odpowiedzi "alert i blok" została zmieniona na "blokuj i koryguj" przy użyciu opcjonalnego ustawienia alertu generowania.

Schemat interfejsu API IoC i identyfikatory zagrożeń z wyprzedzeniem zostały zaktualizowane w celu dopasowania ich do zmiany nazwy akcji odpowiedzi IoC. Zmiany schematu interfejsu API mają zastosowanie do wszystkich typów IoC.

> [!Note]
> Istnieje limit 15 000 wskaźników na dzierżawę. Wskaźniki plików i certyfikatów nie blokują [wykluczeń zdefiniowanych dla Program antywirusowy Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus). Wskaźniki nie są obsługiwane w Program antywirusowy Microsoft Defender, gdy są w trybie pasywnym.
>
> Format importowania nowych wskaźników (IoCs) zmienił się zgodnie z nowymi zaktualizowanymi ustawieniami akcji i alertów. Zalecamy pobranie nowego formatu CSV, który można znaleźć w dolnej części panelu importu.

## <a name="related-topics"></a>Tematy pokrewne

- [Tworzenie kontekstowego IoC](respond-file-alerts.md#add-indicator-to-block-or-allow-a-file)
- [Korzystanie z interfejsu API wskaźników Ochrona punktu końcowego w usłudze Microsoft Defender](ti-indicator.md)
- [Korzystanie ze zintegrowanych rozwiązań partnerów](partner-applications.md)
