---
title: Ręczna rejestracja dla istniejących urządzeń
description: Zarejestruj istniejące urządzenia, aby zarządzać nimi przez Microsoft Managed Desktop
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
ms.openlocfilehash: 1d100cc3336dcb465e54f4b81d13d50ecd4bfe1e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704246"
---
# <a name="manual-registration-for-existing-devices"></a>Ręczna rejestracja dla istniejących urządzeń

>[!NOTE]
>W tym artykule opisano procedurę ponownego używania już posiadanych urządzeń i zarejestrowania ich w Microsoft Managed Desktop. Jeśli pracujesz z zupełnie nowymi urządzeniami, zamiast tego wykonaj czynności opisane w te sposób: Rejestrowanie nowych urządzeń Microsoft Managed Desktop [dla siebie](manual-registration.md). <br> <br> Proces rejestrowania urządzeń przez partnerów o dokumencie Procedura [dla partnerów jest udokumentowany](partner-registration.md).

Microsoft Managed Desktop może pracować z zupełnie nowymi urządzeniami lub możesz ponownie używać urządzeń, które być może już posiadasz. W przypadku ponownego użycia urządzeń należy je ponownie zaimportować. Urządzenia można rejestrować w Microsoft Managed Desktop w portalu Microsoft Endpoint Manager sieci.

## <a name="prepare-to-register-existing-devices"></a>Przygotowywanie do zarejestrowania istniejących urządzeń

**Aby zarejestrować istniejące urządzenia:**

