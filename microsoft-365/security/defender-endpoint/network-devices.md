---
title: Odnajdowanie urządzeń sieciowych i zarządzanie lukami w zabezpieczeniach
description: Zalecenia dotyczące zabezpieczeń i wykrywanie luk są teraz dostępne dla systemów operacyjnych przełączników, routerów, kontrolerów WLAN i zapór.
keywords: urządzenia sieciowe, wykrywanie luk w zabezpieczeniach urządzeń sieciowych, systemy operacyjne przełączników, routerów, kontrolerów WLAN i zapór
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: levinec
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: f6092800de89ebfdeed35230b1ade296e0396a85
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468782"
---
# <a name="network-device-discovery-and-vulnerability-management"></a>Odnajdowanie urządzeń sieciowych i zarządzanie lukami w zabezpieczeniach

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Zagrożenia i zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

> [!NOTE]
> W [opublikowanym](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/network-device-discovery-and-vulnerability-assessments/ba-p/2267548) \(w blogu 04–13–2021 \) blogu odnajdowanie i ocenianie luk w zabezpieczeniach urządzeń sieciowych zawiera szczegółowe informacje na temat nowych funkcji odnajdowania urządzeń sieciowych w uchcie Defender for Endpoint. Ten artykuł zawiera omówienie wyzwania, w przypadku którym  zaprojektowano odnajdowanie urządzeń sieciowych, oraz szczegółowe informacje o rozpoczynaniu korzystania z tych nowych funkcji.

Funkcje odnajdowania sieci są dostępne w sekcji **Spis** urządzeń w portalu Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">sieci</a> i Microsoft 365 Defender sieci.

W każdym Ochrona punktu końcowego w usłudze Microsoft Defender będzie używane wyznaczony urządzenie do okresowego uwierzytelniania skanów wstępnie skonfigurowanych urządzeń sieciowych. Po odkrytiu funkcje łączności usługi Defender for Endpoint Zarządzanie zagrożeniami i lukami zintegrowanych przepływów pracy w celu zabezpieczenia przełączników, routerów, kontrolerów WLAN, zapór i bram VPN.

Gdy urządzenia sieciowe zostaną wykryte i sklasyfikowane, administratorzy zabezpieczeń będą mogli otrzymywać najnowsze zalecenia dotyczące zabezpieczeń oraz przeglądać niedawno wykryte luki w zabezpieczeniach na urządzeniach sieciowych wdrożonych w ich organizacjach.

## <a name="approach"></a>Podejście

Urządzenia sieciowe nie są zarządzane jako standardowe punkty końcowe, ponieważ program Defender for Endpoint nie ma wbudowanego czujnika w urządzenia sieciowe. Te typy urządzeń wymagają podejścia bez agenta, w którym skanowanie zdalne uzyska niezbędne informacje z urządzeń. W zależności od topologii i charakterystyk sieci jedno urządzenie lub kilka urządzeń podłączonych do programu Ochrona punktu końcowego w usłudze Microsoft Defender będzie przeprowadzać uwierzytelnione skany urządzeń sieciowych przy użyciu SNMP (tylko do odczytu).

Należy pamiętać o dwóch typach urządzeń:

- **Urządzenie do** oceniania: urządzenie, które jest już podłączone do skanowania urządzeń sieciowych.
- **Urządzenia sieciowe**: urządzenia sieciowe, które zamierzasz skanować i w które chcesz wychować.

### <a name="vulnerability-management-for-network-devices"></a>Zarządzanie lukami w zabezpieczeniach urządzeń sieciowych

Gdy urządzenia sieciowe zostaną wykryte i sklasyfikowane, administratorzy zabezpieczeń będą mogli otrzymywać najnowsze zalecenia dotyczące zabezpieczeń oraz przeglądać niedawno wykryte luki w zabezpieczeniach na urządzeniach sieciowych wdrożonych w ich organizacjach.

