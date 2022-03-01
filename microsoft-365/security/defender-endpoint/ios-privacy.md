---
title: Informacje dotyczące prywatności — Program Microsoft Defender for Endpoint w systemie iOS
ms.reviewer: ''
description: W tym artykule opisano informacje dotyczące prywatności dla programu Microsoft Defender for Endpoint w systemie iOS
keywords: microsoft, defender, Microsoft Defender for Endpoint, ios, policy, overview
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 4fc5d4fb51170a70edc8664d5ccba0943b93353d
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/29/2021
ms.locfileid: "62996778"
---
# <a name="privacy-information---microsoft-defender-for-endpoint-on-ios"></a>Informacje dotyczące prywatności — Program Microsoft Defender for Endpoint w systemie iOS

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

> [!NOTE]
> Usługa Defender for Endpoint w systemie iOS korzysta z połączenia VPN w celu zapewnienia funkcji ochrony sieci Web. Nie jest to zwykły vpn, który jest lokalnym lub samopętlowym siecią VPN, który nie przejmuje ruchu poza urządzeniem. **Firma Microsoft lub Twoja organizacja nie widzi Twojej aktywności przeglądania.**

Program Defender for Endpoint w systemie iOS zbiera informacje ze skonfigurowanych urządzeń z systemem iOS i przechowuje je w tej samej dzierżawie, w której masz usługę Defender for Endpoint. Informacje te są zbierane w celu zapewnienia, że usługa Defender dla punktu końcowego w systemie iOS jest bezpieczna, aktualne i działa zgodnie z oczekiwaniami, oraz aby obsługiwać usługę.

Aby uzyskać więcej informacji na temat przechowywania danych, zobacz [Program Microsoft Defender for Endpoint data storage and privacy (Przechowywanie danych punktu końcowego i prywatność](data-storage-privacy.md)).

Aby uzyskać więcej informacji na temat najczęstszych pytań dotyczących prywatności dotyczących programu Microsoft Defender dla punktu końcowego na urządzeniach przenośnych z systemem Android i iOS, zobacz Program Microsoft Defender for Endpoint i Twoja prywatność na urządzeniach przenośnych z [systemami Android i iOS](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-and-your-privacy-on-android-and-ios-mobile-devices-4109bc54-8ec5-4433-9c33-d359b75ac22a).

## <a name="required-data"></a>Wymagane dane

Wymagane dane składają się z danych, które są niezbędne do tego, aby program Defender dla punktu końcowego w systemie iOS działał zgodnie z oczekiwaniami. Te dane są istotne dla działania usługi i mogą obejmować dane dotyczące użytkownika końcowego, organizacji, urządzenia i aplikacji.

Poniżej znajduje się lista typów zbieranych danych:

### <a name="web-page-or-network-information"></a>Strona sieci Web lub informacje o sieci

- Nazwa domeny i adres IP witryny sieci Web tylko w przypadku wykrycia złośliwego połączenia lub strony internetowej.

### <a name="device-and-account-information"></a>Informacje o urządzeniu i koncie

- Informacje o urządzeniu, takie jak &, wersja systemu iOS, informacje o procesorze i identyfikator urządzenia, gdzie Identyfikator urządzenia to jeden z następujących identyfikatorów:
  - Wi-Fi adres MAC karty sieciOwej
  - Losowo generowany identyfikator unikatowy identyfikator globalny (GUID)
- Informacje o dzierżawie, urządzeniu i użytkowniku
  - Azure Active Directory (AD) Identyfikator urządzenia i Identyfikator użytkownika platformy Azure — jednoznacznie identyfikuje urządzenie odpowiednio dla użytkownika w usłudze Azure Active Directory.
  - Identyfikator dzierżawy platformy Azure — identyfikator GUID identyfikujący Twoją organizację w ramach Azure Active Directory.
  - Identyfikator organizacji programu Microsoft Defender for Endpoint — unikatowy identyfikator skojarzony z przedsiębiorstwem, do którego należy urządzenie. Umożliwia firmie Microsoft zidentyfikowanie, czy występują problemy dotyczące wybranego zestawu przedsiębiorstw i liczby przedsiębiorstw, na które ma to wpływ.
  - Główna nazwa użytkownika — identyfikator poczty e-mail użytkownika.

### <a name="product-and-service-usage-data"></a>Dane dotyczące użycia produktów i usług

Poniższe informacje są zbierane tylko dla aplikacji Microsoft Defender for Endpoint zainstalowanej na urządzeniu.

- Informacje o pakiecie aplikacji, w tym nazwa, wersja i stan uaktualniania aplikacji.
- Akcje wykonywane w aplikacji.
- Dzienniki raportów o awariach wygenerowane przez system iOS.
- Dane dotyczące użycia pamięci.

## <a name="optional-data"></a>Dane opcjonalne

Opcjonalne dane obejmują dane diagnostyczne i dane zwrotne z klienta. Opcjonalne dane diagnostyczne to dodatkowe dane, które ułatwiają ulepszanie produktów i zapewniają rozszerzone informacje pomagające wykrywać, diagnozować i naprawiać problemy. Te dane są tylko dla celów diagnostycznych i nie są wymagane dla samej usługi.

Opcjonalne dane diagnostyczne obejmują:

- App, CPU i network usage for Defender for Endpoint.
- Funkcje skonfigurowane przez administratora dla usługi Defender for Endpoint.

Dane opinii są zbierane za pośrednictwem opinii w aplikacji dostarczonej przez użytkownika.

- Adres e-mail użytkownika, jeśli użytkownik zdecyduje się go podać.
- Typ opinii (uśmiech, śmieszny, pomysł) i wszelkie komentarze przesłane przez użytkownika.

Aby uzyskać więcej informacji, zobacz [Więcej informacji na temat prywatności](https://aka.ms/mdatpiosprivacystatement).
