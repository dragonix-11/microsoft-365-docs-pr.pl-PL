---
title: Ręczna rejestracja
description: Zarejestruj urządzenia, które mają być zarządzane przez Microsoft Managed Desktop
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: aaa1446cbb1ffdc20b023f568a7fd41d6cf01848
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704960"
---
# <a name="manual-registration"></a>Ręczna rejestracja

Microsoft Managed Desktop może pracować z zupełnie nowymi urządzeniami lub możesz ponownie używać urządzeń, które być może już posiadasz. W przypadku ponownego użycia urządzeń należy je ponownie zaimportować. Urządzenia można rejestrować w Microsoft Managed Desktop w portalu Microsoft Endpoint Manager sieci.

> [!NOTE]
> Współpracujesz z partnerem w celu uzyskania urządzeń? Jeśli tak, nie musisz się martwić o uzyskanie skrótów sprzętowych. zajmie się tym za Ciebie. Upewnij się, że Partner nawiązy relację z Tobem w [Centrum partnerskim](https://partner.microsoft.com/dashboard). Partner może dowiedzieć się więcej w [Centrum partnerskim w pomocy](/partner-center/request-a-relationship-with-a-customer). <br><br>Po nawiązycej relacji partner po prostu zarejestruje urządzenia w Twoim imieniu — nie będą od Ciebie wymagane żadne dalsze działania. Jeśli chcesz wyświetlić szczegółowe informacje lub partner ma pytania, zobacz Rejestracja [partnera](partner-registration.md). Po zarejestrowaniu urządzeń możesz kontynuować sprawdzanie obrazu i [dostarczanie tych urządzeń](#deliver-the-device) użytkownikom.[](#check-the-image)

## <a name="prepare-to-register-brand-new-devices"></a>Przygotuj się do zarejestrowania zupełnie nowych urządzeń

Gdy będziesz mieć pod ręką nowe urządzenia, wykonaj następujące czynności:

1. [Uzyskaj skrót sprzętowy dla każdego urządzenia.](#obtain-the-hardware-hash)
2. [Scalanie danych skrótu](#merge-hash-data).
3. [Zarejestruj urządzenia w Microsoft Managed Desktop](#register-devices-by-using-the-admin-portal).
4. [Sprawdź dwukrotnie, czy obraz jest poprawny.](#check-the-image)
5. [Dostarczyć urządzenie](#deliver-the-device).

### <a name="obtain-the-hardware-hash"></a>Uzyskiwanie skrótu sprzętowego

Microsoft Managed Desktop identyfikuje każde urządzenie jednoznacznie, odwołując się do jego skrótu sprzętowego. Dostępne są trzy opcje uzyskiwania tych informacji.

**Aby uzyskać skrót sprzętowy:**

- Poproś dostawcę OEM o plik rejestracji rozwiązania AutoPilot, który będzie zawierał skróty sprzętowe.
- Uruchom skrypt [Windows PowerShell na](#powershell-script-method) każdym urządzeniu i zbierz wyniki w pliku.
- Uruchom każde urządzenie, ale nie przejmij wszystkich Windows konfiguracji i zbierz [skróty na wymiennych dyskach flash](#flash-drive-method).

#### <a name="powershell-script-method"></a>Metoda skryptu programu PowerShell

Skryptu programu [Get-WindowsAutoPilotInfo.ps1](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) PowerShell można użyć w witrynie galerii programu PowerShell w sieci Web. Aby uzyskać więcej informacji na temat identyfikacji urządzenia i skrótu sprzętowego, zobacz [Dodawanie urządzeń do rozwiązania Windows Autopilot](/mem/autopilot/add-devices#device-identification).

**Aby użyć metody skryptu programu PowerShell:**

1. Otwórz monit programu PowerShell z uprawnieniami administracyjnymi.
2. Uruchom `Install-Script -Name Get-WindowsAutoPilotInfo`.
3. Uruchom `powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`.
4. Uruchom `powershell -ExecutionPolicy restricted` ten program, aby uniemożliwić uruchamianie kolejnych nieograniczone skryptów.

#### <a name="flash-drive-method"></a>Metoda dysku flash

**Aby użyć metody dysku flash:**

1. Na urządzeniu innym niż to, które rejestrujesz, włóż dysk USB.
2. Otwórz monit programu PowerShell z uprawnieniami administracyjnymi.
3. Uruchom `Save-Script -Name Get-WindowsAutoPilotInfo -Path <pathToUsb>`
4. Włącz urządzenie, które rejestrujesz, ale *nie uruchamiaj procesu konfiguracji*. Jeśli środowisko konfiguracji zostanie przypadkowo uruchomić, będzie trzeba zresetować lub ponownie zaimportować urządzenie.
5. Włóż dysk USB, a następnie naciśnij klawisze SHIFT + F10.
6. Otwórz monit programu PowerShell z uprawnieniami administracyjnymi, a następnie uruchom .`cd <pathToUsb>`
7. Uruchom `Set-ExecutionPolicy -ExecutionPolicy Unrestricted`
8. Uruchom `.\Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`
9. Usuń dysk USB, a następnie wyłącz urządzenie, uruchamiając `shutdown -s -t 0`

> [!IMPORTANT]
> Nie wsaduj ponownie urządzenia, które zarejestrujesz, dopóki nie zakończysz rejestracji dla tego urządzenia.

### <a name="merge-hash-data"></a>Scalanie danych z skrótami

Aby ukończyć rejestrację, dane z plików CSV muszą być połączone w jeden plik. Oto przykładowy skrypt programu PowerShell ułatwiający wykonywanie tych pracy:

`Import-CSV -Path (Get-ChildItem -Filter *.csv) | ConvertTo-Csv -NoTypeInformation | % {$_.Replace('"', '')} | Out-File .\aggregatedDevices.csv`

> [!NOTE]
> Dodatkowe kolumny nie są obsługiwane. Oferty nie są obsługiwane. Można używać tylko plików tekstowych w formacie ANSI (nie unicode). W nagłówkach jest wielkość liter. Edytowanie pliku w Excel zapisaniu go jako pliku CSV nie spowoduje wygenerowania pliku do użytku z powodu tych wymagań. Pamiętaj, aby zachować wszystkie zera wiodące w numerach seryjnych urządzeń.

### <a name="register-devices-by-using-the-admin-portal"></a>Rejestrowanie urządzeń za pomocą portalu administracyjnego

W [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) nawigacji wybierz **pozycję Urządzenia** w lewym okienku nawigacji. W sekcji Microsoft Managed Desktop wybierz pozycję **Urządzenia**. W obszarze Microsoft Managed Desktop urządzenia wybierz pozycję **+ Zarejestruj** urządzenia, co spowoduje otwarcie wysuwanych aplikacji w celu zarejestrowania nowych urządzeń.

<!-- [![Fly-in after selecting Register devices, listing devices with columns for assigned users, serial number, status, last-seen date, and age.](../../media/new-registration-ui.png)](../../media/new-registration-ui.png) -->

<!--Registering any existing devices with Managed Desktop will completely re-image them; make sure you've backed up any important data prior to starting the registration process.-->

**Aby zarejestrować urządzenia za pomocą portalu administracyjnego:**

1. W **przesyłaniu** pliku podaj ścieżkę do utworzonego wcześniej pliku CSV.
2. Wybierz [profil urządzenia](../service-description/profiles.md) z menu rozwijanego.
3. Wybierz **pozycję Zarejestruj urządzenia**. System doda urządzenia do listy urządzeń na urządzeniach **oznaczonych** jako " **Oczekiwanie na rejestrację"**. Rejestracja zwykle trwa mniej niż 10 minut, a po pomyślnym uruchomieniu urządzenie będzie wyświetlane jako  Gotowe dla użytkownika, co oznacza, że jest gotowe i oczekuje na rozpoczęcie korzystania przez użytkownika.

> [!NOTE]
> Jeśli ręcznie zmienisz członkostwo w Azure Active Directory (AAD) na urządzeniu, zostanie ono automatycznie ponownie przypisana do grupy dla jej profilu urządzenia i usunięta ze wszystkich grup powodującego konflikt.

Możesz monitorować postęp rejestracji urządzeń na stronie głównej. Raporty mogą obejmować:

| Stan | Opis |
| -----|-----|
| Oczekiwanie na rejestrację | Rejestracja nie została jeszcze ukończona. Sprawdź ponownie później. |
| Rejestracja nie powiodła się | Rejestracji nie można ukończyć. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z rejestracją urządzenia](#troubleshooting-device-registration). |
| Gotowe dla użytkownika | Rejestracja powiodła się. Urządzenie jest teraz gotowe do dostarczenia do użytkownika. Microsoft Managed Desktop ten sposób poprowadzi ich przez konfigurowanie po raz pierwszy, więc nie trzeba nic więcej robić. |
| Aktywny | Urządzenie zostało dostarczone do użytkownika i zostało zarejestrowane w Twojej dzierżawie. Ten stan oznacza również, że te urządzenia regularnie korzysta z urządzenia. |
| Nieaktywny | Urządzenie zostało dostarczone do użytkownika i zostało zarejestrowane w Twojej dzierżawie. Jednak nie używali go ostatnio (w ciągu ostatnich siedmiu dni).  |

#### <a name="troubleshooting-device-registration"></a>Rozwiązywanie problemów z rejestracją urządzeń

| Komunikat o błędzie | Szczegóły |
|-----| ----- |
| Nie znaleziono urządzenia | Nie mogliśmy zarejestrować tego urządzenia, ponieważ nie mogliśmy znaleźć dopasowania do podanego producenta, modelu lub numeru seryjnego. Potwierdź te wartości u dostawcy urządzenia. |
| Skrót sprzętowy jest nieprawidłowy | Skrót sprzętowy podany dla tego urządzenia nie został prawidłowo sformatowany. Sprawdź dwukrotnie skrót sprzętowy, a następnie prześlij go ponownie. |
| Urządzenie już zarejestrowane | To urządzenie jest już zarejestrowane w Twojej organizacji. Nie są wymagane żadne dalsze działania. |
| Urządzenie przechowane przez inną organizację | To urządzenie zostało już odebrać przez inną organizację. Skontaktuj się z dostawcą urządzenia. |
| Nieoczekiwany błąd | Nie można automatycznie przetworzyć Twojego żądania. Skontaktuj się z pomocą techniczną i podaj identyfikator wniosku: `<requestId>` |

### <a name="check-the-image"></a>Sprawdź obraz

Jeśli urządzenie pochodzi od dostawcy Microsoft Managed Desktop, obraz powinien być poprawny.

Jeśli wolisz, możesz również samodzielnie zastosować obraz. Aby rozpocząć, skontaktuj się z przedstawicielem firmy Microsoft, z który pracujesz. Przedstawiciel poda lokalizację i instrukcje dotyczące stosowania obrazu.

### <a name="autopilot-group-tag"></a>Tag grupy rozwiązania Autopilot

Podczas rejestrowania urządzeń za pomocą portalu administracyjnego automatycznie przypisujemy tag grupy rozwiązania Autopilot skojarzony z profilem urządzeń wymienionym w Centrum [partnerskim.](partner-registration.md)
Usługa monitoruje wszystkie Microsoft Managed Desktop urządzeniach i przypisuje tag grupy dowolnym, które jeszcze go nie mają.

### <a name="deliver-the-device"></a>Dostarczanie urządzenia

> [!IMPORTANT]
> Przed oddaniem urządzenia do użytkownika upewnij się, że uzyskano i zastosowano odpowiednie [licencje](../get-ready/prerequisites.md) dla tego użytkownika.

Jeśli wszystkie licencje zostały zastosowane, możesz przygotować użytkowników do [korzystania z urządzeń](get-started-devices.md). Następnie użytkownik może uruchomić urządzenie i przejść przez proces konfiguracji Windows instalacji.