## <a name="operating-systems-that-are-supported"></a>Obsługiwane systemy operacyjne

Obsługiwane są obecnie następujące systemy operacyjne:

- Cisco iOS, iOS-XE, ROUTER-OS
- Juniper JUNOS
- HPE ArubaOS, oprogramowanie przełączania procurve
- Palo Alto Networks PAN-OS

Z czasem zostanie dodanych więcej dostawców sieci i systemu operacyjnego na podstawie danych zebranych z użycia klientów. Dlatego zachęcamy do skonfigurowania wszystkich urządzeń sieciowych, nawet jeśli nie są one wymienione na tej liście.

## <a name="how-to-get-started"></a>Jak rozpocząć

Pierwszym krokiem jest wybranie urządzenia, które będzie przeprowadzać uwierzytelnione skany sieci.

1. Wybierz usługę Defender for Endpoint na urządzeniu onboarded (kliencie lub serwerze), które ma połączenie sieciowe z portem zarządzania dla urządzeń sieciowych, które planujesz skanować.

2. Ruch SNMP między urządzeniem do oceny punktu końcowego programu Defender a docelowymi urządzeniami sieciowym musi być dozwolony (na przykład przez Zaporę).

3. Zdecyduj, które urządzenia sieciowe będą oceniane w przypadku luk (na przykład: przełącznik Cisco lub zapora Palo Alto Networks).

4. Upewnij się, że opcja SNMP tylko do odczytu jest włączona na wszystkich skonfigurowanych urządzeniach sieciowych, aby umożliwić programowi Defender for Endpoint assessment device wykonywanie zapytań na skonfigurowanych urządzeniach sieciowych. Funkcja "zapis SNMP" nie jest potrzebna do prawidłowego działania tej funkcji.

5. Uzyskaj adresy IP urządzeń sieciowych, które mają być skanowane (lub podsieci, w których te urządzenia są wdrożone).

6. Uzyskaj poświadczenia SNMP dla urządzeń sieciowych (na przykład: Community String, noAuthNoPriv, authNoPriv, authPriv). Podczas konfigurowania nowego zadania oceniania będzie wymagane podanie poświadczeń.

7. Konfiguracja klienta serwera proxy: Nie jest wymagana dodatkowa konfiguracja inna niż wymagania serwera proxy dla urządzenia końcowego programu Defender.

8. Aby umożliwić uwierzytelnienie skanera sieciowego i poprawne działanie, należy dodać następujące domeny/adresy URL:

    - login.windows.net
    - \*security.microsoft.com
    - login.microsoftonline.com
    - \*blob.core.windows.net/networkscannerstable/\*

    > [!NOTE]
    > Nie wszystkie adresy URL są określone na liście dozwolonych danych listy dozwolonych punktów końcowych usługi Defender for Endpoint.

## <a name="permissions"></a>Uprawnienia

Do skonfigurowania zadań oceniania jest wymagana następująca opcja uprawnień użytkownika: **Zarządzanie ustawieniami zabezpieczeń w uchcie programu Defender**. Aby znaleźć to uprawnienie, zobacz Role **Ustawienia** \> **.** Aby uzyskać więcej informacji, zobacz [Tworzenie ról w kontrolach dostępu opartych na rolach i zarządzanie nimi](user-roles.md).

## <a name="install-the-network-scanner"></a>Instalowanie skanera sieciowego

1. Przejdź do **Microsoft 365 oceny Ustawienia** \>  \> **punktów** \> **końcowych (w** obszarze **Oceny sieci**).
    1. W portalu Microsoft 365 Defender przejdź do strony Ustawienia > zadania oceny.

2. Pobierz skaner sieciowy i zainstaluj go na wskazanym urządzeniu do oceny punktu końcowego programu Defender.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/assessment-jobs-download-scanner.png" alt-text="Przycisk Pobierz skaner" lightbox="images/assessment-jobs-download-scanner.png":::

