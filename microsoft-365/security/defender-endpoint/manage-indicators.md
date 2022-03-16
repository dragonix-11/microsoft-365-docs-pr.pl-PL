---
title: Tworzenie wskaźników
ms.reviewer: ''
description: Tworzenie wskaźników dla skrótu plików, adresu IP, adresów URL lub domen definiujące wykrywanie, zapobieganie i wykluczenie obiektów.
keywords: manage, allowed, blocked, block, clean, malicious, file hash, ip address, urls, domain
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
ms.openlocfilehash: 00685ee4540949028b8bb438dd8a4965e2e9a5e7
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2022
ms.locfileid: "63513062"
---
# <a name="create-indicators"></a>Tworzenie wskaźników

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
>
> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Wskaźnik naruszenia zabezpieczeń (IoCs) to podstawowa funkcja w każdym rozwiązaniu ochrony punktu końcowego. Ta funkcja umożliwia programowi SecOps ustawianie listy wskaźników do wykrywania i blokowania (zapobiegania i reagowania).

Tworzenie wskaźników definiujące wykrywanie, zapobieganie i wykluczenie obiektów. Możesz zdefiniować akcję, która ma zostać podjęta, a także czas trwania, do kiedy zastosować akcję, a także zakres grupy urządzeń, do których chcesz zastosować akcję.

Obecnie obsługiwane źródła to aparat wykrywania w chmurze usługi Defender for Endpoint, zautomatyzowany aparat badania i rozwiązywania problemów oraz aparat ochrony przed punktami końcowymi (Program antywirusowy Microsoft Defender).

## <a name="cloud-detection-engine"></a>Aparat wykrywania chmury

Aparat wykrywania w chmurze usługi Defender for Endpoint regularnie skanuje zebrane dane i próbuje dopasować je do ustawionych wskaźników. W przypadku dopasowania akcja zostanie podjęta zgodnie z ustawieniami określonymi dla IoC.

## <a name="endpoint-prevention-engine"></a>Aparat ochrony przed punktami końcowymi

Ten sam wykaz wskaźników jest honorowany przez agenta zapobiegania. Oznacza to, że jeśli program Microsoft Defender AV jest podstawowym skonfigurowanym audio/wideo, dopasowane wskaźniki będą traktowane zgodnie z ustawieniami. Jeśli na przykład akcja to "Alert i blokowanie", program Microsoft Defender AV uniemożliwi wykonywanie plików (blokowanie i rozwiązywanie problemów), a odpowiedni alert zostanie podniesiony. Z drugiej strony, jeśli akcja jest ustawiona na "Allow" (Zezwalaj), program Microsoft Defender AV nie wykryje ani nie zablokuje uruchamiania pliku.

## <a name="automated-investigation-and-remediation-engine"></a>Zautomatyzowany aparat badań i rozwiązywania problemów

Zautomatyzowane badania i działania naprawcze działają tak samo. Jeśli wskaźnik jest ustawiony na "Zezwalaj", automatyczne badanie i rozwiązywanie problemów zignoruje "zły" werdykt. Jeśli ustawiono opcję "Blokowanie", automatyczne badanie i rozwiązywanie problemów będzie traktować je jak "złe".

Ustawienie EnableFileHashComputation oblicza skrót pliku dla certyfikatu i pliku IoC podczas skanowania plików. Obsługuje ono wymuszanie skrótów i certyfikatów przez program IoC, które należą do zaufanych aplikacji. Będzie on włączany i wyłączany jednocześnie z ustawieniem zezwalania lub blokowania pliku. Funkcja EnableFileHashComputation jest włączana ręcznie za pośrednictwem zasady grupy i jest domyślnie wyłączona.

Podczas tworzenia nowego wskaźnika (IoC) dostępna jest co najmniej jedna z następujących akcji:

