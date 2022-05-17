---
title: Odnajdywanie i zarządzanie lukami w zabezpieczeniach urządzeń sieciowych
description: Zalecenia dotyczące zabezpieczeń i wykrywanie luk w zabezpieczeniach są teraz dostępne dla systemów operacyjnych przełączników, routerów, kontrolerów sieci WLAN i zapór.
keywords: urządzenia sieciowe, wykrywanie luk w zabezpieczeniach urządzeń sieciowych, systemy operacyjne przełączników, routerów, kontrolerów sieci WLAN i zapór
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
ms.openlocfilehash: f5c2f1c7c73f150c02192fa7e275a07b12c64c79
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438383"
---
# <a name="network-device-discovery-and-vulnerability-management"></a>Odnajdywanie i zarządzanie lukami w zabezpieczeniach urządzeń sieciowych

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Zagrożenia i zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

> [!NOTE]
> Blog \([Dotyczący odnajdywania urządzeń sieciowych i ocen luk w zabezpieczeniach](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/network-device-discovery-and-vulnerability-assessments/ba-p/2267548) opublikowany w wersji 04-13-2021\) zapewnia wgląd w nowe możliwości **odnajdywania urządzeń sieciowych** w usłudze Defender for Endpoint. Ten artykuł zawiera omówienie wyzwania, z jakim jest przeznaczone do rozwiązania **odnajdywanie urządzeń sieciowych** , oraz szczegółowe informacje o tym, jak rozpocząć korzystanie z tych nowych możliwości.

Możliwości odnajdywania sieci są dostępne w sekcji **Spis urządzeń** w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> i konsolach Microsoft 365 Defender.

Wyznaczone urządzenie Ochrona punktu końcowego w usłudze Microsoft Defender będzie używane w każdym segmencie sieci do przeprowadzania okresowych uwierzytelnionych skanów wstępnie skonfigurowanych urządzeń sieciowych. Po odnalezieniu funkcje Zarządzanie zagrożeniami i lukami usługi Defender for Endpoint zapewniają zintegrowane przepływy pracy w celu zabezpieczenia odnalezionych przełączników, routerów, kontrolerów sieci WLAN, zapór i bram sieci VPN.

Po odnalezieniu i sklasyfikowaniu urządzeń sieciowych administratorzy zabezpieczeń będą mogli otrzymywać najnowsze zalecenia dotyczące zabezpieczeń i przeglądać niedawno wykryte luki w zabezpieczeniach na urządzeniach sieciowych wdrożonych w ich organizacjach.

## <a name="approach"></a>Podejście

Urządzenia sieciowe nie są zarządzane jako standardowe punkty końcowe, ponieważ usługa Defender dla punktu końcowego nie ma czujnika wbudowanego w same urządzenia sieciowe. Tego typu urządzenia wymagają podejścia bez agenta, w którym zdalne skanowanie będzie uzyskiwać niezbędne informacje z urządzeń. W zależności od topologii i charakterystyki sieci pojedyncze urządzenie lub kilka urządzeń dołączonych do Ochrona punktu końcowego w usłudze Microsoft Defender przeprowadzi uwierzytelnione skanowanie urządzeń sieciowych przy użyciu protokołu SNMP (tylko do odczytu).

Należy pamiętać o dwóch typach urządzeń:

- **Urządzenie do oceny**: urządzenie, które jest już dołączone, którego użyjesz do skanowania urządzeń sieciowych.
- **Urządzenia sieciowe**: urządzenia sieciowe, które mają zostać zeskanowane i dołączone.

### <a name="vulnerability-management-for-network-devices"></a>Zarządzanie lukami w zabezpieczeniach dla urządzeń sieciowych

Po odnalezieniu i sklasyfikowaniu urządzeń sieciowych administratorzy zabezpieczeń będą mogli otrzymywać najnowsze zalecenia dotyczące zabezpieczeń i przeglądać niedawno wykryte luki w zabezpieczeniach na urządzeniach sieciowych wdrożonych w ich organizacjach.