1. [Uzyskaj skrót sprzętowy dla każdego urządzenia.](#obtain-the-hardware-hash)
2. [Scalanie danych skrótu](#merge-hash-data).
3. [Zarejestruj urządzenia w Microsoft Managed Desktop](#register-devices-by-using-the-admin-portal).
4. [Sprawdź dwukrotnie, czy obraz jest poprawny.](#check-the-image)
5. [Dostarczyć urządzenie](#deliver-the-device).

### <a name="obtain-the-hardware-hash"></a>Uzyskiwanie skrótu sprzętowego

Microsoft Managed Desktop identyfikuje każde urządzenie jednoznacznie, odwołując się do jego skrótu sprzętowego. Dostępne są cztery opcje uzyskiwania tych informacji z urządzeń, których już używasz.

**Aby uzyskać skrót sprzętowy:**

- Poproś dostawcę OEM o plik rejestracji rozwiązania AutoPilot, który będzie zawierał skróty sprzętowe.
- Zbieranie informacji w [programie Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager).
- Uruchom skrypt Windows PowerShell przy użyciu usługi [Active Directory](#active-directory-powershell-script-method) lub ręcznie na każdym urządzeniu i [](#manual-powershell-script-method) zbierz wyniki w pliku.
- Uruchom każde urządzenie, ale nie przejmij wszystkich Windows konfiguracji i zbierz [skróty na wymiennych dyskach flash](#flash-drive-method).

#### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

Za pomocą skrótów Microsoft Endpoint Configuration Manager można zbierać skróty sprzętowe z istniejących urządzeń, które chcesz zarejestrować w Microsoft Managed Desktop. Jeśli spełniłeś(-asz) wszystkie te wymagania wstępne, możesz zebrać te informacje.

> [!IMPORTANT]
> Wszystkie urządzenia, dla których chcesz uzyskać te informacje, muszą mieć Windows 10 w wersji 1703 lub nowszej.

**Aby zebrać informacje o skrótach sprzętowych:**

1. W konsoli Menedżer konfiguracji wybierz **pozycję Monitorowanie**.
2. W obszarze roboczym Monitorowanie **rozwiń węzeł** Raportowanie, rozwiń węzeł **Raporty** i wybierz węzeł **Sprzęt —** ogólne.
3. Uruchom raport, Windows **informacje o urządzeniu rozwiązania Autopilot** i wyświetl wyniki.
4. W przeglądarce raportów wybierz ikonę Eksportuj, a następnie wybierz opcję **PLIK CSV (rozdzielany przecinkami**).
5. Po zapisaniu pliku musisz przefiltrować wyniki tylko do urządzeń, które zamierzasz zarejestrować w Microsoft Managed Desktop. Następnie przekaż dane do Microsoft Managed Desktop.
    - Otwórz Microsoft Endpoint Manager i **przejdź do menu** Urządzenia.
    - W sekcji Microsoft Managed Desktop wybierz pozycję **Urządzenia**.
    - Wybierz **pozycję + Zarejestruj urządzenia**, co spowoduje otwarcie wysuwanych aplikacji w celu zarejestrowania nowych urządzeń.

Aby uzyskać więcej informacji, zobacz [Rejestrowanie urządzeń za pomocą portalu administracyjnego poniżej](#register-devices-by-using-the-admin-portal) .

#### <a name="active-directory-powershell-script-method"></a>Metoda skryptu programu PowerShell w usłudze Active Directory

W środowisku usługi Active Directory możesz użyć polecenia cmdlet programu PowerShell, `Get-WindowsAutoPilotInfo` aby zdalnie zbierać informacje z urządzeń w grupach usługi Active Directory przy użyciu usługi WinRM. Możesz także użyć polecenia `Get-AD Computer` cmdlet i uzyskać odfiltrowane wyniki dla określonej nazwy modelu sprzętu zawartej w wykazie. Przed rozpoczęciem potwierdź te wymagania wstępne, a następnie kontynuuj.

**Aby użyć metody skryptu programu PowerShell dla usługi Active Directory:**

1. Upewnij się, że włączono funkcję WinRM.
1. Urządzenia, które chcesz zarejestrować, są aktywne w sieci. Oznacza to, że nie są rozłączone ani wyłączone.
1. Upewnij się, że masz parametr poświadczeń domeny, który ma uprawnienie do wykonywania zdalnie na urządzeniach.
1. Upewnij się, Windows zezwala na dostęp do usługi WMI. W tym celu wykonaj następujące czynności:

    - Otwórz panel **Windows Defender sterowania zapory i** wybierz pozycję **Zezwalaj aplikacji lub funkcji na dostęp przez Windows Defender zaporze**.
    - Znajdź **Windows Zarządzania Instrumentacją Zarządzania (WMI)** na liście, włącz opcję Prywatna i Publiczna **, a** następnie wybierz przycisk **OK**.
1. Otwórz monit programu PowerShell z uprawnieniami administracyjnymi.
1. Uruchom *jeden z* tych skryptów:

    ```powershell
    Install-script -name Get-WindowsAutoPilotInfo 
    #example one – leverage Get-ADComputer to enumerate devices 
    Get-ADComputer -filter * | powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo.ps1 -credential Domainname\<accountname>
    ```

    ```powershell
    #example two – target specific devices: 
    Set-ExecutionPolicy powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo.ps1 -credential Domainname\<accountname> -Name Machine1,Machine2,Machine3
    ```

1. Dostęp do katalogów, w których mogą być wpisy dotyczące urządzeń. Usuń wpisy dla każdego urządzenia ze *wszystkich katalogów*, w tym katalogów Windows Server Active Directory domenowych i Azure Active Directory. Przetwarzanie może potrwać kilka godzin.
1. Usługi zarządzania dostępem, w przypadku których mogą być wpisy dotyczące urządzeń. Usuń wpisy dotyczące poszczególnych urządzeń ze  wszystkich usług zarządzania, w tym Microsoft Endpoint Configuration Manager, Microsoft Intune i Windows Autopilot. Przetwarzanie może potrwać kilka godzin.

Teraz możesz przystąpić do [rejestrowania urządzeń](#register-devices-by-using-the-admin-portal).

#### <a name="manual-powershell-script-method"></a>Ręczna metoda skryptu programu PowerShell

**Aby użyć ręcznej metody skryptu programu PowerShell:**

1. Otwórz monit programu PowerShell z uprawnieniami administracyjnymi.
2. Uruchom `Install-Script -Name Get-WindowsAutoPilotInfo`.
3. Uruchom `powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`.
4. [Scalanie danych skrótu.](#merge-hash-data)

#### <a name="flash-drive-method"></a>Metoda dysku flash

**Aby użyć metody dysku flash:**

1. Na urządzeniu innym niż to, które rejestrujesz, włóż dysk USB.
2. Otwórz monit programu PowerShell z uprawnieniami administracyjnymi.
3. Uruchom `Save-Script -Name Get-WindowsAutoPilotInfo -Path <pathToUsb>`.
4. Włącz urządzenie, które rejestrujesz, ale *nie uruchamiaj procesu konfiguracji*. Jeśli środowisko konfiguracji zostanie przypadkowo uruchomić, będzie trzeba zresetować lub ponownie zaimportować urządzenie.
5. Włóż dysk USB, a następnie naciśnij klawisze SHIFT + F10.
6. Otwórz monit programu PowerShell z uprawnieniami administracyjnymi, a następnie uruchom .`cd <pathToUsb>`
7. Uruchom `Set-ExecutionPolicy -ExecutionPolicy Unrestricted`.
8. Uruchom `.\Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`.
9. Usuń dysk USB, a następnie wyłącz urządzenie, uruchamiając program `shutdown -s -t 0`.
10. [Scalanie danych skrótu.](#merge-hash-data)

> [!IMPORTANT]
> Nie wsaduj ponownie urządzenia, które zarejestrujesz, dopóki nie zakończysz rejestracji dla tego urządzenia.

### <a name="merge-hash-data"></a>Scalanie danych z skrótami

Jeśli dane skrótu sprzętowego zostały zebrane ręcznie za pomocą programu PowerShell lub dysku flash, musisz połączyć dane z tych dwóch plików CSV w jeden plik, aby zakończyć rejestrację. Oto przykładowy skrypt programu PowerShell ułatwiający wykonywanie tych pracy:

```powershell
Import-CSV -Path (Get-ChildItem -Filter *.csv) | ConvertTo-Csv -NoTypeInformation | % {$_.Replace('"', '')} | Out-File .\aggregatedDevices.csv
```

Po scaleniu danych z hasztagiem w jednym pliku CSV możesz przystąpić do [rejestrowania urządzeń](#register-devices-by-using-the-admin-portal).

## <a name="register-devices-by-using-the-admin-portal"></a>Rejestrowanie urządzeń za pomocą portalu administracyjnego

W [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) nawigacji wybierz **pozycję Urządzenia** w lewym okienku nawigacji. W sekcji Microsoft Managed Desktop wybierz pozycję **Urządzenia**. W obszarze Microsoft Managed Desktop urządzenia wybierz pozycję **+ Zarejestruj** urządzenia, co spowoduje otwarcie wysuwanych aplikacji w celu zarejestrowania nowych urządzeń.

<!-- Update with new picture [![Fly-in after selecting Register devices, listing devices with columns for assigned users, serial number, status, last-seen date, and age.](../../media/new-registration-ui.png)](../../media/new-registration-ui.png) -->

<!--Registering any existing devices with Managed Desktop will completely re-image them; make sure you've backed up any important data prior to starting the registration process.-->

**Aby zarejestrować urządzenia za pomocą portalu administracyjnego:**

1. W **przesyłaniu** pliku podaj ścieżkę do utworzonego wcześniej pliku CSV.
2. Wybierz [profil urządzenia](../service-description/profiles.md) z menu rozwijanego.
3. Wybierz **pozycję Zarejestruj urządzenia**. System doda urządzenia do listy urządzeń **na urządzeniu.** Urządzenia są oznaczone jako **Oczekujące na rejestrację**. Rejestracja zwykle trwa mniej niż 10 minut, a jeśli się powiedzie, urządzenie będzie wyświetlane jako **Gotowe dla użytkownika**. **Ready for user** means it's ready and waiting for a user to start using.

> [!NOTE]
> Jeśli ręcznie zmienisz członkostwo w Azure Active Directory (AAD) na urządzeniu, zostanie ono automatycznie ponownie przypisana do grupy dla jej profilu urządzenia i usunięta ze wszystkich grup powodującego konflikt.

Możesz monitorować postęp rejestracji urządzeń na stronie głównej. Raporty mogą obejmować:

| Stan | Opis |
| ----- | ----- |
| Oczekiwanie na rejestrację | Rejestracja nie została jeszcze ukończona. Sprawdź ponownie później. |
| Rejestracja nie powiodła się | Rejestracji nie można ukończyć. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z rejestracją urządzenia](#troubleshooting-device-registration). |
| Gotowe dla użytkownika | Rejestracja powiodła się. Urządzenie jest teraz gotowe do dostarczenia do użytkownika. Microsoft Managed Desktop ten sposób poprowadzi ich przez konfigurowanie po raz pierwszy, więc nie trzeba nic więcej robić. |
| Aktywny | Urządzenie zostało dostarczone do użytkownika i zostało zarejestrowane w Twojej dzierżawie. Ten stan oznacza również, że te urządzenia regularnie korzysta z urządzenia. |
| Nieaktywny | Urządzenie zostało dostarczone do użytkownika i zostało zarejestrowane w Twojej dzierżawie. Jednak użytkownik nie używał urządzenia ostatnio (w ciągu ostatnich siedmiu dni). |

### <a name="troubleshooting-device-registration"></a>Rozwiązywanie problemów z rejestracją urządzeń

| Komunikat o błędzie | Szczegóły |
| ----- | ----- |
| Nie znaleziono urządzenia | Nie mogliśmy zarejestrować tego urządzenia, ponieważ nie mogliśmy znaleźć dopasowania do podanego producenta, modelu lub numeru seryjnego. Potwierdź te wartości u dostawcy urządzenia. |
| Skrót sprzętowy jest nieprawidłowy | Skrót sprzętowy podany dla tego urządzenia nie został prawidłowo sformatowany. Sprawdź dwukrotnie skrót sprzętowy, a następnie prześlij go ponownie. |
| Urządzenie już zarejestrowane | To urządzenie jest już zarejestrowane w Twojej organizacji. Nie są wymagane żadne dalsze działania. |
| Urządzenie przechowane przez inną organizację | To urządzenie zostało już odebrać przez inną organizację. Skontaktuj się z dostawcą urządzenia. |
| Nieoczekiwany błąd | Nie można automatycznie przetworzyć Twojego żądania. Skontaktuj się z pomocą techniczną i podaj identyfikator wniosku: `<requestId>` |

## <a name="check-the-image"></a>Sprawdź obraz

Jeśli urządzenie pochodzi od dostawcy Microsoft Managed Desktop, obraz powinien być poprawny.

Jeśli wolisz, możesz również samodzielnie zastosować obraz. Aby rozpocząć pracę, skontaktuj się z przedstawicielem firmy Microsoft, z którym pracujesz, a następnie poda Ci lokalizację i instrukcje dotyczące stosowania obrazu.

## <a name="deliver-the-device"></a>Dostarczanie urządzenia

> [!IMPORTANT]
> Przed oddaniem urządzenia do użytkownika upewnij się, że uzyskano i zastosowano odpowiednie [licencje](../get-ready/prerequisites.md) dla tego użytkownika.

Jeśli wszystkie licencje zostały zastosowane, możesz przygotować użytkowników do [korzystania z urządzeń](get-started-devices.md). Następnie użytkownik może uruchomić urządzenie i przejść przez proces konfiguracji Windows instalacji.
