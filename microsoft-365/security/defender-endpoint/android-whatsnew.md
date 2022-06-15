---
title: Co nowego w Ochrona punktu końcowego w usłudze Microsoft Defender na Android
description: Dowiedz się więcej o najważniejszych zmianach w poprzednich wersjach Ochrona punktu końcowego w usłudze Microsoft Defender na Android.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mac, instalacja, macos, whatsnew
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: reference
ms.technology: mde
ms.openlocfilehash: d1379836a2d55a8c6c256ce734c40acc5fc48599
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2022
ms.locfileid: "66090503"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-android"></a>Co nowego w Ochrona punktu końcowego w usłudze Microsoft Defender na Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="network-protection"></a>Ochrona sieci
Ochrona sieci w Ochrona punktu końcowego w usłudze Microsoft Defender jest teraz dostępna w publicznej wersji zapoznawczej. Ochrona sieci zapewnia ochronę przed nieautoryzowanymi zagrożeniami związanymi z Wi-Fi, nieautoryzowanym sprzętem, takim jak urządzenia ananasowe, i powiadamia użytkownika o wykryciu powiązanego zagrożenia. Użytkownicy zobaczą również środowisko z przewodnikiem umożliwiające nawiązywanie połączeń z bezpiecznymi sieciami i zmienianie sieci po nawiązaniu połączenia z niezabezpieczonym połączeniem.

Obejmuje ona kilka kontrolek administratora zapewniających elastyczność, na przykład możliwość konfigurowania funkcji z poziomu centrum Microsoft Endpoint Manager Administracja. Administratorzy mogą również włączyć mechanizmy kontroli prywatności, aby skonfigurować dane wysyłane przez usługę Defender for Endpoint z urządzeń Android. 

Jeśli chcesz wziąć udział w tej publicznej wersji zapoznawczej, udostępnij nam swój identyfikator dzierżawy w networkprotection@microsoft.com. Aby uzyskać więcej informacji, zobacz [ochrona sieci](/microsoft-365/security/defender-endpoint/android-configure).

