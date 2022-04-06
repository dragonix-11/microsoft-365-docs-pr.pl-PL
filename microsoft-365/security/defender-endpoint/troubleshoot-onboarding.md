---
title: Rozwiązywanie Ochrona punktu końcowego w usłudze Microsoft Defender problemów z dołączaniem
description: Rozwiązywanie problemów, które mogą wystąpić podczas dołączania urządzeń lub do Ochrona punktu końcowego w usłudze Microsoft Defender usługi.
keywords: rozwiązywanie problemów z wnoszeniu, wnoszeniu, przeglądarka zdarzeń, kompilacje zbierania i podglądu danych, dane czujnika i diagnostyka
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
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: 9813857bffe62ab26d377d49b2830f55d0f38f93
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473524"
---
# <a name="troubleshoot-microsoft-defender-for-endpoint-onboarding-issues"></a>Rozwiązywanie Ochrona punktu końcowego w usłudze Microsoft Defender problemów z dołączaniem

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Windows Server 2012 R2
- System Windows Server 2016
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Jeśli wystąpią problemy, może Ochrona punktu końcowego w usłudze Microsoft Defender rozwiązywanie problemów z procesem dołączania.
Ta strona zawiera szczegółowe kroki rozwiązywania problemów z wdrażaniem, które mogą wystąpić podczas wdrażania przy użyciu jednego z narzędzi wdrażania, oraz typowe błędy, które mogą wystąpić na urządzeniach.

Przed rozpoczęciem rozwiązywania problemów z narzędziami dołączania należy sprawdzić, czy są spełnione minimalne wymagania dotyczące urządzeń dołączających do usług. [Dowiedz się więcej o wymaganiach dotyczących licencjonowania, sprzętu i oprogramowania, które należy spełnić, aby wdowysyłać urządzenia do usługi](minimum-requirements.md).

## <a name="troubleshoot-issues-with-onboarding-tools"></a>Rozwiązywanie problemów z narzędziami dołączania

Jeśli po zakończeniu procesu dołączania urządzenia nie są już na liście Urządzenia po upływie godziny[](investigate-machines.md), może to wskazywać na problem z włozeniem lub łącznością.

### <a name="troubleshoot-onboarding-when-deploying-with-group-policy"></a>Rozwiązywanie problemów z dołączaniem podczas wdrażania za pomocą zasady grupy

Wdrożenie z zasady grupy jest wykonywane przez uruchomienie skryptu wdrażania na urządzeniach. Konsola zasady grupy nie wskazuje, czy wdrożenie zakończyło się pomyślnie, czy nie.