- Zezwalaj — na Twoich urządzeniach będzie można uruchamiać urządzenie IoC.
- Inspekcja — po uruchomienie aplikacji IoC zostanie wyzwolony alert.
- Ostrzegaj — WiAD wyświetli monit z ostrzeżeniem, że użytkownik może pominąć 
- Blokuj wykonywanie — nie będzie można uruchomić programu IoC.
- Blokowanie i rozwiązywanie problemów — centrum IoC nie będzie dozwolone, a do centrum IoC zostanie zastosowana akcja rozwiązywania problemów.

>[!NOTE]
> Użycie trybu ostrzegawczego spowoduje, że użytkownicy będą monitować o ostrzeżenie, jeśli otworzą one ryzykowną aplikację. Monit nie zablokuje im możliwości korzystania z aplikacji, ale możesz podać niestandardowy komunikat i linki do strony firmy opisujące odpowiednie użycie aplikacji. Użytkownicy nadal mogą pominąć ostrzeżenie i w razie potrzeby nadal korzystać z aplikacji. Aby uzyskać więcej informacji, zobacz [Reguluj aplikacje odkryte przez program Microsoft Defender for Endpoint](/cloud-app-security/mde-govern).

Możesz utworzyć wskaźnik dla:

- [Pliki](indicator-file.md)
- [Adresy IP, adresy URL/domeny](indicator-ip-domain.md)
- [Certyfikaty](indicator-certificates.md)

W poniższej tabeli przedstawiono dokładnie, które akcje są dostępne dla każdego typu wskaźnika (IoC):

| Typ IoC | Dostępne akcje |
|:---|:---|
| [Pliki](indicator-file.md) | Zezwalaj <br> Inspekcja <br> Blokowanie i rozwiązywanie problemów |
| [Adresy IP](indicator-ip-domain.md) | Zezwalaj <br> Inspekcja <br> Blokuj wykonywanie <br> Ostrzegaj |
| [Adresy URL i domeny](indicator-ip-domain.md) | Zezwalaj <br> Inspekcja <br> Blokuj wykonywanie<br> Ostrzegaj |
| [Certyfikaty](indicator-certificates.md) | Zezwalaj <br> Blokowanie i rozwiązywanie problemów |

Funkcjonalność istniejących wcześniej komputerów IoC nie zmieni się. Nazwy wskaźników zostały jednak zmienione tak, aby były zgodne z obecnie obsługiwanymi akcjami odpowiedzi:

- Akcja odpowiedzi "Tylko alert" została zmieniona na "inspekcja" z włączonym ustawieniem generuj alert.
- Nazwa odpowiedzi "alert i blok" została zmieniona na "blokowanie i rozwiązywanie problemów" przy użyciu opcjonalnego ustawienia generuj alert.

Schemat interfejsu API IoC i identyfikatory zagrożeń z wyprzedzeniem zostały zaktualizowane, aby dopasować je do nazw akcji odpowiedzi IoC. Zmiany schematu interfejsu API dotyczą wszystkich typów IoC.

> [!Note]
> Istnieje limit 15 000 wskaźników na dzierżawcę. Wskaźniki plików i certyfikatów nie blokują [wykluczeń zdefiniowanych dla Program antywirusowy Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus). Wskaźniki nie są obsługiwane w trybie Program antywirusowy Microsoft Defender, gdy są w trybie pasywnym.
>
> Format importowania nowych wskaźników (IoCs) zmienił się zgodnie z nowymi zaktualizowanymi ustawieniami akcji i alertów. Zalecamy pobranie nowego formatu CSV, który znajduje się u dołu panelu importowania.

## <a name="related-topics"></a>Tematy pokrewne

- [Tworzenie kontekstowego IoC](respond-file-alerts.md#add-indicator-to-block-or-allow-a-file)
- [Używanie interfejsu API wskaźników programu Microsoft Defender dla punktów końcowych](ti-indicator.md)
- [Używanie zintegrowanych rozwiązań partnerów](partner-applications.md)
