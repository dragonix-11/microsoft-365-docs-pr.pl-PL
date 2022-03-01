---
title: Rozwiązywanie problemów z dołączaniem związanych z zarządzaniem zabezpieczeniami dla programu Microsoft Defender dla punktu końcowego
description: Rozwiązywanie problemów, które mogą się pojawić podczas korzystania z urządzeń przy użyciu zarządzania zabezpieczeniami dla programu Microsoft Defender for Endpoint.
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
ms.openlocfilehash: d6c3beb5a33a6d2323159917944e0f069b02035e
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2022
ms.locfileid: "63013266"
---
# <a name="troubleshoot-onboarding-issues-related-to-security-management-for-microsoft-defender-for-endpoint"></a>Rozwiązywanie problemów z dołączaniem związanych z zarządzaniem zabezpieczeniami dla programu Microsoft Defender dla punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Zarządzanie programem Microsoft Defender for Endpoint na urządzeniach za pomocą Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Zarządzanie zabezpieczeniami dla programu Microsoft Defender for Endpoint to funkcja urządzeń, które nie są zarządzane przez Microsoft Endpoint Manager, Microsoft Intune lub Microsoft Endpoint Configuration Manager , aby odbierać konfiguracje zabezpieczeń programu Microsoft Defender dla punktu końcowego bezpośrednio Endpoint Manager.
Aby uzyskać więcej informacji na temat zarządzania zabezpieczeniami dla programu Microsoft Defender dla punktu końcowego, zobacz Zarządzanie programem [Microsoft Defender dla punktu końcowego na urządzeniach z systemem Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration).

Aby uzyskać instrukcje dotyczące zarządzania zabezpieczeniami dla programu Microsoft Defender dla punktu końcowego, zobacz [Program Microsoft Defender for Endpoint Security Configuration Management](security-config-management.md)

To end-to-end onboarding jest zaprojektowane jako nieumyślne i nie wymaga od użytkowników danych wejściowych. Jednak jeśli napotkasz problemy podczas dołączania, możesz wyświetlić błędy i rozwiązać je w obrębie platformy Microsoft Defender for Endpoint.