Jeśli po zakończeniu procesu dołączania urządzenia nie są już na liście Urządzenia po upływie godziny[](investigate-machines.md), możesz sprawdzić wyniki skryptu na tych urządzeniach. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z wdrażaniem podczas wdrażania za pomocą skryptu](#troubleshoot-onboarding-when-deploying-with-a-script).

Jeśli skrypt zostanie pomyślnie ukończony, zobacz Rozwiązywanie problemów z dołączaniem na urządzeniach [, aby uzyskać](#troubleshoot-onboarding-issues-on-the-device) informacje o dodatkowych błędach, które mogą wystąpić.

### <a name="troubleshoot-onboarding-issues-when-deploying-with-microsoft-endpoint-configuration-manager"></a>Rozwiązywanie problemów z dołączaniem podczas wdrażania za pomocą aplikacji Microsoft Endpoint Configuration Manager

W przypadku korzystania z urządzeń korzystających z następujących wersji programu Configuration Manager:

- Microsoft Endpoint Configuration Manager
- System Center 2012 Configuration Manager
- System Center 2012 R2 Configuration Manager

Wdrożenie przy użyciu powyższych wersji pakietu Configuration Manager jest wykonywane przez uruchomienie skryptu dołączania na urządzeniach. Możesz śledzić wdrożenie w konsoli Configuration Manager sieci.

Jeśli wdrożenie się nie powiedzie, możesz sprawdzić wynik skryptu na urządzeniach.

Jeśli pomyślnie ukończono dołączanie, ale urządzenia nie są wyświetlane na liście Urządzenia po  upływie godziny, zobacz Rozwiązywanie problemów z [](#troubleshoot-onboarding-issues-on-the-device) dołączaniem na urządzeniu, aby uzyskać informacje o dodatkowych błędach, które mogą wystąpić.

### <a name="troubleshoot-onboarding-when-deploying-with-a-script"></a>Rozwiązywanie problemów z dołączaniem podczas wdrażania za pomocą skryptu

**Sprawdź wynik skryptu na urządzeniu:**

1. Kliknij **przycisk Start**, **wpisz Podgląd zdarzeń** i naciśnij klawisz **Enter**.

2. Przejdź do **Windows Dzienniki.** \> 

3. Poszukaj zdarzenia w źródle zdarzeń **WDATPOnboarding** .

Jeśli skrypt nie powiedzie się, a zdarzenie jest błędem, możesz sprawdzić identyfikator zdarzenia w poniższej tabeli, aby uzyskać pomoc w rozwiązywaniu problemów.

> [!NOTE]
> Następujące identyfikatory zdarzeń są specyficzne tylko dla skryptu dołączania.

<br>

****

|Identyfikator zdarzenia|Typ błędu|Kroki rozwiązywania problemu|
|:---:|---|---|
|`5`|Znaleziono dane wynoszone, ale nie można ich usunąć|Sprawdź uprawnienia do rejestru, a w szczególności <p> `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.|
|`10`|Danych dołączania nie można zapisywać w rejestrze|Sprawdź uprawnienia do rejestru, a w szczególności <p> `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`. <p> Sprawdź, czy skrypt został uruchomiony jako administrator.|
|`15`|Nie można uruchomić usługi SENSE|Sprawdzanie kondycji usługi (`sc query sense` polecenie). Upewnij się, że nie jest w stanie pośrednim (na przykład *Pending_Stopped*' lub *"Pending_Running")* i spróbuj ponownie uruchomić skrypt (z uprawnieniami administratora). <p> Jeśli na urządzeniu działa Windows 10 wersji 1607 `sc query sense` `START_PENDING`i ponownie zostanie uruchomione polecenie, uruchom ponownie urządzenie. Jeśli ponowne uruchomienie urządzenia nie rozwiązało problemu, uaktualnij go do aktualizacji KB4015217 i spróbuj ponownie wboardować.|
|`15`|Nie można uruchomić usługi SENSE|Jeśli komunikat o błędzie jest taki: Wystąpił błąd systemu 577 lub błąd 1058, należy włączyć sterownik Program antywirusowy Microsoft Defender ELAM. Aby uzyskać instrukcje, zobacz Zapewnianie, że [](#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy) Program antywirusowy Microsoft Defender nie jest wyłączone przez zasady.|
|`30`|Nie można czekać na uruchomienie usługi przez skrypt|Uruchamianie usługi mogło zostać wykonane dłużej lub wystąpiły błędy podczas próby uruchomienia. Aby uzyskać więcej informacji o zdarzeniach i błędach związanych z sensem, zobacz [Przeglądanie zdarzeń i błędów przy użyciu przeglądarki zdarzeń](event-error-codes.md).|
|`35`|Skrypt nie znalazł potrzebnej wartości rejestru stanu dołączania|Przy pierwszym uruchamianiu usługi SENSE jest zapisywany stan dołączania do lokalizacji rejestru. <p> `HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status`. <p> Skrypt nie znalazł go po kilku sekundach. Możesz je przetestować ręcznie i sprawdzić, czy są dostępne. Aby uzyskać więcej informacji o zdarzeniach i błędach związanych z sensem, zobacz [Przeglądanie zdarzeń i błędów przy użyciu przeglądarki zdarzeń](event-error-codes.md).|
|`40`|Stan dołączania do usługi SENSE nie jest ustawiony na **1**|Usługa SENSE nie została prawidłowo w naniesiena. Aby uzyskać więcej informacji o zdarzeniach i błędach związanych z sensem, zobacz [Przeglądanie zdarzeń i błędów przy użyciu przeglądarki zdarzeń](event-error-codes.md).|
|`65`|Niewystarczające uprawnienia|Uruchom ponownie skrypt z uprawnieniami administratora.|
|

### <a name="troubleshoot-onboarding-issues-using-microsoft-intune"></a>Rozwiązywanie problemów z dołączaniem przy użyciu Microsoft Intune

Możesz użyć Microsoft Intune do sprawdzenia kodów błędów i próby rozwiązania przyczyny problemu.

Jeśli zasady skonfigurowane w aplikacji Intune nie są propagowane na urządzeniach, może być konieczne skonfigurowanie automatycznej rejestracji mdM.

Skorzystaj z poniższych tabel, aby zrozumieć możliwe przyczyny problemów podczas dołączania do pracy:

- Microsoft Intune kodów błędów i OMA-URIs tabeli
- Znane problemy dotyczące tabeli niezgodności
- Tabela Zarządzanie urządzeniami zdarzeń usługi Mobile Zarządzanie urządzeniami (MDM)

Jeśli żaden z dzienników zdarzeń i czynności rozwiązywania problemów nie działają, pobierz skrypt Local z  sekcji Zarządzanie urządzeniami w portalu i uruchom go w wierszu polecenia z podwyższonym poziomem uprawnień.

#### <a name="microsoft-intune-error-codes-and-oma-uris"></a>Microsoft Intune kodów błędów i OMA-URIs

<br>

****

|Hex kodu błędu|Kod błędu Dec|Opis błędu|OMA-URI|Możliwe kroki przyczyn i rozwiązywania problemów|
|:---:|---|---|---|---|
|0x87D1FDE8|-2016281112|Działania naprawcze nie powiodły się|Wniesienie <p> Wyniesienie|**Możliwa przyczyna:** Wnonięcie lub wynoszenie nie powiodło się w przypadku niewłaściwego obiektu blob: nieprawidłowy podpis lub brakujące pola PreviousOrgIds. <p> **Procedura rozwiązywania problemów:** <p> Sprawdź identyfikatory zdarzeń [w sekcji dziennika](#view-agent-onboarding-errors-in-the-device-event-log) zdarzeń urządzenia w przypadku błędów dołączania agenta widoku. <p> Sprawdź dzienniki zdarzeń MDM w poniższej tabeli lub postępuj zgodnie z instrukcjami w tece Diagnozowanie niepowodzeń usługi [MDM w](/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10) Windows.|
||||Wniesienie <p> Wyniesienie <p> SampleSharing|**Możliwa przyczyna:** Ochrona punktu końcowego w usłudze Microsoft Defender rejestru zasad nie istnieje lub klient OMA DM nie ma uprawnień do zapisu w tym kluczu. <p> **Procedura rozwiązywania problemów:** Upewnij się, że istnieje następujący klucz rejestru: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection` <p> Jeśli nie istnieje, otwórz polecenie z podwyższonym poziomem uprawnień i dodaj klucz.|
||||SenseIsRunning <p> OnboardingState <p> OrgId|**Możliwa przyczyna:** Próba rozwiązania problemów za pomocą właściwości tylko do odczytu. Dołączanie nie powiodło się. <p> **Procedura rozwiązywania problemów:** Zapoznaj się z instrukcjami rozwiązywania [problemów w tece Rozwiązywanie problemów z dołączaniem na urządzeniu](#troubleshoot-onboarding-issues-on-the-device). <p> Sprawdź dzienniki zdarzeń MDM w poniższej tabeli lub postępuj zgodnie z instrukcjami w tece Diagnozowanie niepowodzeń usługi [MDM w](/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10) Windows.|
||||Wszystkie|**Możliwa przyczyna:** Spróbuj wdrożyć Ochrona punktu końcowego w usłudze Microsoft Defender na nie obsługiwanej sku/platformie, zwłaszcza Holographic SKU. <p> Obecnie obsługiwane platformy: <p> Enterprise, Education i Professional.<p> Serwer nie jest obsługiwany.|
|0x87D101A9|-2016345687|SyncML(425): Żądane polecenie nie powiodło się, ponieważ nadawca nie ma odpowiednich uprawnień kontroli dostępu do adresata.|Wszystkie|**Możliwa przyczyna:** Spróbuj wdrożyć Ochrona punktu końcowego w usłudze Microsoft Defender na nie obsługiwanej sku/platformie, zwłaszcza Holographic SKU.<p> Obecnie obsługiwane platformy: <p> Enterprise, Education i Professional.|
|

#### <a name="known-issues-with-non-compliance"></a>Znane problemy dotyczące braku zgodności

W poniższej tabeli przedstawiono informacje o problemach związanych z niezgodnościami i o tym, jak można je rozwiązać.

<br>

****

|Sprawa|Symptomy|Możliwe kroki przyczyn i rozwiązywania problemów|
|:---:|---|---|
|`1`|Urządzenie jest zgodne przez usługę SenseIsRunning OMA-URI. Ale jest niezgodne przez orgid, dołączanie i dołączanieState OMA-URI.|**Możliwa przyczyna:** Sprawdź, czy użytkownik przekazał OOBE po Windows instalacji lub uaktualnieniu. Podczas dołączania do systemu OOBE nie można ukończyć, ale sense już działa. <p> **Procedura rozwiązywania problemów:** Poczekaj na ukończenie pracy systemu OOBE.|
|`2`|Urządzenie jest zgodne przez interfejsy OMA-URI organizacji, dołączania i dołączania, ale jest niezgodne przez senseisrunning OMA-URI.|**Możliwa przyczyna:** Typ uruchamiania usługi Sense service jest ustawiony jako "Opóźnione rozpoczęcie". Czasami powoduje to, że Microsoft Intune zgłasza urządzenie jako niezgodne przez SenseIsRunning, gdy sesja DM występuje przy uruchomieniu systemu. <p> **Procedura rozwiązywania problemów:** Problem powinien zostać automatycznie rozwiązany w ciągu 24 godzin.|
|`3`|Urządzenie jest niezgodne|**Procedura rozwiązywania problemów:** Upewnij się, że zasady dołączania i wynoszania nie są wdrażane jednocześnie na tym samym urządzeniu.|
|

#### <a name="mobile-device-management-mdm-event-logs"></a>Dzienniki Zarządzanie urządzeniami mdM (Mobile Zarządzanie urządzeniami)

Wyświetlanie dzienników zdarzeń usługi MDM w celu rozwiązywania problemów, które mogą się pojawić podczas dołączania:

Nazwa dziennika: Microsoft\Windows\DeviceManagement-EnterpriseDiagnostics-Provider

Nazwa kanału: Administrator

<br>

****

|ID|Ważność|Opis zdarzenia|Czynności umożliwiające rozwiązywanie problemów|
|---|---|---|---|
|1819|Error|Ochrona punktu końcowego w usłudze Microsoft Defender CSP: Nie można ustawić wartości węzła. NodeId: (%1), TokenName: (%2), Result: (%3).|Pobierz [aktualizację skumulowaną dla Windows 10 1607](https://go.microsoft.com/fwlink/?linkid=829760).|
|

## <a name="troubleshoot-onboarding-issues-on-the-device"></a>Rozwiązywanie problemów z dołączaniem na urządzeniu

Jeśli używane narzędzia wdrażania nie wskazują błędu w procesie wdrażania, ale urządzenia nadal nie pojawiają się na liście urządzeń w ciągu godziny, przejdź do poniższych tematów weryfikacji, aby sprawdzić, czy wystąpił błąd Ochrona punktu końcowego w usłudze Microsoft Defender agenta.

- [Wyświetlanie błędów dołączania agenta w dzienniku zdarzeń urządzenia](#view-agent-onboarding-errors-in-the-device-event-log)
- [Upewnij się, że usługa danych diagnostycznych jest włączona](#ensure-the-diagnostics-service-is-enabled)
- [Upewnij się, że usługa jest ustawiona na uruchomienie](#ensure-the-service-is-set-to-start)
- [Upewnij się, że urządzenie ma połączenie internetowe](#ensure-the-device-has-an-internet-connection)
- [Zapewnianie Program antywirusowy Microsoft Defender że zasady nie wyłączą tego ustawienia](#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)

### <a name="view-agent-onboarding-errors-in-the-device-event-log"></a>Wyświetlanie błędów dołączania agenta w dzienniku zdarzeń urządzenia

1. Kliknij **przycisk Start**, **wpisz Podgląd zdarzeń** i naciśnij klawisz **Enter**.

2. W **okienku Podgląd zdarzeń (Local)** rozwiń pozycję **Applications and Services Logs** \> (Dzienniki aplikacji i usług) **firma Microsoft** \> **Windows** \> **SENSE**.

   > [!NOTE]
   > SENSE to wewnętrzna nazwa używana do nazywania czujnika zachowania, który potęguje Ochrona punktu końcowego w usłudze Microsoft Defender.

3. Wybierz **pozycję Operacyjne** , aby załadować dziennik.

4. W **okienku Akcja** kliknij pozycję **Filtruj bieżący dziennik**.

5. Na karcie **Filtr** w obszarze **Poziom zdarzenia wybierz** pozycję **Krytyczne**, **Ostrzeżenie** i **Błąd**, a następnie kliknij przycisk **OK**.

   :::image type="content" source="images/filter-log.png" alt-text="Filtr Podgląd zdarzeń dziennika" lightbox="images/filter-log.png":::

6. Zdarzenia, które mogą wskazywać problemy, pojawią się w **okienku Operacyjne** . Możesz spróbować je rozwiązać w oparciu o rozwiązania z poniższej tabeli:

   <br>

   ****

   |Identyfikator zdarzenia|Komunikat|Kroki rozwiązywania problemu|
   |:---:|---|---|
   |`5`|Ochrona punktu końcowego w usłudze Microsoft Defender nie można połączyć się z serwerem _przy zmiennej_|[Upewnij się, że urządzenie ma dostęp do Internetu](#ensure-the-device-has-an-internet-connection).|
   |`6`|Ochrona punktu końcowego w usłudze Microsoft Defender nie jest wnosłana i nie znaleziono parametrów dołączania. Kod błędu: _zmienna_|[Uruchom ponownie skrypt dołączania](configure-endpoints-script.md).|
   |`7`|Ochrona punktu końcowego w usłudze Microsoft Defender nie można odczytać parametrów dołączania. Kod błędu: _zmienna_|[Upewnij się, że urządzenie ma dostęp do Internetu](#ensure-the-device-has-an-internet-connection), a następnie ponownie uruchom cały proces dołączania.|
   |`9`|Ochrona punktu końcowego w usłudze Microsoft Defender nie można zmienić typu uruchomienia usługi. Kod błędu: zmienna|Jeśli zdarzenie miało miejsce podczas dołączania, uruchom ponownie komputer i ponownie spróbuj uruchomić skrypt dołączania. Aby uzyskać więcej informacji, zobacz [Ponownie uruchom skrypt dołączania](configure-endpoints-script.md). <br><br>Jeśli zdarzenie miało miejsce podczas wynegocjowania, skontaktuj się z pomocą techniczną.|
   |`10`|Ochrona punktu końcowego w usłudze Microsoft Defender usługi nie udało się utrzymać informacji o dołączaniu. Kod błędu: zmienna|Jeśli zdarzenie miało miejsce podczas dołączania, ponownie spróbuj uruchomienie skryptu dołączania. Aby uzyskać więcej informacji, zobacz [Ponownie uruchom skrypt dołączania](configure-endpoints-script.md). <br><br>Jeśli problem będzie nadal występował, skontaktuj się z pomocą techniczną.|
   |`15`|Ochrona punktu końcowego w usłudze Microsoft Defender nie można uruchomić kanału poleceń z adresem URL: _zmienna_|[Upewnij się, że urządzenie ma dostęp do Internetu](#ensure-the-device-has-an-internet-connection).|
   |`17`|Ochrona punktu końcowego w usłudze Microsoft Defender nie można zmienić lokalizacji usługi połączonego użytkownika i telemetrii. Kod błędu: zmienna|[Uruchom ponownie skrypt dołączania](configure-endpoints-script.md). Jeśli problem będzie nadal występował, skontaktuj się z pomocą techniczną.|
   |`25`|Ochrona punktu końcowego w usłudze Microsoft Defender nie można zresetować stanu kondycji w rejestrze. Kod błędu: _zmienna_|Skontaktuj się z pomocą techniczną.|
   |`27`|Nie można włączyć Ochrona punktu końcowego w usłudze Microsoft Defender w trybie Windows Defender. Proces dołączania nie powiódł się. Kod błędu: zmienna|Skontaktuj się z pomocą techniczną.|
   |`29`|Nie można odczytać parametrów wynoszowania. Typ błędu: %1, Kod błędu: %2, Opis: %3|Upewnij się, że urządzenie ma dostęp do Internetu, a następnie ponownie uruchom cały proces wywęzienia.|
   |`30`|Nie można wyłączyć trybu $(build.sense.productDisplayName) w Ochrona punktu końcowego w usłudze Microsoft Defender. Kod błędu: %1|Skontaktuj się z pomocą techniczną.|
   |`32`|Usługa $(build.sense.productDisplayName) nie powiodła się po zakończeniu procesu wynoszania. Kod błędu: %1|Sprawdź, czy typ uruchomienia usługi jest ręczny i czy ponownie uruchom urządzenie.|
   |`55`|Nie można utworzyć autologowania bezpiecznego etW. Kod błędu: %1|Uruchom ponownie urządzenie.|
   |`63`|Aktualizowanie typu uruchomienia usługi zewnętrznej. Nazwa: %1, rzeczywisty typ rozpoczęcia: %2, oczekiwany typ rozpoczęcia: %3, kod wyjścia: %4|Zidentyfikuj, co powoduje zmiany w typie uruchomienia wymienionej usługi. Jeśli kod zakończenia jest innego niż 0, należy ręcznie naprawić typ początku, aby był oczekiwanym typem początku.|
   |`64`|Uruchamianie zatrzymało usługę zewnętrzną. Nazwa: %1, kod wyjścia: %2|Jeśli zdarzenie nadal się pojawia, skontaktuj się z pomocą techniczną.|
   |`68`|Typ uruchomienia usługi jest nieoczekiwany. Nazwa usługi: %1, rzeczywisty typ rozpoczęcia: %2, oczekiwany typ rozpoczęcia: %3|Zidentyfikuj, co powoduje zmiany w typie początku. Naprawianie wymienionego typu uruchomienia usługi.|
   |`69`|Usługa została zatrzymana. Nazwa usługi: %1|Uruchom wymienioną usługę. Jeśli ten problem nie ustąpi, skontaktuj się z pomocą techniczną.|
   |

Na urządzeniu znajdują się dodatkowe składniki, od których Ochrona punktu końcowego w usłudze Microsoft Defender musi działać prawidłowo. Jeśli nie ma żadnych błędów związanych z dołączaniem w dzienniku zdarzeń agenta Ochrona punktu końcowego w usłudze Microsoft Defender, postępuj zgodnie z poniższymi krokami, aby upewnić się, że dodatkowe składniki są poprawnie skonfigurowane.

<span id="ensure-the-diagnostics-service-is-enabled" />

### <a name="ensure-the-diagnostic-data-service-is-enabled"></a>Upewnij się, że usługa danych diagnostycznych jest włączona

Jeśli urządzenia nie zgłaszają się poprawnie, może być konieczne sprawdzenie, czy usługa Windows jest automatycznie uruchamiana i działa na urządzeniu. Usługa mogła zostać wyłączona przez inne programy lub zmiany w konfiguracji użytkownika.

Najpierw upewnij się, że usługa jest ustawiona tak, aby uruchamiała się automatycznie podczas uruchamiania Windows, a następnie sprawdź, czy usługa jest obecnie uruchomiona (i uruchom ją, jeśli nie jest).

### <a name="ensure-the-service-is-set-to-start"></a>Upewnij się, że usługa jest ustawiona na uruchomienie

**Użyj wiersza polecenia, aby sprawdzić typ uruchamiania Windows danych diagnostycznych**:

1. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień na urządzeniu:

   a. Kliknij **przycisk Start**, wpisz **cmd** i naciśnij klawisz **Enter**.

   b. Kliknij prawym przyciskiem myszy **pozycję Wiersz polecenia i** wybierz **pozycję Uruchom jako administrator**.

2. Wprowadź następujące polecenie i naciśnij klawisz **Enter**:

   ```console
   sc qc diagtrack
   ```

   Jeśli usługa jest włączona, wynik powinien wyglądać tak, jak na poniższym zrzucie ekranu:

   :::image type="content" source="images/windefatp-sc-qc-diagtrack.png" alt-text="Wynik polecenia zapytania sc w celu rozwiązania diagtrack" lightbox="images/windefatp-sc-qc-diagtrack.png":::

   Jeśli to `START_TYPE` ustawienie nie jest ustawione `AUTO_START`na , musisz skonfigurować usługę tak, aby uruchamiała się automatycznie.

**Użyj wiersza polecenia, aby ustawić automatyczne uruchamianie Windows danych diagnostycznych:**

1. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień na urządzeniu:

   a. Kliknij **przycisk Start**, wpisz **cmd** i naciśnij klawisz **Enter**.

   b. Kliknij prawym przyciskiem myszy **pozycję Wiersz polecenia i** wybierz **pozycję Uruchom jako administrator**.

2. Wprowadź następujące polecenie i naciśnij klawisz **Enter**:

   ```console
   sc config diagtrack start=auto
   ```

3. Zostanie wyświetlony komunikat o sukcesie. Sprawdź zmianę, wprowadzając następujące polecenie, a następnie naciśnij klawisz **Enter**:

   ```console
   sc qc diagtrack
   ```

4. Uruchom usługę. W wierszu polecenia wpisz następujące polecenie i naciśnij klawisz **Enter**:

   ```console
   sc start diagtrack
   ```

### <a name="ensure-the-device-has-an-internet-connection"></a>Upewnij się, że urządzenie ma połączenie internetowe

Czujnik Ochrona punktu końcowego w usłudze Microsoft Defender wymaga od firmy Microsoft Windows HTTP (WinHTTP) zgłaszania danych czujnika i komunikowania się z Ochrona punktu końcowego w usłudze Microsoft Defender serwisem.

System WinHTTP jest niezależny od ustawień serwera proxy przeglądania Internetu i innych aplikacji kontekstowych użytkownika i musi mieć możliwość wykrycia serwerów proxy dostępnych w danym środowisku.

Aby upewnić się, że czujnik ma łączność z usługą, wykonaj czynności opisane w temacie Weryfikowanie łączności klienta z Ochrona punktu końcowego w usłudze Microsoft Defender [URL usługi](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls).

Jeśli weryfikacja zakończy się niepowodzeniem i Twoje środowisko łączy się z Internetem za pomocą serwera proxy, postępuj zgodnie z instrukcjami opisanymi w temacie Konfigurowanie ustawień serwera [proxy i łączności internetowej](configure-proxy-internet.md) .

### <a name="ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy"></a>Zapewnianie Program antywirusowy Microsoft Defender że zasady nie wyłączą tego ustawienia

> [!IMPORTANT]
> Poniższe informacje dotyczą tylko urządzeń, które nie  otrzymały jeszcze aktualizacji z sierpnia 2020 r. (wersja 4.18.2007.8) do Program antywirusowy Microsoft Defender.
>
> Ta aktualizacja gwarantuje, że Program antywirusowy Microsoft Defender wyłączyć na urządzeniach klienckich za pośrednictwem zasad systemowych.

**Problem**: Ochrona punktu końcowego w usłudze Microsoft Defender nie uruchamia się po rozpoczęciu.

**Objaw**: Podczas próby uruchomienia usługi pomyślnie ukończono dołączanie, ale podczas próby uruchomienia usługi jest wyświetlany błąd 577 lub 1058.

**Rozwiązanie**: Jeśli na Twoich urządzeniach jest uruchomiony klient ochrony przed złośliwym oprogramowaniem innej firmy, agent Ochrona punktu końcowego w usłudze Microsoft Defender potrzebuje, aby włączono sterownik ochrony przed złośliwym oprogramowaniem (ELAM, Early Launch Antimalware). Należy się upewnić, że zasady systemowe nie wyłączają tej opcji.

- W zależności od narzędzia służącego do implementowania zasad musisz sprawdzić, czy wyczyszczysz Windows Defender zasad:

  - DisableAntiSpyware
  - DisableAntiVirus

  Na przykład w zasady grupy nie powinny być żadne pozycje, takie jak następujące wartości:

  - `<Key Path="SOFTWARE\Policies\Microsoft\Windows Defender"><KeyValue Value="0" ValueKind="DWord" Name="DisableAntiSpyware"/></Key>`
  - `<Key Path="SOFTWARE\Policies\Microsoft\Windows Defender"><KeyValue Value="0" ValueKind="DWord" Name="DisableAntiVirus"/></Key>`

> [!IMPORTANT]
> To `disableAntiSpyware` ustawienie zostanie wycofane i będzie ignorowane na wszystkich Windows 10 urządzeniach od sierpnia 2020 r. (wersja 4.18.2007.8) do Program antywirusowy Microsoft Defender.

- Po wyczyszczeniu zasad ponownie uruchom kroki dotyczące dołączania.

- Możesz również sprawdzić poprzednie wartości kluczy rejestru, aby sprawdzić, czy zasady są wyłączone, otwierając klucz rejestru `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`.

  :::image type="content" source="images/atp-disableantispyware-regkey.png" alt-text="Klucz rejestru dla Program antywirusowy Microsoft Defender" lightbox="images/atp-disableantispyware-regkey.png":::

   > [!NOTE]
   > Wszystkie Windows Defender (wdboot, wdfilter, wdnisdrv, wdnissvc i windefend) powinny być w stanie domyślnym. Zmiana uruchamiania tych usług jest nieobsługiwana i może spowodować ponowne zaimportowanie systemu.
   >
   > Przykład konfiguracji domyślnych dla oprogramowania WdBoot i WdFilter:
   >
   > - `<Key Path="SYSTEM\CurrentControlSet\Services\WdBoot"><KeyValue Value="0" ValueKind="DWord" Name="Start"/></Key>`
   > - `<Key Path="SYSTEM\CurrentControlSet\Services\WdFilter"><KeyValue Value="0" ValueKind="DWord" Name="Start"/></Key>`

## <a name="troubleshoot-onboarding-issues"></a>Rozwiązywanie problemów z dołączaniem 

> [!NOTE]
> Poniższe wskazówki dotyczące rozwiązywania problemów mają zastosowanie tylko w Windows Server 2016 i niższej.

Jeśli wystąpią problemy podczas dołączania serwera, przejdź przez poniższe kroki weryfikacji, aby rozwiązać możliwe problemy.


- [Upewnij Microsoft Monitoring Agent, że program MMA jest zainstalowany i skonfigurowany do zgłaszania danych czujnika do usługi](configure-server-endpoints.md)
- [Upewnij się, że ustawienia serwera proxy i łączności internetowej są poprawnie skonfigurowane](configure-server-endpoints.md)

Konieczne może być również sprawdzenie następujących czynności:

- Sprawdź, czy na karcie Procesy w Menedżerze Ochrona punktu końcowego w usłudze Microsoft Defender jest uruchomiona **usługa zarządzania procesami**. Przykład:

  :::image type="content" source="images/atp-task-manager.png" alt-text="Widok procesu z uruchomionym Ochrona punktu końcowego w usłudze Microsoft Defender Proces" lightbox="images/atp-task-manager.png":::

- Sprawdź **Podgląd zdarzeń** \> **menedżerze** \> operacji Dzienniki aplikacji i usług, aby sprawdzić, czy nie występują jakieś błędy.

- W **chmurze** Usługi sprawdź, **czy Microsoft Monitoring Agent** na serwerze. Na przykład:

  :::image type="content" source="images/atp-services.png" alt-text="Usługi" lightbox="images/atp-services.png":::

- W **Microsoft Monitoring Agent** \> **Azure Log Analytics (OMS)** sprawdź obszar roboczy i sprawdź, czy jest uruchomiony stan.

  :::image type="content" source="images/atp-mma-properties.png" alt-text="Właściwości Microsoft Monitoring Agent projektu" lightbox="images/atp-mma-properties.png":::

- Sprawdź, czy urządzenia są odzwierciedlane na liście **Urządzenia w** portalu.

## <a name="confirming-onboarding-of-newly-built-devices"></a>Potwierdzanie doniania nowo utworzonych urządzeń

W niektórych przypadkach dołączanie jest wdrażane na nowo utworzonym urządzeniu, ale nie jest ukończone.

Poniższe czynności zawierają wskazówki dotyczące następującego scenariusza:

- Pakiet wdrażania na nowo utworzonych urządzeniach
- Czujnik nie uruchamia się, ponieważ OOBE (Out-of-box experience) lub pierwsze logowanie użytkownika nie zostało ukończone
- Urządzenie jest wyłączone lub ponownie uruchomione przed pierwszym logowaniem przez użytkownika końcowego
- W tym scenariuszu usługa SENSE nie zostanie uruchamiana automatycznie mimo wdrożenia pakietu wdrażania

> [!NOTE]
> Logowanie użytkownika po OOBE nie jest już wymagane, aby usługa SENSE uruchamiała się w następujących lub najnowszych wersjach programu Windows: Windows 10, wersja 1809 lub Windows Server 2019 lub Windows Server 2022 z aktualizacją zbiorczą aktualizacji z [22 kwietnia 2021](https://support.microsoft.com/kb/5001384) r. Windows 10, wersja 1909 z aktualizacją [z kwietnia 2021 r](https://support.microsoft.com/kb/5001396). Windows 10 2004/20H2 z aktualizacją pakietu zbiorczą z [28 kwietnia 2021 r](https://support.microsoft.com/kb/5001391). 


> [!NOTE]
> Poniższe kroki mają zastosowanie tylko w przypadku korzystania z Microsoft Endpoint Configuration Manager. Aby uzyskać więcej szczegółowych informacji na temat dołączania przy Microsoft Endpoint Configuration Manager, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender](/mem/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection).

1. Utwórz aplikację w aplikacji Microsoft Endpoint Configuration Manager.

   :::image type="content" source="images/mecm-1.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-1" lightbox="images/mecm-1.png":::

2. Wybierz **pozycję Ręcznie określ informacje o aplikacji**.

   :::image type="content" source="images/mecm-2.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-2" lightbox="images/mecm-2.png":::

3. Określ informacje o aplikacji, a następnie wybierz pozycję **Dalej**.

   :::image type="content" source="images/mecm-3.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-3" lightbox="images/mecm-3.png":::

4. Określ informacje o centrum oprogramowania, a następnie wybierz pozycję **Dalej**.

   :::image type="content" source="images/mecm-4.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-4" lightbox="images/mecm-4.png":::

5. Na **stronie Typy wdrażania** wybierz pozycję **Dodaj**.

   :::image type="content" source="images/mecm-5.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-5" lightbox="images/mecm-5.png":::

6. Wybierz **pozycję Ręcznie określ informacje o typie wdrożenia**, a następnie wybierz pozycję **Dalej**.

   :::image type="content" source="images/mecm-6.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-6" lightbox="images/mecm-6.png":::

7. Określ typ wdrożenia, a następnie wybierz pozycję **Dalej**.

   :::image type="content" source="images/mecm-7.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-7" lightbox="images/mecm-7.png":::

8. W **programie** \> **Instalacja zawartości** określ polecenie: `net start sense`.

   :::image type="content" source="images/mecm-8.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-8" lightbox="images/mecm-8.png":::

9. W **przypadku metody wykrywania** wybierz **pozycję Konfiguruj reguły, aby wykryć obecność tego** typu wdrożenia, a następnie wybierz pozycję **Dodaj klauzulę**.

   :::image type="content" source="images/mecm-9.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-9" lightbox="images/mecm-9.png":::

10. Określ następujące szczegóły reguły wykrywania, a następnie wybierz przycisk **OK**:

    :::image type="content" source="images/mecm-10.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-10" lightbox="images/mecm-10.png":::

11. W **przypadku metody wykrywania** wybierz pozycję **Dalej**.

    :::image type="content" source="images/mecm-11.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-11" lightbox="images/mecm-11.png":::

12. W **jęz**. użytkownika określ następujące informacje, a następnie wybierz pozycję **Dalej**:

    :::image type="content" source="images/mecm-12.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-12" lightbox="images/mecm-12.png":::

13. W **polecej** Wymagania wybierz przycisk **Dalej**.

    :::image type="content" source="images/mecm-13.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-13" lightbox="images/mecm-13.png":::

14. W **zależnościach** wybierz pozycję **Dalej**.

    :::image type="content" source="images/mecm-14.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-14" lightbox="images/mecm-14.png":::

15. W **programie Summary** wybierz pozycję **Next (Dalej**).

    :::image type="content" source="images/mecm-15.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-15" lightbox="images/mecm-15.png":::

16. W **2016** roku wybierz **pozycję Zamknij**.

    :::image type="content" source="images/mecm-16.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-16" lightbox="images/mecm-16.png":::

17. W **typach wdrażania** wybierz pozycję **Dalej**.

    :::image type="content" source="images/mecm-17.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-17" lightbox="images/mecm-17.png":::

18. W **programie Summary** wybierz pozycję **Next (Dalej**).

    :::image type="content" source="images/mecm-18.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-18" lightbox="images/mecm-18.png":::

    Zostanie wyświetlony stan: :::image type="content" source="images/mecm-19.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-19" lightbox="images/mecm-19.png":::

19. W **2016** roku wybierz **pozycję Zamknij**.

    :::image type="content" source="images/mecm-20.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-20" lightbox="images/mecm-20.png":::

20. Teraz możesz wdrożyć aplikację, klikając aplikację prawym przyciskiem myszy i wybierając pozycję **Wdeksuj**.

    :::image type="content" source="images/mecm-21.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-21" lightbox="images/mecm-21.png":::

21. W **ogólne** wybierz **pozycję Automatycznie rozpowszechniaj zawartość dla zależności i** **Przeglądaj**.

    :::image type="content" source="images/mecm-22.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-22" lightbox="images/mecm-22.png":::

22. W **treści wybierz** pozycję **Dalej**.

    :::image type="content" source="images/mecm-23.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-23" lightbox="images/mecm-23.png":::

23. W **ustawieniach wdrażania** wybierz pozycję **Dalej**.

    :::image type="content" source="images/mecm-24.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-24" lightbox="images/mecm-24.png":::

24. W **planowaniu** wybierz **opcję Jak najszybciej po dostępnym czasie**, a następnie wybierz pozycję **Dalej**.

    :::image type="content" source="images/mecm-25.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-25" lightbox="images/mecm-25.png":::

25. W **oknie Środowisko użytkownika** wybierz pozycję **Zat zatwierdzeniu zmian w terminie lub w oknie konserwacji (wymaga ponownego uruchomienia)** i wybierz pozycję **Dalej**.

    :::image type="content" source="images/mecm-26.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-26" lightbox="images/mecm-26.png":::

26. W **alertach** wybierz pozycję **Dalej**.

    :::image type="content" source="images/mecm-27.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-27" lightbox="images/mecm-27.png":::

27. W **programie Summary** wybierz pozycję **Next (Dalej**).

    :::image type="content" source="images/mecm-28.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-28" lightbox="images/mecm-28.png":::
      

    Zostanie wyświetlony stan :::image type="content" source="images/mecm-29.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-29" lightbox="images/mecm-29.png":::

28. W **2016** roku wybierz **pozycję Zamknij**.

    :::image type="content" source="images/mecm-30.png" alt-text="Konfiguracja Microsoft Endpoint Configuration Manager-30" lightbox="images/mecm-30.png":::

## <a name="related-topics"></a>Tematy pokrewne

- [Rozwiązywanie Ochrona punktu końcowego w usłudze Microsoft Defender](troubleshoot-mdatp.md)
- [Dołączanie urządzeń](onboard-configure.md)
- [Konfiguruj ustawienia serwera proxy urządzenia i połączenia internetowego](configure-proxy-internet.md)
