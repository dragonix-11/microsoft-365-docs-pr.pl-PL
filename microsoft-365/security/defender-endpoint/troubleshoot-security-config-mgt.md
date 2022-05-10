---
title: Rozwiązywanie problemów z dołączaniem związanych z usługą Security Management dla Ochrona punktu końcowego w usłudze Microsoft Defender
description: Rozwiązywanie problemów, które mogą wystąpić podczas dołączania urządzeń przy użyciu usługi Security Management dla Ochrona punktu końcowego w usłudze Microsoft Defender.
keywords: rozwiązywanie problemów z dołączaniem, dołączaniem, podglądem zdarzeń, zbieraniem danych i kompilacjami w wersji zapoznawczej, danymi czujników i diagnostyką
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
ms.openlocfilehash: e7b9e757f15663338f2e12c645cc3cb0b63ef34b
ms.sourcegitcommit: 4cd8be7c22d29100478dce225dce3bcdce52644d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2022
ms.locfileid: "65302250"
---
# <a name="troubleshoot-onboarding-issues-related-to-security-management-for-microsoft-defender-for-endpoint"></a>Rozwiązywanie problemów z dołączaniem związanych z usługą Security Management dla Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniach przy użyciu Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Zarządzanie zabezpieczeniami dla Ochrona punktu końcowego w usłudze Microsoft Defender to funkcja dla urządzeń, które nie są zarządzane przez Microsoft Endpoint Manager, Microsoft Intune lub Microsoft Endpoint Configuration Manager, aby odbierać konfiguracje zabezpieczeń dla Ochrona punktu końcowego w usłudze Microsoft Defender bezpośrednio z Endpoint Manager.
Aby uzyskać więcej informacji na temat zarządzania zabezpieczeniami dla Ochrona punktu końcowego w usłudze Microsoft Defender, zobacz [Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniach za pomocą Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration).

Aby uzyskać instrukcje dotyczące zarządzania zabezpieczeniami dla Ochrona punktu końcowego w usłudze Microsoft Defender dołączania, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender Zarządzanie konfiguracją zabezpieczeń](security-config-management.md)

To kompleksowe dołączanie zostało zaprojektowane tak, aby było bezproblemowe i nie wymaga danych wejściowych użytkownika. Jeśli jednak wystąpią problemy podczas dołączania, możesz wyświetlać błędy i rozwiązywać problemy z nimi na platformie Ochrona punktu końcowego w usłudze Microsoft Defender.