## <a name="operating-systems-that-are-supported"></a>Obsługiwane systemy operacyjne

Obecnie obsługiwane są następujące systemy operacyjne:

- Cisco IOS, IOS-XE, NX-OS
- Juniper JUNOS
- HPE ArubaOS, oprogramowanie przełącznika nabytego
- Palo Alto Networks PAN-OS

Więcej dostawców sieci i systemu operacyjnego zostanie dodanych w miarę upływu czasu na podstawie danych zebranych z użycia klienta. W związku z tym zachęcamy do skonfigurowania wszystkich urządzeń sieciowych, nawet jeśli nie zostaną one określone na tej liście.

## <a name="how-to-get-started"></a>Jak rozpocząć pracę

Pierwszym krokiem jest wybranie urządzenia, które wykona uwierzytelnione skanowanie sieci.

1. Zdecyduj o urządzeniu dołączonym do usługi Defender for Endpoint (kliencie lub serwerze), które ma połączenie sieciowe z portem zarządzania dla urządzeń sieciowych, które planujesz skanować.

2. Ruch SNMP między urządzeniem do oceny punktu końcowego usługi Defender i docelowymi urządzeniami sieciowymi musi być dozwolony (na przykład przez zaporę).

3. Zdecyduj, które urządzenia sieciowe będą oceniane pod kątem luk w zabezpieczeniach (na przykład przełącznik Cisco lub zapora Palo Alto Networks).

4. Upewnij się, że protokół SNMP tylko do odczytu jest włączony na wszystkich skonfigurowanych urządzeniach sieciowych, aby umożliwić urządzeniu do oceny punktu końcowego usługi Defender wykonywanie zapytań względem skonfigurowanych urządzeń sieciowych. "Zapis SNMP" nie jest potrzebny do prawidłowego działania tej funkcji.

5. Uzyskaj adresy IP urządzeń sieciowych do skanowania (lub podsieci, w których te urządzenia są wdrażane).

6. Uzyskaj poświadczenia SNMP urządzeń sieciowych (na przykład: Community String, noAuthNoPriv, authNoPriv, authPriv). Podczas konfigurowania nowego zadania oceny wymagane będzie podanie poświadczeń.

7. Konfiguracja klienta serwera proxy: nie jest wymagana żadna dodatkowa konfiguracja poza wymaganiami serwera proxy urządzenia usługi Defender for Endpoint.

8. Aby umożliwić poprawne uwierzytelnianie skanera sieciowego, należy dodać następujące domeny/adresy URL:

    - login.windows.net
    - \*.security.microsoft.com
    - login.microsoftonline.com
    - \*.blob.core.windows.net/networkscannerstable/\*

    > [!NOTE]
    > Nie wszystkie adresy URL są określone na udokumentowanej liście dozwolonych zbierania danych w usłudze Defender for Endpoint.

## <a name="permissions"></a>Uprawnienia

Aby skonfigurować zadania oceny, wymagana jest następująca opcja uprawnień użytkownika: **Zarządzanie ustawieniami zabezpieczeń w usłudze Defender**. Uprawnienie można znaleźć, przechodząc do **pozycji Role Ustawienia** \> **.** Aby uzyskać więcej informacji, zobacz [Tworzenie ról i zarządzanie nimi na potrzeby kontroli dostępu opartej na rolach](user-roles.md).

## <a name="install-the-network-scanner"></a>Instalowanie skanera sieci

1. Przejdź do **obszaru Microsoft 365** **zadania oceny** **punktów końcowych** \> **Ustawienia** \> zabezpieczeń \> (w obszarze **oceny sieci**).
    1. W portalu Microsoft 365 Defender przejdź do strony zadania oceny Ustawienia >.

2. Pobierz skaner sieciowy i zainstaluj go na wyznaczonym urządzeniu do oceny punktu końcowego usługi Defender.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/assessment-jobs-download-scanner.png" alt-text="Przycisk Pobierz skaner" lightbox="images/assessment-jobs-download-scanner.png":::