## <a name="network-scanner-installation--registration"></a>Instalacja skanera sieciowego & rejestracji

Proces logowania można ukończyć na wskazanym urządzeniu oceniania lub innym urządzeniu (na przykład na osobistym urządzeniu klienckim).

Aby ukończyć proces rejestracji skanera sieciowego:

1. Skopiuj adres URL widoczny w wierszu polecenia i użyj podanego kodu instalacyjnego, aby ukończyć proces rejestracji.

    > [!NOTE]
    > Może być konieczne zmiana ustawień wiersza polecenia, aby móc skopiować adres URL.

2. Wprowadź kod i zaloguj się przy użyciu konta Microsoft, które ma uprawnienie Defender for Endpoint o nazwie "Zarządzanie ustawieniami zabezpieczeń w programie Defender".

3. Po zakończeniu powinien zostać wyświetlony komunikat z potwierdzeniem zalogowania się.

## <a name="configure-a-new-assessment-job"></a>Konfigurowanie nowego zadania oceniania

Na stronie Zadania oceny w **programie Ustawienia** wybierz **pozycję Dodaj zadanie oceny sieci**. Postępuj zgodnie z procesem instalacji, aby wybrać urządzenia sieciowe do regularnego skanowania i dodania do spisu urządzeń.

Aby zapobiec duplikowaniu urządzeń w spisie urządzeń sieciowych, upewnij się, że każdy adres IP jest skonfigurowany tylko raz na wielu urządzeniach do oceny.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/assessment-jobs-add.png" alt-text="Przycisk Dodaj zadanie oceny sieci" lightbox="images/assessment-jobs-add.png":::

Dodawanie kroków zadania oceny sieci:

1. Wybierz nazwę zadania oceny i "urządzenie do oceny", na którym zainstalowano skaner sieciowy. To urządzenie będzie przeprowadzać okresowe uwierzytelnione skany.

2. Dodaj adresy IP docelowych urządzeń sieciowych do skanowania (lub podsieci, w których te urządzenia są wdrożone).

3. Dodaj wymagane poświadczenia SNMP dla docelowych urządzeń sieciowych.

4. Zapisz nowo skonfigurowane zadanie oceny sieci, aby rozpocząć okresowe skanowanie sieci.

### <a name="scan-and-add-network-devices"></a>Skanowanie i dodawanie urządzeń sieciowych

W trakcie procesu instalacji możesz wykonać skanowanie testowe w czasie rzeczywistym, aby sprawdzić, czy:

- Istnieje łączność między urządzeniem do oceny punktu końcowego programu Defender a skonfigurowanymi docelowymi urządzeniami sieciowym.
- Skonfigurowane poświadczenia SNMP są prawidłowe.

Każde urządzenie oceniające może obsługiwać do 1500 pomyślnie skanowanych adresów IP. Na przykład w przypadku skanowania 10 różnych podsieci, w których tylko 100 adresów IP zwraca pomyślne wyniki, będzie można przeskanować 1400 dodatkowych adresów IP z innych podsieci na tym samym urządzeniu testowym.

Jeśli do przeskanowania jest wiele zakresów adresów IP/podsieci, wyniki skanowania testowego będą się pojawiać po kilku minutach. Dostępne będzie skanowanie testowe dla maksymalnie 1024 adresów.

Po wyświetlniu wyników możesz wybrać urządzenia, które będą uwzględniane w okresowym skanowaniu. Jeśli pominiesz wyświetlanie wyników skanowania, wszystkie skonfigurowane adresy IP zostaną dodane do zadania oceny sieci (niezależnie od odpowiedzi urządzenia). Wyniki skanowania można również eksportować.

## <a name="device-inventory"></a>Spis urządzeń