> [!NOTE]
> Jeśli masz problemy z przepływem dołączania nowych urządzeń, zapoznaj się z [Ochrona punktu końcowego w usłudze Microsoft Defender wymaganiami wstępnymi](/mem/intune/protect/mde-security-integration#prerequisites) i upewnij się, że są przestrzegane instrukcje dołączania.

Aby uzyskać więcej informacji na temat analizatora klienta, zobacz [Rozwiązywanie problemów z kondycją czujnika przy użyciu Ochrona punktu końcowego w usłudze Microsoft Defender Client Analyzer](/microsoft-365/security/defender-endpoint/overview-client-analyzer).

## <a name="registering-domain-joined-computers-with-azure-active-directory"></a>Rejestrowanie komputerów przyłączonych do domeny przy użyciu Azure Active Directory

Aby pomyślnie zarejestrować urządzenia w Azure Active Directory, należy upewnić się, że:

- Komputery mogą uwierzytelniać się za pomocą kontrolera domeny
- Komputery mają dostęp do następujących zasobów firmy Microsoft z sieci organizacji:
  - https://enterpriseregistration.windows.net
  - https://login.microsoftonline.com
  - https://device.login.microsoftonline.com
- Azure AD connect jest skonfigurowany do synchronizowania obiektów komputera. Domyślnie jednostki organizacyjne komputerów znajdują się w Azure AD zakresu synchronizacji połączenia. Jeśli obiekty komputera należą do określonych jednostek organizacyjnych , skonfiguruj jednostki organizacyjne do synchronizacji w Azure AD Połączenie. Aby dowiedzieć się więcej na temat synchronizowania obiektów komputerów przy użyciu Azure AD Połączenie, zobacz [Filtrowanie oparte na jednostkach organizacyjnych](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering#organizational-unitbased-filtering).

> [!IMPORTANT]
> Azure AD connect nie synchronizuje Windows Server 2012 obiektów komputera R2. Jeśli musisz zarejestrować je w usłudze Azure AD dla usługi Security Management dla Ochrona punktu końcowego w usłudze Microsoft Defender, musisz dostosować regułę synchronizacji Azure AD nawiązywania połączenia, aby uwzględnić te obiekty komputera w zakresie synchronizacji. Zobacz [Instrukcje dotyczące stosowania reguły przyłączania do komputera w Azure Active Directory Połączenie]().

> [!NOTE]
> Aby pomyślnie ukończyć przepływ dołączania i niezależnie od systemu operacyjnego urządzenia, stan Azure Active Directory urządzenia może ulec zmianie na podstawie stanu początkowego urządzeń:
>
> <br>
>
>|Uruchamianie stanu urządzenia|Nowy stan urządzenia|
>|---|---|
>|Już AADJ lub HAADJ|Pozostaje w niezmienionej postaci|
>|Nie dołączono do usługi AADJ ani przyłączania hybrydowego do Azure Active Directory (HAADJ) i przyłączonych do domeny|Urządzenie to HAADJ'd|
>|Nie przyłączono do domeny AADJ ani HAADJ + Nie|Urządzenie to AADJ'd|
>
> Gdzie AADJ reprezentuje Azure Active Directory Joined i HAADJ reprezentuje hybrydowe Azure Active Directory sprzężone.

## <a name="troubleshoot-errors-from-the-microsoft-defender-for-endpoint-portal"></a>Rozwiązywanie problemów z błędami w portalu Ochrona punktu końcowego w usłudze Microsoft Defender

Za pośrednictwem portalu Ochrona punktu końcowego w usłudze Microsoft Defender administratorzy zabezpieczeń mogą teraz rozwiązywać problemy z usługą Security Management na potrzeby dołączania Ochrona punktu końcowego w usłudze Microsoft Defender.

W obszarze **Spis urządzeń** **punktów końcowych** \> kolumna **Zarządzane przez została dodana** do filtrowania według kanału zarządzania (na przykład MEM).

:::image type="content" source="./images/device-inventory-mde-error.png" alt-text="Strona spisu urządzeń" lightbox="./images/device-inventory-mde-error.png":::

Aby wyświetlić listę wszystkich urządzeń, które nie powiodły się w procesie dołączania usługi Security Management dla Ochrona punktu końcowego w usłudze Microsoft Defender, przefiltruj tabelę według wartości **MDE-Error**.

Na liście wybierz określone urządzenie, aby wyświetlić szczegóły rozwiązywania problemów w panelu bocznym, wskazując główną przyczynę błędu i odpowiednią dokumentację.


:::image type="content" source="./images/secconfig-mde-error.png" alt-text="Kryteria filtru zastosowane na stronie spisu urządzeń" lightbox="./images/secconfig-mde-error.png":::

## <a name="run-microsoft-defender-for-endpoint-client-analyzer-on-windows"></a>Uruchamianie analizatora klienta Ochrona punktu końcowego w usłudze Microsoft Defender na Windows

Rozważ uruchomienie analizatora klienta w punktach końcowych, które nie mogą ukończyć przepływu zarządzania zabezpieczeniami w celu Ochrona punktu końcowego w usłudze Microsoft Defender dołączania. Aby uzyskać więcej informacji na temat analizatora klienta, zobacz [Rozwiązywanie problemów z kondycją czujnika przy użyciu Ochrona punktu końcowego w usłudze Microsoft Defender Client Analyzer](overview-client-analyzer.md).

Plik wyjściowy analizatora klienta (Results.htm analizatora klienta MDE) może dostarczyć informacji dotyczących rozwiązywania problemów z kluczem:

- Sprawdź, czy system operacyjny urządzenia jest w zakresie zarządzania zabezpieczeniami dla przepływu dołączania Ochrona punktu końcowego w usłudze Microsoft Defender w sekcji **Ogólne szczegóły urządzenia**
- Sprawdź, czy urządzenie zostało pomyślnie zarejestrowane w celu Azure Active Directory w **szczegółach zarządzania konfiguracją urządzeń**

  :::image type="content" source="images/client-analyzer-results.png" alt-text="Wyniki analizatora klienta" lightbox="images/client-analyzer-results.png":::

W sekcji **Szczegółowe wyniki** raportu analizator klienta zawiera również praktyczne wskazówki.

> [!TIP]
> Upewnij się, że sekcja Szczegółowe wyniki raportu nie zawiera żadnych "błędów" i upewnij się, że przejrzyj wszystkie komunikaty "Ostrzeżenie".

Na przykład w ramach przepływu dołączania usługi Security Management jest wymagane, aby identyfikator dzierżawy Azure Active Directory w dzierżawie Ochrona punktu końcowego w usłudze Microsoft Defender był zgodny z identyfikatorem dzierżawy protokołu SCP wyświetlanym w sekcji **Szczegóły zarządzania konfiguracją urządzeń** w raportach. W razie potrzeby dane wyjściowe raportu zalecają przeprowadzenie tej weryfikacji.

:::image type="content" source="images/detailed-results.png" alt-text="Strona wyświetlająca szczegółowe wyniki" lightbox="images/detailed-results.png"

## <a name="general-troubleshooting"></a>Ogólne rozwiązywanie problemów

Jeśli nie możesz zidentyfikować dołączonego urządzenia w AAD lub MEM i nie wystąpił błąd podczas rejestracji, sprawdzenie klucza `Computer\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\SenseCM\\EnrollmentStatus` rejestru może dostarczyć dodatkowych informacji dotyczących rozwiązywania problemów.

:::image type="content" source="images/enrollment-status.png" alt-text="Strona ze stanem rejestracji" lightbox="images/enrollment-status.png":::

W poniższej tabeli wymieniono błędy i wskazówki dotyczące tego, co należy wypróbować/sprawdzić, aby rozwiązać problem z błędem. Pamiętaj, że lista błędów nie jest kompletna i jest oparta na typowych/typowych błędach napotykanych przez klientów w przeszłości:

<br>

****

|Kod błędu|Stan rejestracji|Akcje administratora|
|---|---|---|
|`5-9`,`11-12`, `26-33`|Błąd ogólny|Urządzenie zostało pomyślnie dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender. Wystąpił jednak błąd w przepływie zarządzania konfiguracją zabezpieczeń. Może to być spowodowane tym, że urządzenie nie spełnia [wymagań wstępnych dotyczących kanału zarządzania Ochrona punktu końcowego w usłudze Microsoft Defender](security-config-management.md). Uruchomienie [analizatora klienta](https://aka.ms/BetaMDEAnalyzer) na urządzeniu może pomóc w zidentyfikowaniu głównej przyczyny problemu. Jeśli to nie pomoże, skontaktuj się z pomocą techniczną.|
|`13-14`,`20`,`24`,`25`|Problem z łącznością|Urządzenie zostało pomyślnie dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender. Wystąpił jednak błąd w przepływie zarządzania konfiguracją zabezpieczeń, który może być spowodowany problemem z łącznością. Sprawdź, czy [punkty końcowe Azure Active Directory i Microsoft Endpoint Manager](security-config-management.md#connectivity-requirements) są otwierane w zaporze.|
|`10`,`42`|Ogólny błąd sprzężenia hybrydowego|Urządzenie zostało pomyślnie dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender. Wystąpił jednak błąd w przepływie zarządzania konfiguracją zabezpieczeń i system operacyjny nie mógł wykonać sprzężenia hybrydowego. [Rozwiązywanie problemów z hybrydowymi urządzeniami przyłączonymi do Azure Active Directory](/azure/active-directory/devices/troubleshoot-hybrid-join-windows-current) w celu rozwiązywania problemów z błędami przyłączania hybrydowego na poziomie systemu operacyjnego.|
|`15`|Niezgodność dzierżawy|Urządzenie zostało pomyślnie dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender. Wystąpił jednak błąd w przepływie zarządzania konfiguracją zabezpieczeń, ponieważ identyfikator dzierżawy Ochrona punktu końcowego w usłudze Microsoft Defender jest niezgodny z identyfikatorem dzierżawy Azure Active Directory. Upewnij się, że identyfikator dzierżawy Azure Active Directory z dzierżawy usługi Defender for Endpoint jest zgodny z identyfikatorem dzierżawy we wpisie SCP domeny. Aby uzyskać więcej informacji, [rozwiąż problemy z dołączaniem związane z usługą Security Management dla Ochrona punktu końcowego w usłudze Microsoft Defender](troubleshoot-security-config-mgt.md).|
|`16`,`17`|Błąd hybrydowy — punkt połączenia usługi|Urządzenie zostało pomyślnie dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender. Jednak rekord punktu połączenia usługi (SCP) nie jest poprawnie skonfigurowany i nie można przyłączyć urządzenia do Azure AD. Może to być spowodowane tym, że protokół SCP został skonfigurowany do dołączania Enterprise usługi DRS. Upewnij się, że punkty rekordu SCP AAD i SCP zostały skonfigurowane zgodnie z najlepszymi rozwiązaniami. Aby uzyskać więcej informacji, zobacz [Konfigurowanie punktu połączenia usługi](/azure/active-directory/devices/hybrid-azuread-join-manual#configure-a-service-connection-point).|
|`18`|Błąd certyfikatu|Urządzenie zostało pomyślnie dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender. Wystąpił jednak błąd w przepływie zarządzania konfiguracją zabezpieczeń z powodu błędu certyfikatu urządzenia. Certyfikat urządzenia należy do innej dzierżawy. Sprawdź, czy podczas tworzenia [profilów zaufanych certyfikatów](/mem/intune/protect/certificates-trusted-root#create-trusted-certificate-profiles) są stosowane najlepsze rozwiązania.|
|`36`|Błąd interfejsu API LDAP|Urządzenie zostało pomyślnie dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender. Wystąpił jednak błąd w przepływie zarządzania konfiguracją zabezpieczeń z powodu błędnej konfiguracji w AAD Połączenie. Aby określić, co uniemożliwia zarejestrowanie urządzenia w AAD, rozważ uruchomienie [narzędzia do rozwiązywania problemów z rejestracją urządzeń](/samples/azure-samples/dsregtool/dsregtool). W przypadku Windows Server 2012 R2 uruchom [dedykowane instrukcje rozwiązywania problemów](/azure/active-directory/devices/troubleshoot-hybrid-join-windows-legacy).  |
|`37`|Problem z synchronizacją lokalną|Urządzenie zostało pomyślnie dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender. Wystąpił jednak błąd w przepływie zarządzania konfiguracją zabezpieczeń z powodu błędnej konfiguracji w AAD Połączenie. Aby określić, co uniemożliwia zarejestrowanie urządzenia w AAD, rozważ uruchomienie [narzędzia do rozwiązywania problemów z rejestracją urządzeń](/samples/azure-samples/dsregtool/dsregtool). W przypadku Windows Server 2012 R2 uruchom [dedykowane instrukcje rozwiązywania problemów](/azure/active-directory/devices/troubleshoot-hybrid-join-windows-legacy). |
|`38`,`41`|Błąd DNS|Urządzenie zostało pomyślnie dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender. Wystąpił jednak błąd w przepływie zarządzania konfiguracją zabezpieczeń z powodu błędu DNS. Sprawdź ustawienia połączenia internetowego i/lub DNS na urządzeniu. Nieprawidłowe ustawienia DNS mogą znajdować się po stronie stacji roboczej. Usługa Active Directory wymaga użycia domeny DNS do prawidłowego działania (a nie adresu routera). Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z dołączaniem związanych z usługą Security Management dla Ochrona punktu końcowego w usłudze Microsoft Defender](troubleshoot-security-config-mgt.md).|
|`40`|Problem z synchronizacją zegara|Urządzenie zostało pomyślnie dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender. Wystąpił jednak błąd w przepływie zarządzania konfiguracją zabezpieczeń. Sprawdź, czy zegar jest ustawiony poprawnie i jest synchronizowany na urządzeniu, na którym występuje błąd.|

## <a name="azure-active-directory-runtime-troubleshooting"></a>rozwiązywanie problemów ze środowiskami uruchomieniami Azure Active Directory

### <a name="azure-active-directory-runtime"></a>środowisko uruchomieniowe Azure Active Directory

Głównym mechanizmem rozwiązywania problemów Azure Active Directory Runtime (AADRT) jest zbieranie śladów debugowania. Azure Active Directory środowisko uruchomieniowe na Windows używa **dostawcy ETW o identyfikatorze bd67e65c-9cc2-51d8-7399-0bb9899e75c1**. Ślady ETW muszą być przechwytywane przy użyciu reprodukcji błędu (na przykład w przypadku niepowodzenia sprzężenia należy włączyć ślady na czas obejmujący wywołania interfejsów API AADRT w celu przeprowadzenia sprzężenia).

Zobacz poniżej, aby zapoznać się z typowym błędem w dzienniku AADRT i jak go odczytać:

:::image type="content" source="images/event-properties.png" alt-text="Strona właściwości zdarzenia" lightbox="images/event-properties.png":::

Z informacji zawartych w komunikacie można w większości przypadków zrozumieć, jaki błąd wystąpił, jaki interfejs API Win32 zwrócił błąd (jeśli ma zastosowanie), jaki adres URL (jeśli ma zastosowanie) został użyty i jakie AAD napotkano błąd interfejsu API środowiska uruchomieniowego.

## <a name="instructions-for-applying-computer-join-rule-in-aad-connect"></a>Instrukcje dotyczące stosowania reguły przyłączania do komputera w AAD Połączenie

W przypadku usługi Security Management dla Ochrona punktu końcowego w usłudze Microsoft Defender na komputerach przyłączonych do domeny Windows Server 2012 R2 wymagana jest aktualizacja reguły synchronizacji Azure AD Połączenie "In from AD-Computer Join". Można to osiągnąć, klonując i modyfikując regułę, co spowoduje wyłączenie oryginalnej reguły "In from AD - Computer Join". Azure AD Połączenie domyślnie oferuje to środowisko do wprowadzania zmian w regułach wbudowanych.

> [!NOTE]
>Te zmiany należy zastosować na serwerze, na którym działa AAD Połączenie. Jeśli wdrożono wiele wystąpień AAD Połączenie, te zmiany muszą być stosowane do wszystkich wystąpień.

1. Otwórz aplikację Edytor reguł synchronizacji z menu Start. Na liście reguł znajdź regułę o nazwie **In z usługi AD — przyłączanie do komputera**. **Zanotuj wartość w kolumnie "Pierwszeństwo" dla tej reguły.**

   :::image type="content" source="images/57ea94e2913562abaf93749d306dd6cf.png" alt-text="Edytor reguł synchronizacji" lightbox="images/57ea94e2913562abaf93749d306dd6cf.png":::

2. Po wyróżnieniu reguły **In from AD – Computer Join (In from AD – Computer Join** ) wybierz pozycję **Edytuj**. W oknie dialogowym **Edytowanie potwierdzenia reguły zarezerwowanej** wybierz pozycję **Tak**.

   :::image type="content" source="images/8854440d6180a5580efda24110551c68.png" alt-text="Strona potwierdzenia edytowania reguły zarezerwowanej" lightbox="images/8854440d6180a5580efda24110551c68.png":::

3. Zostanie wyświetlone okno **Edytowanie reguły synchronizacji ruchu przychodzącego** . Zaktualizuj opis reguły, aby pamiętać, że Windows Server 2012R2 zostanie zsynchronizowany przy użyciu tej reguły. Pozostaw wszystkie inne opcje bez zmian z wyjątkiem wartości Pierwszeństwo. Wprowadź wartość pierwszeństwa, która jest wyższa niż wartość z oryginalnej reguły (jak pokazano na liście reguł).

   :::image type="content" source="images/ee0f29162bc3f2fbe666c22f14614c45.png" alt-text="Strona Edytowanie reguły synchronizacji ruchu przychodzącego, na której wprowadza się wartości" lightbox="images/ee0f29162bc3f2fbe666c22f14614c45.png":::

4. Wybierz pozycję **Dalej** trzy razy. Spowoduje to przejście do sekcji "Przekształcenia" reguły. Nie wprowadzaj żadnych zmian w sekcjach "Filtr określania zakresu" i "Reguły sprzężenia" reguły. Teraz powinna zostać wyświetlona sekcja "Przekształcenia".

   :::image type="content" source="images/296f2c2a705e41233631c3784373bc23.png" alt-text="Reguła synchronizacji ruchu przychodzącego" lightbox="images/296f2c2a705e41233631c3784373bc23.png":::

5. Przewiń do dołu listy przekształceń. Znajdź przekształcenie atrybutu **cloudFiltered** . W polu tekstowym w kolumnie **Źródło** zaznacz cały tekst (Control-A) i usuń go. Pole tekstowe powinno być teraz puste.

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

7. Wybierz pozycję **Zapisz** , aby zapisać nową regułę.

> [!NOTE]
> Po wprowadzeniu tej zmiany reguły wymagana będzie pełna synchronizacja usługi Active Directory. W przypadku dużych środowisk zaleca się zaplanowanie tej zmiany reguły i pełną synchronizację w okresach ciszy lokalnej usługi Active Directory.

## <a name="related-topic"></a>Temat pokrewny

- [Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniach przy użyciu Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