## <a name="network-scanner-installation--registration"></a>Rejestracja & instalacji skanera sieci

Proces logowania można ukończyć na wyznaczonym urządzeniu do oceny lub na dowolnym innym urządzeniu (na przykład osobistym urządzeniu klienckim).

> [!NOTE]
> Zarówno konto, za pomocą którego loguje się użytkownik, jak i urządzenie używane do ukończenia procesu logowania, musi znajdować się w tej samej dzierżawie, w której urządzenie jest dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender.

Aby ukończyć proces rejestracji skanera sieciowego:

1. Skopiuj adres URL wyświetlany w wierszu polecenia i użyj dostarczonego kodu instalacyjnego, aby ukończyć proces rejestracji.

    > [!NOTE]
    > Aby móc skopiować adres URL, może być konieczna zmiana ustawień wiersza polecenia.

2. Wprowadź kod i zaloguj się przy użyciu konta Microsoft z uprawnieniem Defender for Endpoint o nazwie "Zarządzanie ustawieniami zabezpieczeń w usłudze Defender".

3. Po zakończeniu powinien zostać wyświetlony komunikat potwierdzający zalogowanie.

## <a name="configure-a-new-assessment-job"></a>Konfigurowanie nowego zadania oceny

Na stronie Zadania oceny w **Ustawienia** wybierz pozycję **Dodaj zadanie oceny sieci**. Postępuj zgodnie z procesem konfigurowania, aby wybrać urządzenia sieciowe, które mają być regularnie skanowane i dodawane do spisu urządzeń.

Aby zapobiec duplikacji urządzeń w spisie urządzeń sieciowych, upewnij się, że każdy adres IP jest skonfigurowany tylko raz na wielu urządzeniach do oceny.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/assessment-jobs-add.png" alt-text="Przycisk Dodaj zadanie oceny sieci" lightbox="images/assessment-jobs-add.png":::

Dodawanie kroków zadania oceny sieci:

1. Wybierz nazwę zadania oceny i urządzenie do oceny, na którym zainstalowano skaner sieciowy. To urządzenie będzie przeprowadzać okresowe uwierzytelnione skanowanie.

2. Dodaj adresy IP docelowych urządzeń sieciowych do skanowania (lub podsieci, w których te urządzenia są wdrażane).

3. Dodaj wymagane poświadczenia SNMP docelowych urządzeń sieciowych.

4. Zapisz nowo skonfigurowane zadanie oceny sieci, aby rozpocząć okresowe skanowanie sieci.

### <a name="scan-and-add-network-devices"></a>Skanowanie i dodawanie urządzeń sieciowych

Podczas procesu konfiguracji można wykonać jednorazowe skanowanie testowe, aby sprawdzić, czy:

- Istnieje łączność między urządzeniem do oceny punktu końcowego usługi Defender i skonfigurowanymi docelowymi urządzeniami sieciowymi.
- Skonfigurowane poświadczenia SNMP są poprawne.

Każde urządzenie do oceny może obsługiwać do 1500 pomyślnego skanowania adresów IP. Jeśli na przykład przeskanujesz 10 różnych podsieci, w których tylko 100 adresów IP zwróci pomyślne wyniki, będzie można przeskanować 1400 dodatkowych adresów IP z innych podsieci na tym samym urządzeniu do oceny.

Jeśli do skanowania jest wiele zakresów adresów IP/podsieci, wyświetlenie wyników skanowania testowego potrwa kilka minut. Skanowanie testowe będzie dostępne dla maksymalnie 1024 adresów.

Po wyświetleniu wyników możesz wybrać urządzenia, które zostaną uwzględnione w okresowym skanowaniu. Jeśli pominiesz wyświetlanie wyników skanowania, wszystkie skonfigurowane adresy IP zostaną dodane do zadania oceny sieci (niezależnie od odpowiedzi urządzenia). Wyniki skanowania można również wyeksportować.

## <a name="device-inventory"></a>Spisz urządzeń