> [!NOTE]
> Jeśli masz problemy z przepływem dołączania nowych urządzeń, przejrzyj wymagania wstępne programu [Microsoft Defender](/mem/intune/protect/mde-security-integration#prerequisites) dla punktu końcowego i upewnij się, że zostały spełnione instrukcje dotyczące dołączania.

Aby uzyskać więcej informacji na temat analizatora klientów, zobacz Rozwiązywanie problemów z [kondycją czujnika przy użyciu programu Microsoft Defender for Endpoint Client Analyzer](/microsoft-365/security/defender-endpoint/overview-client-analyzer).

## <a name="registering-domain-joined-computers-with-azure-active-directory"></a>Rejestrowanie komputerów przyłączona do domeny w u Azure Active Directory

Aby pomyślnie zarejestrować urządzenia Azure Active Directory, musisz upewnić się, że:

- Komputery mogą uwierzytelniać się przy użyciu kontrolera domeny
- Komputery mają dostęp do następujących zasobów firmy Microsoft w obrębie sieci organizacji:
  - https://enterpriseregistration.windows.net
  - https://login.microsoftonline.com
  - https://device.login.microsoftonline.com
- Narzędzie Azure AD Connect jest skonfigurowane do synchronizacji obiektów na komputerze. Domyślnie rozmiary użytkowników komputerów znajdują się w zakresie synchronizacji Usługi Azure AD Connect. Jeśli obiekty komputerów należą do określonych jednostek organizacyjnych, skonfiguruj jednostki organizacyjne do synchronizacji w usłudze Azure AD Połączenie. Aby dowiedzieć się więcej na temat synchronizowania obiektów komputera przy użyciu usługi Azure AD Połączenie, zobacz Filtrowanie [oparte na jednostkach organizacyjnych](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering#organizational-unitbased-filtering).

> [!IMPORTANT]
> Narzędzie Azure AD Connect nie synchronizuje Windows Server 2012 obiektami komputera W2. Jeśli chcesz je zarejestrować w usłudze Azure AD for Security Management for Microsoft Defender for Endpoint, musisz dostosować regułę synchronizacji usługi Azure AD Connect, aby uwzględnić te obiekty komputerów w zakresie synchronizacji. Zobacz [Instrukcje dotyczące stosowania reguły dołączania do komputera w programie Azure Active Directory Połączenie]().

> [!NOTE]
> Aby pomyślnie ukończyć przepływ dołączania, niezależnie od systemu operacyjnego urządzenia, Azure Active Directory stan urządzenia może się zmienić w zależności od stanu początkowego urządzenia:
>
> <br>
>
>|Stan urządzenia początkowego|Stan nowego urządzenia|
>|---|---|
>|Już AADJ lub HAADJ|Pozostają bez mów|
>|Nie AADJ ani Hybrid Azure Active Directory Join (HAADJ) + Domain joined|Urządzenie to HAADJ|
>|Nie AADJ ani HAADJ + Nie dołączyć do domeny|Urządzenie to AADJ|
>
> Gdzie AADJ reprezentuje Azure Active Directory sprzężenia, a HAADJ reprezentuje model Azure Active Directory sprzężenia.

## <a name="troubleshoot-errors-from-the-microsoft-defender-for-endpoint-portal"></a>Rozwiązywanie problemów z portalem programu Microsoft Defender dla punktu końcowego

Za pośrednictwem portalu programu Microsoft Defender for Endpoint administratorzy zabezpieczeń mogą teraz rozwiązywać problemy z zarządzaniem zabezpieczeniami dla programu Microsoft Defender na potrzeby dołączania do punktu końcowego.

W **spisie urządzeń** \> **punktów końcowych** dodano kolumnę Zarządzane **przez** do filtrowania według kanału zarządzania (na przykład MEM).

:::image type="content" alt-text="Obraz strony spisu urządzeń" source="./images/device-inventory-mde-error.png":::

Aby wyświetlić listę wszystkich urządzeń, na których nie powiodło się przetwarzanie zarządzania zabezpieczeniami dla programu Microsoft Defender w trakcie procesu dołączania do punktu końcowego, przefiltruj tabelę według **błędu MDE**.

Wybierz z listy konkretne urządzenie, aby wyświetlić szczegóły rozwiązywania problemów w panelu bocznym, wskaż główną przyczynę błędu i odpowiednią dokumentację.

:::image type="content" alt-text="Obraz filtrowanych stron w spisie urządzeń" source="./images/secconfig-mde-error.png":::

## <a name="run-microsoft-defender-for-endpoint-client-analyzer-on-windows"></a>Uruchom program Microsoft Defender for Endpoint Client Analyzer na Windows

Rozważ uruchomienie Analizatora klienta dla punktów końcowych, które nie mogą ukończyć zarządzania zabezpieczeniami dla programu Microsoft Defender dla przepływu dołączania do punktu końcowego. Aby uzyskać więcej informacji na temat analizatora klientów, zobacz Rozwiązywanie problemów z [kondycją czujnika przy użyciu programu Microsoft Defender for Endpoint Client Analyzer](overview-client-analyzer.md).

Plik wyjściowy Analizatora klienta (analizator klienta MDE Results.htm) może dostarczyć kluczowych informacji dotyczących rozwiązywania problemów:

- Sprawdzanie, czy system operacyjny urządzenia ma zakres zarządzania zabezpieczeniami dla programu Microsoft Defender for Endpoint (przepływ dołączania punktu końcowego) w **sekcji Ogólne szczegóły** urządzenia
- Sprawdzanie, czy urządzenie zostało pomyślnie zarejestrowane w u Azure Active Directory **Szczegóły zarządzania konfiguracją urządzenia**

    ![Obraz wyników analizatora klienta](images/client-analyzer-results.png)

W sekcji **Szczegółowe wyniki** raportu Analizator klienta udostępnia również wskazówki z akcjami.

> [!TIP]
> Upewnij się, że sekcja Szczegółowe wyniki raportu nie zawiera żadnych komunikatów "Błędy" i przejrzyj wszystkie komunikaty "Ostrzeżenie".

Na przykład w ramach przepływu dołączania zarządzania zabezpieczeniami identyfikator dzierżawy usługi Azure Active Directory w dzierżawie punktów końcowych usługi Microsoft Defender jest wymagany do dopasowania identyfikatora dzierżawy SCP wyświetlanego w sekcji Szczegóły zarządzania konfiguracją urządzeń w **raportach.** Jeśli jest to istotne, przeprowadzenie tej weryfikacji będzie zalecane w wynikach raportu.

![Obraz szczegółowych wyników](images/detailed-results.png)

## <a name="general-troubleshooting"></a>Ogólne rozwiązywanie problemów

Jeśli nie udało Ci się zidentyfikować urządzenia w urządzeniu w programie AAD lub MEM i nie został wyświetlony komunikat o błędzie podczas rejestracji, `Computer\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\SenseCM\\EnrollmentStatus` sprawdzenie klucza rejestru może dostarczyć dodatkowych informacji dotyczących rozwiązywania problemów.

:::image type="content" alt-text="Obraz stanu rejestracji." source="images/enrollment-status.png":::

W poniższej tabeli wymieniono błędy i wskazówki dotyczące czynności sprawdzanych w celu rozwiązania tego błędu. Lista błędów nie jest pełna i jest oparta na typowych/typowych błędach występujących u klientów w przeszłości:

<br>

****

|Kod błędu|Stan rejestracji|Akcje administratora|
|---|---|---|
|`5-9`,`11-12`, `26-33`|Błąd ogólny|Urządzenie zostało pomyślnie dołoowane do programu Microsoft Defender for Endpoint. Wystąpił jednak błąd w przepływie zarządzania konfiguracją zabezpieczeń. Może to być spowodowane tym, że urządzenie nie spełnia wymagań wstępnych programu [Microsoft Defender dla kanału zarządzania punktami końcowymi](security-config-management.md). Uruchomienie [Analizatora klienta](https://aka.ms/BetaMDEAnalyzer) na urządzeniu może pomóc w zidentyfikowaniu głównej przyczyny problemu. Jeśli to nie pomoże, skontaktuj się z pomocą techniczną.|
|`13-14`,`20`,`24`,`25`|Problem z łącznością|Urządzenie zostało pomyślnie dołoowane do programu Microsoft Defender for Endpoint. Wystąpił jednak błąd w przepływie zarządzania konfiguracją zabezpieczeń, który mógł być spowodowany problemem z łącznością. Upewnij się, [że Azure Active Directory i Microsoft Endpoint Manager są](security-config-management.md#connectivity-requirements) otwarte w zaporze.|
|`10`,`42`|Błąd ogólnego sprzężenia hybrydowego|Urządzenie zostało pomyślnie dołoowane do programu Microsoft Defender for Endpoint. Wystąpił jednak błąd w przepływie zarządzania konfiguracją zabezpieczeń i system operacyjny nie może wykonać sprzężenia hybrydowego. Rozwiązywanie [problemów z Azure Active Directory sprzężeniami](/azure/active-directory/devices/troubleshoot-hybrid-join-windows-current) hybrydowymi na urządzeniach na potrzeby rozwiązywania problemów z błędami sprzężenia hybrydowego na poziomie systemu operacyjnego.|
|`15`|Niezgodność dzierżaw|Urządzenie zostało pomyślnie dołoowane do programu Microsoft Defender for Endpoint. Wystąpił jednak błąd w przepływie zarządzania konfiguracją zabezpieczeń, ponieważ identyfikator dzierżawy programu Microsoft Defender dla punktu końcowego nie jest Azure Active Directory identyfikatorem dzierżawy. Upewnij się, że Azure Active Directory identyfikatora dzierżawy usługi Defender dla dzierżawy punktu końcowego jest taki, jak identyfikator dzierżawy we wpisie SCP domeny. Aby uzyskać więcej szczegółowych informacji, rozwiązywanie problemów związanych z dołączaniem [do usługi Zarządzanie zabezpieczeniami dla programu Microsoft Defender for Endpoint](troubleshoot-security-config-mgt.md).|
|`16`,`17`|Błąd hybrydowy — punkt połączenia usługi|Urządzenie zostało pomyślnie dołoowane do programu Microsoft Defender for Endpoint. Jednak rekord punktu połączenia usługi (SCP) nie jest prawidłowo skonfigurowany i urządzenia nie można dołączyć do usługi Azure AD. Może to być spowodowane tym, że oznaczanie SCP jest skonfigurowane do dołączania do Enterprise DRS. Upewnij się, że rekord SCP wskazuje AAD, a SCP jest skonfigurowany zgodnie z najlepszymi rozwiązaniami. Aby uzyskać więcej informacji, [zobacz Konfigurowanie punktu połączenia usługi](/azure/active-directory/devices/hybrid-azuread-join-manual#configure-a-service-connection-point).|
|`18`|Błąd certyfikatu|Urządzenie zostało pomyślnie dołoowane do programu Microsoft Defender for Endpoint. Wystąpił jednak błąd w przepływie zarządzania konfiguracją zabezpieczeń z powodu błędu certyfikatu urządzenia. Certyfikat urządzenia należy do innej dzierżawy. Podczas tworzenia zaufanych profilów certyfikatów należy sprawdzić, czy są stosowane [najlepsze rozwiązania](/mem/intune/protect/certificates-trusted-root#create-trusted-certificate-profiles).|
|`36`|Błąd interfejsu API LDAP|Urządzenie zostało pomyślnie dołoowane do programu Microsoft Defender for Endpoint. Wystąpił jednak błąd w przepływie zarządzania konfiguracją zabezpieczeń. Sprawdź topologię sieci i upewnij się, że jest dostępny interfejs API LDAP do pełnego żądania sprzężenia hybrydowego.|
|`37`|Problem z synchronizacją lokalną|Urządzenie zostało pomyślnie dołoowane do programu Microsoft Defender for Endpoint. Wystąpił jednak błąd w przepływie zarządzania konfiguracją zabezpieczeń. Spróbuj ponownie później. Jeśli to nie pomoże, zobacz Rozwiązywanie problemów z synchronizacją obiektów [z usługą Azure AD Połączenie synchronizacji](/azure/active-directory/hybrid/tshoot-connect-objectsync).|
|`38`,`41`|Błąd DNS|Urządzenie zostało pomyślnie dołoowane do programu Microsoft Defender for Endpoint. Wystąpił jednak błąd w przepływie zarządzania konfiguracją zabezpieczeń z powodu błędu DNS. Sprawdź połączenie internetowe i/lub ustawienia DNS na urządzeniu. Nieprawidłowe ustawienia DNS mogą być po stronie stacji roboczej. Usługa Active Directory wymaga poprawnego działania systemu DNS domeny (a nie adresu routera). Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów związanych z dołączaniem do usługi Zarządzanie zabezpieczeniami dla programu Microsoft Defender for Endpoint](troubleshoot-security-config-mgt.md).|
|`40`|Problem z synchronizacją zegara|Urządzenie zostało pomyślnie dołoowane do programu Microsoft Defender for Endpoint. Wystąpił jednak błąd w przepływie zarządzania konfiguracją zabezpieczeń. Sprawdź, czy zegar jest poprawnie ustawiony i zsynchronizowany na urządzeniu, na którym wystąpił błąd.|

## <a name="azure-active-directory-runtime-troubleshooting"></a>rozwiązywanie Azure Active Directory środowiska uruchomieniowego

### <a name="azure-active-directory-runtime"></a>Azure Active Directory środowiska uruchomieniowego

Głównym mechanizmem rozwiązywania problemów z Azure Active Directory Runtime (AADRT) jest zbieranie śladów debugowania. Azure Active Directory Runtime w Windows korzysta z dostawcy **ETW o identyfikatorze bd67e65c-9cc2-51d8-7399-0bb9899e75c1**. Śledzenia ETW należy przechwycić wraz z kopiowaniem niepowodzenia (na przykład w przypadku wystąpienia błędu sprzężenia należy włączyć śledzenia na czas trwania połączeń z interfejsami API AADRT w celu wykonania sprzężenia).

Poniżej przedstawiono typowy błąd w dzienniku AADRT i sposób odczytywania go:

![Obraz właściwości zdarzenia](images/event-properties.png)

Z informacji w tym komunikacie można w większości przypadków dowiedzieć się, na czym wystąpił błąd, jaki interfejs API Win32 zwrócił błąd (jeśli ma zastosowanie), jaki adres URL (jeśli ma zastosowanie) i jakie błędy interfejsu API środowiska AAD Runtime wystąpiły.

## <a name="instructions-for-applying-computer-join-rule-in-aad-connect"></a>Instrukcje dotyczące stosowania reguły dołączania do komputera w AAD Połączenie

W przypadku zarządzania zabezpieczeniami dla programu Microsoft Defender for Endpoint na komputerach przyłącznych do domeny Windows Server 2012 R2 potrzebna jest aktualizacja reguły synchronizacji usługi Azure AD Połączenie "In z AD-Computer Join". Można to osiągnąć, klonując i modyfikując regułę, co spowoduje wyłączenie oryginalnej reguły "W z usługi AD — dołączanie do komputera". Usługa Azure AD Połączenie domyślnie oferuje to środowisko do zmieniania wbudowanych reguł.

> [!NOTE]
>Te zmiany należy zastosować na serwerze, na AAD Połączenie jest uruchomiony. Jeśli masz wiele wystąpień AAD Połączenie, te zmiany należy zastosować do wszystkich wystąpień.

1. Otwórz aplikację Edytor reguł synchronizacji z menu Start. Na liście reguł odszukaj regułę o nazwie **W z usługi AD — Dołączanie do komputera**. **Zanotuj wartość tej reguły w kolumnie "Pierwszeństwo".**

    ![Obraz edytora reguł synchronizacji](images/57ea94e2913562abaf93749d306dd6cf.png)

2. Gdy reguła **Dołączanie do komputera jest** wyróżniona w oknie In from AD (W z usługi AD — Dołączanie do komputera), wybierz pozycję **Edit (Edytuj**). W **oknie dialogowym Edytowanie zastrzeżonej reguły potwierdzenia** wybierz pozycję **Tak**.

   ![Obraz potwierdzenia edytowania reguły zastrzeżonej](images/8854440d6180a5580efda24110551c68.png)

3. Zostanie **wyświetlone okno Edytowanie reguły synchronizacji ruchu przychodzącego** . Zaktualizuj opis reguły, aby pamiętać, że Windows Server 2012R2 zostanie zsynchronizowany przy użyciu tej reguły. Pozostaw wszystkie inne opcje bez zmian z wyjątkiem wartości Pierwszeństwo. Wprowadź wartość pierwszeństwa większą niż wartość oryginalnej reguły (jak widać na liście reguł).

   ![Obraz potwierdzenia](images/ee0f29162bc3f2fbe666c22f14614c45.png)

4. Wybierz **pozycję Dalej** trzy razy. Spowoduje to przejście do sekcji "Przekształcenia" reguły. Nie wprowadzaj żadnych zmian w sekcjach "Filtrowanie zakresu" i "Reguły dołączania" reguły. Teraz powinna zostać pokazana sekcja "Przekształcenia".

    ![Obraz reguły synchronizacji przychodzącej](images/296f2c2a705e41233631c3784373bc23.png)

5. Przewiń do dołu listy przekształceń. Znajdź przekształcenie dla **atrybutu cloudFiltered** . W polu tekstowym w **kolumnie Źródło** zaznacz cały tekst (control-A) i usuń go. Pole tekstowe powinno być teraz puste.

6. Wklej zawartość nowej reguły do pola tekstowego.

    ```command
    IIF(
      IsNullOrEmpty([userCertificate])
      ||
      (
        (InStr(UCase([operatingSystem]),"WINDOWS") > 0)
        &&
        (Left([operatingSystemVersion],2) = "6.")
        &&
        (Left([operatingSystemVersion],3) <> "6.3")
      )
      ||
      (
        (Left([operatingSystemVersion],3) = "6.3")
        &&
        (InStr(UCase([operatingSystem]),"WINDOWS") > 0)
        &&
        With(
          $validCerts,
          Where(
            $c,
            [userCertificate],
            IsCert($c) && CertNotAfter($c) > Now() && RegexIsMatch(CertSubject($c), "CN=[{]*" & StringFromGuid([objectGUID]) & "[}]*", "IgnoreCase")),
          Count($validCerts) = 0)
      ),
      True,
      NULL
    )
    ```

7. Wybierz **pozycję Zapisz** , aby zapisać nową regułę.

> [!NOTE]
> Po w związku z tą zmianą reguły będzie wymagana pełna synchronizacja usługi Active Directory. W dużych środowiskach zaleca się zaplanowanie tej zmiany reguły i pełnej synchronizacji podczas lokalnych okresów ciszy usługi Active Directory.

## <a name="related-topic"></a>Temat pokrewny

- [Zarządzanie programem Microsoft Defender for Endpoint na urządzeniach za pomocą Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
