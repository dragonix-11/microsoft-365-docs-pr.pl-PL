---
title: Program Microsoft Defender dla punktu końcowego w systemie Android — informacje dotyczące prywatności
description: Mechanizmy kontroli prywatności, jak skonfigurować ustawienia zasad, które mają wpływ na prywatność, oraz informacje o danych diagnostycznych zbieranych w programie Microsoft Defender for Endpoint w systemie Android.
keywords: microsoft, defender, Microsoft Defender for Endpoint, android, privacy, diagnostic
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 6772539f4ca4ea819a0f8cd2a92a817fcea650f3
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2022
ms.locfileid: "62974005"
---
# <a name="microsoft-defender-for-endpoint-on-android---privacy-information"></a>Program Microsoft Defender dla punktu końcowego w systemie Android — informacje dotyczące prywatności

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Program Defender for Endpoint w systemie Android zbiera informacje z skonfigurowanych urządzeń z systemem Android i przechowuje je w tej samej dzierżawie, w której masz usługę Defender for Endpoint. Informacje te są zbierane w celu zapewnienia, że usługa Defender dla punktu końcowego systemu Android jest bezpieczna, aktualne i działa zgodnie z oczekiwaniami, oraz aby obsługiwać usługę.

Aby uzyskać więcej informacji na temat przechowywania danych, zobacz [Program Microsoft Defender for Endpoint data storage and privacy (Przechowywanie danych punktu końcowego i prywatność](data-storage-privacy.md)).

Zbierane są informacje w celu zapewnienia, że usługa Defender dla punktu końcowego systemu Android jest bezpieczna, aktualne i działa zgodnie z oczekiwaniami oraz aby obsługiwać usługę.

Aby uzyskać więcej informacji na temat najczęstszych pytań dotyczących prywatności dotyczących programu Microsoft Defender dla punktu końcowego na urządzeniach przenośnych z systemem Android i iOS, zobacz Program Microsoft Defender for Endpoint i Twoja prywatność na urządzeniach przenośnych z [systemami Android i iOS](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-and-your-privacy-on-android-and-ios-mobile-devices-4109bc54-8ec5-4433-9c33-d359b75ac22a).

## <a name="required-data"></a>Wymagane dane

Wymagane dane składają się z danych niezbędnych do tego, aby program Defender dla punktu końcowego systemu Android działał zgodnie z oczekiwaniami. Te dane są istotne dla działania usługi i mogą obejmować dane dotyczące użytkownika końcowego, organizacji, urządzenia i aplikacji. Poniżej podano listę typów zbieranych danych:

### <a name="app-information"></a>Informacje o aplikacji

Informacje o **złośliwych pakietach** aplikacji dla systemu Android (A APKs) na urządzeniu, takie jak

- Zainstaluj źródło
- Storage lokalizacji (ścieżka pliku)
- Godzina instalacji, rozmiar pliku OIM i uprawnień

Dla urządzeń z systemem Android Enterprise w pełni zarządzanych — informacje o pakietach aplikacji systemu Android zainstalowanych na urządzeniu, w tym

- Nazwa i nazwa pakietu aplikacji
- Numer wersji aplikacji
- Nazwa dostawcy

Dla systemu Android Enterprise z profilem służbowym — informacje o pakietach aplikacji systemu Android zainstalowanych na profilu służbowym urządzenia, w tym

- Nazwa i nazwa pakietu aplikacji
- Numer wersji aplikacji
- Nazwa dostawcy

*Twoja organizacja może także skonfigurować usługę Defender for Endpoint w celu wysyłania informacji o wszystkich aplikacjach zainstalowanych na urządzeniu. Domyślnie te informacje nie są wysyłane do Twojej organizacji.*


### <a name="web-page--network-information"></a>Strona sieci Web / Informacje o sieci

- Pełny adres URL witryny sieci Web tylko w przypadku wykrycia i zablokowania złośliwego połączenia lub strony internetowej.
- Informacje o połączeniu
- Typ protokołu (taki jak HTTP, HTTPS itp.)

### <a name="device-and-account-information"></a>Informacje o urządzeniu i koncie

- Informacje o urządzeniu, takie jak data &, wersja systemu Android, model OEM, informacje o procesorze i identyfikator urządzenia.
- Identyfikator urządzenia jest jednym z poniższych:
  - Wi-Fi adres MAC karty sieciOwej
  - [Identyfikator Systemu Android](https://developer.android.com/reference/android/provider/Settings.Secure#ANDROID_ID) (wygenerowany przez system Android przy pierwszym uruchomieniu urządzenia).
  - Losowo generowany identyfikator unikatowy identyfikator globalny (GUID).

- Informacje o dzierżawie, urządzeniu i użytkowniku
  - Azure Active Directory (AD) Identyfikator urządzenia i Identyfikator użytkownika platformy Azure: jednoznacznie identyfikuje urządzenie, odpowiednio użytkownika w usłudze Azure Active Directory.
  - Identyfikator dzierżawy platformy Azure: identyfikator GUID identyfikujący Twoją organizację w ramach Azure Active Directory.
  - Identyfikator organizacji programu Microsoft Defender for Endpoint: unikatowy identyfikator skojarzony z przedsiębiorstwem, do którego należy urządzenie. Umożliwia firmie Microsoft zidentyfikowanie, czy problemy wpływają na wybór zestawu przedsiębiorstw i na ile przedsiębiorstw ma to wpływ.
  - Główna nazwa użytkownika: identyfikator poczty e-mail użytkownika

### <a name="product-and-service-usage-data"></a>Dane dotyczące użycia produktów i usług

Poniższe informacje są zbierane tylko dla aplikacji Microsoft Defender for Endpoint zainstalowanej na urządzeniu. 

- Informacje o pakiecie aplikacji, w tym nazwa, wersja i stan uaktualniania aplikacji.
- Akcje wykonywane w aplikacji.
- Informacje dotyczące wykrywania zagrożeń, takie jak nazwa zagrożenia, kategoria itp.
- Dzienniki raportów o awariach wygenerowane przez system Android.

## <a name="optional-data"></a>Dane opcjonalne

Opcjonalne dane obejmują dane diagnostyczne i dane zwrotne. Opcjonalne dane diagnostyczne to dodatkowe dane, które ułatwiają ulepszanie produktów i zapewniają rozszerzone informacje pomagające wykrywać, diagnozować i naprawiać problemy. Opcjonalne dane diagnostyczne obejmują:

- Użycie aplikacji, procesora CPU i sieci.
- Stan urządzenia z perspektywy aplikacji, w tym stan skanowania, chronometraż skanowania, udzielone uprawnienia aplikacji i stan uaktualnienia.
- Funkcje skonfigurowane przez administratora.
- Podstawowe informacje o przeglądarkach na urządzeniu.

**Dane opinii** są zbierane za pośrednictwem opinii w aplikacji dostarczonej przez użytkownika

- Adres e-mail użytkownika, jeśli użytkownik zdecyduje się go podać.
- Typ opinii (uśmiech, śmieszny, pomysł) i wszelkie komentarze przesłane przez użytkownika.