Nowo odnalezione urządzenia będą wyświetlane na nowej karcie **Urządzenia sieciowe** na stronie **Spis urządzeń** . Dodanie zadania oceny może potrwać do dwóch godzin, dopóki urządzenia nie zostaną zaktualizowane.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/assessment-jobs-device-inventory.png" alt-text="Sekcja Urządzenia sieciowe w spisie urządzeń" lightbox="images/assessment-jobs-device-inventory.png":::

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="network-scanner-installation-has-failed"></a>Instalacja skanera sieci nie powiodła się

Sprawdź, czy wymagane adresy URL są dodawane do dozwolonych domen w ustawieniach zapory. Upewnij się również, że ustawienia serwera proxy są skonfigurowane zgodnie z opisem w [temacie Konfigurowanie ustawień serwera proxy urządzenia i łączności z Internetem](configure-proxy-internet.md).

### <a name="the-microsoftcomdevicelogin-web-page-did-not-show-up"></a>Strona sieci Web Microsoft.com/devicelogin nie została wyświetlona

Sprawdź, czy wymagane adresy URL są dodawane do dozwolonych domen w zaporze. Upewnij się również, że ustawienia serwera proxy są skonfigurowane zgodnie z opisem w [temacie Konfigurowanie ustawień serwera proxy urządzenia i łączności z Internetem](configure-proxy-internet.md).

### <a name="network-devices-are-not-shown-in-the-device-inventory-after-several-hours"></a>Urządzenia sieciowe nie są wyświetlane w spisie urządzeń po kilku godzinach

Wyniki skanowania powinny zostać zaktualizowane kilka godzin po początkowym skanowaniu, które miało miejsce po zakończeniu konfiguracji zadania oceny.

Jeśli urządzenia nadal nie są wyświetlane, sprawdź, czy usługa "MdatpNetworkScanService" jest uruchomiona na urządzeniach do oceny, na których zainstalowano skaner sieciowy, i wykonaj polecenie "Uruchom skanowanie" w odpowiedniej konfiguracji zadania oceny.

Jeśli nadal nie uzyskasz wyników po 5 minutach, uruchom ponownie usługę.

### <a name="devices-last-seen-time-is-longer-than-24-hours"></a>Czas ostatniego wyświetleń urządzeń trwa dłużej niż 24 godziny

Sprawdź, czy skaner działa prawidłowo. Następnie przejdź do definicji skanowania i wybierz pozycję "Uruchom test". Sprawdź, jakie komunikaty o błędach są zwracane z odpowiednich adresów IP.

### <a name="required-threat-and-vulnerability-management-user-permission"></a>Wymagane uprawnienie użytkownika Zarządzanie zagrożeniami i lukami

Rejestracja zakończyła się błędem: "Wygląda na to, że nie masz wystarczających uprawnień do dodawania nowego agenta. Wymagane uprawnienie to "Zarządzanie ustawieniami zabezpieczeń w usłudze Defender".

Naciśnij dowolny klucz, aby zakończyć pracę.

Poproś administratora systemu o przypisanie ci wymaganych uprawnień. Alternatywnie poproś innego odpowiedniego członka o pomoc w procesie logowania, podając mu kod logowania i link.

### <a name="registration-process-fails-using-provided-link-in-the-command-line-in-registration-process"></a>Proces rejestracji kończy się niepowodzeniem przy użyciu podanej linku w wierszu polecenia w procesie rejestracji

Wypróbuj inną przeglądarkę lub skopiuj link logowania i kod na inne urządzenie.

### <a name="text-too-small-or-cant-copy-text-from-command-line"></a>Tekst jest zbyt mały lub nie można skopiować tekstu z wiersza polecenia

Zmień ustawienia wiersza polecenia na urządzeniu, aby umożliwić kopiowanie i zmienianie rozmiaru tekstu.

## <a name="related-articles"></a>Powiązane artykuły:

- [Spisz urządzeń](machines-view-overview.md)
- [Konfiguruj funkcje zaawansowane](advanced-features.md)