>[!NOTE]
>Usługa Microsoft Defender nie jest już obsługiwana w wersjach poniżej 1.0.3011.0302. Użytkownicy są proszeni o uaktualnienie do najnowszych wersji w celu zapewnienia bezpieczeństwa urządzeń.
Aby zostać zaktualizowanym, użytkownicy mogą wykonać następujące czynności:
>1. W profilu służbowym przejdź do pozycji Zarządzane Sklep Play.
>2. Naciśnij ikonę profilu w prawym górnym rogu i wybierz pozycję "Zarządzaj aplikacjami i urządzeniem".
>3. Zlokalizuj rozwiązanie MDE w obszarze dostępne aktualizacje i wybierz pozycję Aktualizuj.
>
>Jeśli wystąpią jakiekolwiek problemy, [prześlij opinię w aplikacji](/security/defender-endpoint/android-support-signin#send-in-app-feedback).

## <a name="microsoft-defender-for-endpoint-is-now-microsoft-defender-in-the-play-store"></a>Ochrona punktu końcowego w usłudze Microsoft Defender jest teraz usługą Microsoft Defender w sklepie Play

Ochrona punktu końcowego w usłudze Microsoft Defender jest teraz dostępna jako **usługa Microsoft Defender** w sklepie play. Dzięki tej aktualizacji aplikacja będzie dostępna w wersji zapoznawczej dla **użytkowników w regionie USA** — w zależności od sposobu logowania się do aplikacji przy użyciu konta służbowego lub osobistego będziesz mieć dostęp do funkcji dla Ochrona punktu końcowego w usłudze Microsoft Defender lub funkcji usługi Microsoft Defender dla użytkowników indywidualnych. Aby uzyskać więcej informacji, zobacz [ten blog](https://www.microsoft.com/microsoft-365/microsoft-defender-for-individuals) .

## <a name="threat-and-vulnerability-management"></a>Zarządzanie zagrożeniami i lukami w zabezpieczeniach

25 stycznia 2022 r. ogłosiliśmy ogólną dostępność zarządzania zagrożeniami i lukami w zabezpieczeniach w Android i iOS. Aby uzyskać więcej informacji, zobacz [wpis techcommunity tutaj](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-general-availability-of-vulnerability-management/ba-p/3071663).

## <a name="upcoming-permission-changes-for-microsoft-defender-for-endpoint-running-android-11-or-later-nov-2021"></a>Nadchodzące zmiany uprawnień dla Ochrona punktu końcowego w usłudze Microsoft Defender uruchomionych Android 11 lub nowszych (listopad 2021 r.)

Kompilacja wydania: 1.0.3501.0301 Miesiąc wydania: listopad 2021 r. Ochrona punktu końcowego w usłudze Microsoft Defender wydała tę aktualizację wymaganą przez [firmę Google](https://developer.android.com/distribute/play-policies#APILevel30) do uaktualnienia do interfejsu API 30 Android. Ta zmiana spowoduje wyświetlenie monitu dla użytkowników poszukujących dostępu do [nowego uprawnienia magazynu](https://developer.android.com/training/data-storage/manage-all-files#all-files-access-google-play) dla urządzeń z systemem Android 11 lub nowszym. Użytkownicy będą musieli zaakceptować to nowe uprawnienie magazynu po zaktualizowaniu aplikacji Defender przy użyciu kompilacji wersji 1.0.3501.0301 lub nowszej. Zapewni to, że funkcja zabezpieczeń aplikacji usługi Defender for Endpoint będzie działać bez żadnych zakłóceń. Aby uzyskać więcej informacji, zapoznaj się z poniższymi sekcjami.

**Jak wpłynie to na organizację:** Te zmiany zostaną wprowadzone, jeśli używasz Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniach z systemem Android 11 lub nowszym i zaktualizowano usługę Defender for Endpoint w celu wydania kompilacji 1.0.3501.0301 lub nowszej.

> [!NOTE]
> Nie można skonfigurować nowych uprawnień magazynu przez administratora do automatycznego zatwierdzania za pośrednictwem Microsoft Endpoint Manager. Użytkownik będzie musiał podjąć działania w celu zapewnienia dostępu do tego uprawnienia.

- **Środowisko użytkownika:** Użytkownicy otrzymają powiadomienie wskazujące brakujące uprawnienia do zabezpieczeń aplikacji. Jeśli użytkownik odmówi tego uprawnienia, funkcja "Zabezpieczenia aplikacji" zostanie wyłączona na urządzeniu. Jeśli użytkownik nie zaakceptuje lub nie odmówi uprawnień, będzie nadal otrzymywać monit podczas odblokowywania urządzenia lub otwierania aplikacji, dopóki nie zostanie zatwierdzona.

> [!NOTE]
> Jeśli Twoja organizacja wyświetla podgląd funkcji "Ochrona przed naruszeniami" i jeśli nowe uprawnienia magazynu nie zostaną przyznane przez użytkownika w ciągu 7 dni od aktualizacji do najnowszej wersji, użytkownik może utracić dostęp do zasobów firmowych.

**Co należy zrobić, aby przygotować:**

Powiadom użytkowników i pomoc techniczną (w stosownych przypadkach), że użytkownicy będą musieli zaakceptować nowe uprawnienia po wyświetleniu monitu po zaktualizowaniu usługi Defender for Endpoint w celu skompilowania wersji 1.0.3501.0301 lub nowszej. Aby zaakceptować uprawnienia, użytkownicy powinni:

1. Naciśnij powiadomienie usługi Defender for Endpoint w aplikacji lub otwórz aplikację Defender for Endpoint. Użytkownicy zobaczą ekran z listą wymaganych uprawnień. Obok uprawnienia Storage brakuje zielonego znacznika wyboru.

2. Naciśnij **pozycję Rozpocznij**.

3. Naciśnij przełącznik **, aby zezwolić na dostęp do zarządzania wszystkimi plikami.**

4. Urządzenie jest teraz chronione.

  > [!NOTE]
  > To uprawnienie umożliwia Ochrona punktu końcowego w usłudze Microsoft Defender dostęp do magazynu na urządzeniu użytkownika, co pomaga wykrywać i usuwać złośliwe i niechciane aplikacje. Ochrona punktu końcowego w usłudze Microsoft Defender uzyskuje dostęp/skanuje tylko Android pliku pakietu aplikacji (apk). Na urządzeniach z profilem służbowym usługa Defender for Endpoint skanuje tylko pliki związane z pracą.