Nowo wykryte urządzenia będą widoczne na nowej karcie **Urządzenia** sieciowe na **stronie spisu** urządzeń. Po dodaniu zadania oceniania może upłynie do dwóch godzin, dopóki urządzenia nie zostaną zaktualizowane.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/assessment-jobs-device-inventory.png" alt-text="Sekcja Urządzenia sieciowe w spisie urządzeń" lightbox="images/assessment-jobs-device-inventory.png":::

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="network-scanner-installation-has-failed"></a>Instalacja skanera sieciowego nie powiodła się

Upewnij się, że wymagane adresy URL zostały dodane do dozwolonych domen w ustawieniach zapory. Upewnij się też, że ustawienia serwera proxy zostały skonfigurowane zgodnie z opisem w tece Konfigurowanie [ustawień serwera proxy i łączności internetowej urządzenia](configure-proxy-internet.md).

### <a name="the-microsoftcomdevicelogin-web-page-did-not-show-up"></a>Strona Microsoft.com/devicelogin sieci Web nie była pokazywana

Upewnij się, że wymagane adresy URL zostały dodane do dozwolonych domen w zaporze. Upewnij się też, że ustawienia serwera proxy zostały skonfigurowane zgodnie z opisem w tece Konfigurowanie [ustawień serwera proxy i łączności internetowej urządzenia](configure-proxy-internet.md).

### <a name="network-devices-are-not-shown-in-the-device-inventory-after-several-hours"></a>Urządzenia sieciowe nie są wyświetlane w spisie urządzeń po kilku godzinach

Wyniki skanowania powinny zostać zaktualizowane kilka godzin po wykonaniu początkowego skanowania po ukończeniu konfiguracji zadania oceny.

Jeśli urządzenia nadal nie są wyświetlane, sprawdź, czy na Twoich urządzeniach oceniających jest uruchomiona usługa "MdatpNetworkService", na których zainstalowano skaner sieciowy, i wykonaj "Uruchom skanowanie" w odpowiedniej konfiguracji zadania oceny.

Jeśli po upływie 5 minut nadal nie otrzymasz wyników, uruchom ponownie usługę.

### <a name="devices-last-seen-time-is-longer-than-24-hours"></a>Urządzenia ostatnio widziane czas jest dłuższy niż 24 godziny

Sprawdź, czy skaner działa prawidłowo. Następnie przejdź do definicji skanowania i wybierz pozycję "Uruchom test". Sprawdź, jakie komunikaty o błędach są zwracane z odpowiednich adresów IP.

### <a name="required-threat-and-vulnerability-management-user-permission"></a>Wymagane Zarządzanie zagrożeniami i lukami użytkownika

Rejestracja zakończyła się komunikatem o błędzie: "Wygląda na to, że nie masz wystarczających uprawnień do dodawania nowego agenta. Wymagane uprawnienie to "Zarządzanie ustawieniami zabezpieczeń w u programie Defender".

Naciśnij dowolny klawisz, aby zamknąć.

Poproś administratora administrator systemu o przypisanie wymaganych uprawnień. Ewentualnie poproś innego odpowiedniego członka o pomoc w procesie logowania, udostępniając mu kod logowania i link.

### <a name="registration-process-fails-using-provided-link-in-the-command-line-in-registration-process"></a>Proces rejestracji kończy się niepowodzeniem przy użyciu podanego linku w wierszu polecenia w procesie rejestracji

Spróbuj użyć innej przeglądarki lub skopiować link logowania i kod do innego urządzenia.

### <a name="text-too-small-or-cant-copy-text-from-command-line"></a>Tekst jest za mały lub nie można skopiować tekstu z wiersza polecenia

Zmień ustawienia wiersza polecenia na urządzeniu, aby zezwolić na kopiowanie i zmienić rozmiar tekstu.

## <a name="related-articles"></a>Artykuły pokrewne

- [Spis urządzeń](machines-view-overview.md)
- [Konfigurowanie funkcji zaawansowanych](advanced-features.md)
