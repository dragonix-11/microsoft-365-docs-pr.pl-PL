---
title: Konfigurowanie Microsoft 365 Defender na laboratorium próbnym lub w środowisku pilotażowym
description: Skonfiguruj Microsoft 365 Defender, na przykład program Microsoft Defender dla systemu Office 365, program Microsoft Defender dla tożsamości, Microsoft Cloud App Security i program Microsoft Defender dla punktu końcowego, w laboratorium próbnym lub środowisku pilotażowym.
keywords: konfigurowanie Microsoft 365 Defender próbnej, Microsoft 365 Defender konfiguracji wersji próbnej, konfigurowanie Microsoft 365 Defender pilotażowego, konfigurowanie Microsoft 365 Defender słupów; Microsoft 365 Defender i słupów
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: e50210f02d14be33c357517515d456318aac4bb6
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2021
ms.locfileid: "62959251"
---
# <a name="configure-microsoft-365-defender-pillars-for-your-trial-lab-or-pilot-environment"></a>Konfigurowanie Microsoft 365 Defender w laboratorium próbnym lub środowisku pilotażowym

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender


Tworzenie Microsoft 365 Defender próbnego lub pilotażowego i wdrażanie go jest procesem trzyfazowym:

|[![Etap 1. Przygotowywanie](../../media/phase-diagrams/prepare.png)](prepare-m365d-eval.md)<br/>[Etap 1. Przygotowywanie](prepare-m365d-eval.md) |[![Etap 2. Konfigurowanie](../../media/phase-diagrams/setup.png)](setup-m365deval.md)<br/>[Etap 2. Konfigurowanie](setup-m365deval.md) |![Etap 3. Wniesienie](../../media/phase-diagrams/onboard.png)<br/>Etap 3. Wniesienie | [![Powrót do programu pilotażowego](../../media/phase-diagrams/backtopilot.png)](m365d-pilot.md)<br/>[Powrót do podręcznika pilotażowego](m365d-pilot.md) |
|--|--|--|--|
|| |*Jesteś tutaj!* | |

Jesteś obecnie w fazie konfiguracji.

Przygotowanie jest kluczem do każdego pomyślnego wdrożenia. W tym artykule otrzymasz  przewodniki na temat punktów, które należy wziąć pod uwagę podczas przygotowywania się do wdrożenia programu Microsoft Defender dla punktu końcowego.

## <a name="microsoft-365-defender-pillars"></a>Microsoft 365 Defender i słupów
Microsoft 365 Defender składa się z czterech słupów. Chociaż jeden słupek może już stanowić wartość dla zabezpieczeń Twojej organizacji sieci, włączenie tych czterech Microsoft 365 Defender spowoduje, że Twoja organizacja będzie najbardziej wartościowa.

![Obraz of_Microsoft rozwiązania Defender 365 dla użytkowników, usługi Microsoft Defender dla tożsamości dla punktów końcowych programu Microsoft Defender, dla aplikacji w chmurze, usług Microsoft Cloud App Security i danych program Microsoft Defender dla komputerów Office 365](../../media/mtp/m365pillars.png)

W tej sekcji podano konfigurować:

- Usługa Microsoft Defender dla Office 365
- Microsoft Defender for Identity
- Microsoft Cloud App Security
- Ochrona punktu końcowego w usłudze Microsoft Defender

## <a name="configure-microsoft-defender-for-office-365"></a>Konfigurowanie usługi Microsoft Defender dla Office 365

> [!NOTE]
> Pomiń ten krok, jeśli masz już włączoną usługę Defender dla Office 365.

Istnieje moduł programu PowerShell o nazwie *Office 365 Advanced Threat Protection Recommended Configuration Analyzer (ORCA),* który ułatwia określenie niektórych z tych ustawień. Po uruchomieniu jako administrator w dzierżawie get-ORCAReport pomoże wygenerować ocenę ustawień ochrony przed spamem, wiadomości anti-phish i innych ustawień wiadomości. Możesz pobrać ten moduł z https://www.powershellgallery.com/packages/ORCA/.

1. Przejdź do [Office 365 Centrum &](https://protection.office.com/homepage) **zgodnościReat** >  **managementPolicy** > .

   ![Obraz of_Office strony zasad zarządzania zagrożeniami w Centrum & zabezpieczeń i zgodności z usługą 365](../../media/mtp-eval-32.png)

2. Kliknij **pozycję Ochrona przed wyłudzaniem** informacji, **wybierz pozycję Utwórz** i wpisz nazwę i opis zasad. Kliknij **Dalej**.

   ![Obraz of_Office strony zasad ochrony przed & wyłudzaniem informacji w Centrum zabezpieczeń & 365, na której można określić nazwę zasad](../../media/mtp-eval-33.png)

   > [!NOTE]
   > Edytuj zaawansowane zasady ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365. Zmień **zaawansowany próg wyłudzania informacji** **na 2 — agresywny**.

3. Kliknij menu **rozwijane Dodaj warunek** i wybierz domeny jako domenę adresata. Kliknij **Dalej**.

   ![Obraz of_Office stronie & zasad ochrony przed wyłudzaniem informacji w Centrum zabezpieczeń 365, na której można dodać warunek dla aplikacji](../../media/mtp-eval-34.png)

4. Przejrzyj ustawienia. Kliknij **pozycję Utwórz te zasady,** aby potwierdzić.

   ![Obraz of_Office stronie zasad ochrony przed wyłudzaniem informacji w Centrum zabezpieczeń & 365, gdzie można przejrzeć ustawienia i kliknąć przycisk Utwórz te zasady.](../../media/mtp-eval-35.png)

5. Wybierz **Sejf załączników** i wybierz opcję Włącz **atP dla SharePoint, OneDrive i Microsoft Teams** atp.

   ![Obraz of_Office strony Centrum zgodności & zabezpieczeń & 365, gdzie można włączyć atP dla sieci SharePoint, OneDrive i Microsoft Teams](../../media/mtp-eval-36.png)

6. Kliknij ikonę +, aby utworzyć nowe bezpieczne zasady załączników i zastosować je jako domenę adresata do swoich domen. Kliknij **Zapisz**.

   ![Obraz of_Office stronie Centrum zgodności & zabezpieczeń 365, na której można utworzyć nowe bezpieczne zasady załączników.](../../media/mtp-eval-37.png)

7. Następnie wybierz zasady **ołówka Sejf**, a następnie kliknij ikonę ołówka, aby edytować zasady domyślne.

8. Upewnij się, że **opcja Nie śledź** po kliknięciu przez użytkowników bezpiecznych linków nie jest zaznaczona, podczas gdy pozostałe opcje są zaznaczone. Aby [uzyskać szczegółowe Sejf, zobacz ustawienia linku](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365). Kliknij **Zapisz**.

   ![Obraz of_Office stronie Centrum zgodności & zabezpieczeń & 365, na której widać, że nie jest zaznaczona opcja Nie śledź po kliknięciu przez użytkowników opcji Bezpieczne](../../media/mtp-eval-38.png)

9. Następnie wybierz zasady **ochrony przed złośliwym** oprogramowaniem, wybierz domyślną i wybierz ikonę ołówka.

10. Kliknij **Ustawienia** pozycję **Tak i użyj domyślnego** tekstu powiadomień, aby włączyć funkcję **wykrywania złośliwego oprogramowania**. Włącz **filtr typowych typów** załączników. Kliknij **Zapisz**.

    ![Obraz of_Office 365 Security & Compliance Center, która pokazuje, że odpowiedź wykrywanie złośliwego oprogramowania jest włączona z domyślnym powiadomieniem i że jest włączony filtr typowych typów załączników](../../media/mtp-eval-39.png)

11. Przejdź do [Office 365 usługi & w Centrum](https://protection.office.com/homepage) >  zgodnościWyszukiwanie >  **dziennikaAudit** i włączanie inspekcji.

    ![Obraz of_Office stronie Centrum & zgodności usługi & 365, gdzie można włączyć przeszukiwanie dziennika inspekcji](../../media/mtp-eval-40.png)

12. Zintegruj usługę Microsoft Defender dla Office 365 z programem Microsoft Defender for Endpoint. Przejdź do [Office 365 centrum &](https://protection.office.com/homepage) >  zgodności Programu **SecurityThreat** **managementExplorer** >  i wybierz pozycję **Microsoft Defender for Endpoint Ustawienia** w prawym górnym rogu ekranu. W oknie dialogowym Połączenie usługi Defender for Endpoint włącz **usługę Połączenie do programu Microsoft Defender for Endpoint**.

    ![Obraz of_Office stronie Centrum & zabezpieczeń i zgodności usługi Microsoft Defender 365, gdzie można włączyć połączenie programu Microsoft Defender for Endpoint](../../media/mtp-eval-41.png)

## <a name="configure-microsoft-defender-for-identity"></a>Konfigurowanie usługi Microsoft Defender dla tożsamości

> [!NOTE]
> Pomiń ten krok, jeśli masz już włączoną usługę Microsoft Defender dla tożsamości

1. Przejdź do [Microsoft 365 Security Center i](https://security.microsoft.com/info) > **pozycję Więcej zasobówMicrosoft** >  **Defender for Identity**.

   ![Obraz of_Microsoft stronie Centrum zabezpieczeń usługi 365, na której jest dostępna opcja otwarcia usługi Microsoft Defender dla tożsamości](../../media/mtp-eval-42.png)

2. Kliknij **przycisk Utwórz** , aby uruchomić kreatora programu Microsoft Defender dla tożsamości.

   ![Obraz of_Microsoft kreatora usługi Defender dla tożsamości, na której należy kliknąć przycisk Utwórz](../../media/mtp-eval-43.png)

3. Wybierz **pozycję Podaj nazwę użytkownika i hasło, aby połączyć się z lasem usługi Active Directory**.

   ![Obraz of_Microsoft powitania usługi Defender dla tożsamości](../../media/mtp-eval-44.png)

4. Wprowadź swoje poświadczenia lokalne usługi Active Directory. Może to być dowolne konto użytkownika z dostępem do odczytu usługi Active Directory.

   ![Obraz of_Microsoft stronie usługi katalogowej usługi Defender for Identity, na której należy umieścić poświadczenia](../../media/mtp-eval-45.png)

5. Następnie wybierz pozycję **Download Sensor Setup (Pobierz konfigurację** czujnika) i przenieś plik do kontrolera domeny.

   ![Obraz of_Microsoft stronie usługi Defender for Identity, na której można wybrać pozycję Pobierz konfigurację czujnika](../../media/mtp-eval-46.png)

6. Wykonaj konfigurację czujnika tożsamości programu Microsoft Defender for Identity i rozpocznij wykonywanie czynności kreatora.

   ![Obraz of_Microsoft stronie usługi Defender for Identity, gdzie należy kliknąć przycisk dalej w celu obserwowania kreatora czujnika tożsamości programu Microsoft Defender](../../media/mtp-eval-47.png)

7. Kliknij **przycisk Dalej** w typie wdrożenia czujnika.

   ![Obraz of_Microsoft stronie Usługi Defender dla tożsamości, gdzie należy kliknąć przycisk dalej, aby przejść do następnej strony](../../media/mtp-eval-48.png)

8. Skopiuj klucz dostępu, ponieważ musisz wprowadzić go dalej w Kreatorze.

   ![Obraz of_the stronie czujnika, gdzie należy skopiować klucz dostępu, który należy wprowadzić na następnej stronie kreatora konfiguracji czujnika tożsamości programu Microsoft Defender](../../media/mtp-eval-49.png)

9. Skopiuj klawisz dostępu do Kreatora i kliknij pozycję **Zainstaluj**.

   ![Obraz of_Microsoft kreatora czujnika tożsamości usługi Defender dla tożsamości, na której należy podać klucz dostępu, a następnie kliknąć przycisk instalacji](../../media/mtp-eval-50.png)

10. Gratulacje! Pomyślnie skonfigurowano usługę Microsoft Defender for Identity na kontrolerze domeny.

    ![Obraz of_Microsoft ukończenia instalacji kreatora czujnika tożsamości usługi Defender for Identity, w którym należy kliknąć przycisk zakończ](../../media/mtp-eval-51.png)

11. W sekcji [ustawień usługi Microsoft Defender for Identity](https://go.microsoft.com/fwlink/?linkid=2040449) wybierz **Microsoft Defender for Endpoint **, a następnie włącz przełącznik. Kliknij **Zapisz**.

    ![Obraz of_the stronie ustawień usługi Microsoft Defender for Identity, gdzie należy włączyć przełącznik programu Microsoft Defender for Endpoint](../../media/mtp-eval-52.png)

## <a name="configure-microsoft-cloud-app-security"></a>Konfigurowanie Microsoft Cloud App Security

> [!NOTE]
> Pomiń ten krok, jeśli masz już włączoną Microsoft Cloud App Security.

1. Przejdź do [Microsoft 365 Centrum](https://security.microsoft.com/info) **zabezpieczeńWięcej** >  zasobów  >  Microsoft Cloud App Security.

   ![Obraz of_Microsoft strony Centrum zabezpieczeń usługi 365, na której można wyświetlić kartę Microsoft Cloud App i należy kliknąć przycisk Otwórz](../../media/mtp-eval-53.png)

2. Po wyświetleniu monitu o integrację usługi Microsoft Defender for Identity wybierz pozycję **Włącz integrację danych usługi Microsoft Defender for Identity**.

   ![Image of_the information prompt to integrate Microsoft Defender for Identity where you should select the Enable Microsoft Defender for Identity data integration link](../../media/mtp-eval-54.png)

   > [!NOTE]
   > Jeśli nie widzisz tej prośby, może to oznaczać, że integracja danych usługi Microsoft Defender dla tożsamości została już włączona. Jeśli jednak nie masz pewności, skontaktuj się z administratorem IT, aby potwierdzić.

3. Przejdź do **Ustawienia**, włącz przełącznik integracji z usługą **Microsoft Defender dla tożsamości**, a następnie kliknij przycisk **Zapisz**.

   ![Image of_the settings page where you should turn on the Microsoft Defender for Identity integration to Identityggle then click save](../../media/mtp-eval-55.png)

   > [!NOTE]
   > W przypadku nowych wystąpień usługi Microsoft Defender dla tożsamości ten przełącznik integracji jest automatycznie włączony. Przed rozpoczęciem następnego kroku upewnij się, że integracja z usługą Microsoft Defender for Identity została włączona.

4. W obszarze Ustawienia odnajdowania w chmurze wybierz pozycję **Microsoft Defender for Endpoint integration (Integracja z** programem Endpoint), a następnie włącz integrację. Kliknij **Zapisz**.

   ![Obraz of_the stronie Programu Microsoft Defender dla punktu końcowego, gdzie jest zaznaczone pole wyboru bloku aplikacji niewykonanych w programie Microsoft Defender for Endpoint. Kliknij przycisk zapisz.](../../media/mtp-eval-56.png)

5. W obszarze Ustawienia odnajdowania w chmurze wybierz **pozycję Wzbogacanie użytkowników**, a następnie włącz integrację z usługą Azure Active Directory.

   ![Obraz sekcji Wzbogacanie użytkownika, w której zaznaczone jest pole wyboru wzbogacenie Azure Active Directory nazwami użytkowników za pomocą Azure Active Directory nazwy użytkowników](../../media/mtp-eval-57.png)

## <a name="configure-microsoft-defender-for-endpoint"></a>Konfigurowanie programu Microsoft Defender dla punktu końcowego

> [!NOTE]
> Pomiń ten krok, jeśli masz już włączony program Microsoft Defender dla punktu końcowego.

1. Przejdź do [Microsoft 365 ZabezpieczeńWięcej](https://security.microsoft.com/info) >  **zasobów** >  **Centrum zabezpieczeń usługi Microsoft Defender**. Kliknij **przycisk Otwórz**.

   ![Obraz of_Microsoft usługi Defender Security Center na Microsoft 365 Centrum zabezpieczeń programu Microsoft 365](../../media/mtp-eval-58.png)

2. Postępuj zgodnie z kreatorem programu Microsoft Defender for Endpoint. Kliknij **Dalej**.

   ![Obraz of_the Centrum zabezpieczeń usługi Microsoft Defender kreatora powitania](../../media/mtp-eval-59.png)

3. Wybierz preferowaną lokalizację przechowywania danych, zasady przechowywania danych, rozmiar organizacji i zgodę na funkcje wersji Preview.

   ![Obraz of_the stronie wybierania kraju przechowywania danych, zasad przechowywania i rozmiaru organizacji. Po wybraniu przycisku kliknij przycisk dalej.](../../media/mtp-eval-60.png)

   > [!NOTE]
   > Później nie możesz zmienić niektórych ustawień, takich jak lokalizacja przechowywania danych.

   Kliknij **Dalej**.

4. Kliknij **przycisk Kontynuuj** , a usługa będzie zapewniać usługę Microsoft Defender dla dzierżawy punktu końcowego.

   ![Obraz of_the monitu o kliknięcie przycisku Kontynuuj w celu utworzenia wystąpienia chmury](../../media/mtp-eval-61.png)

5. Wdowaj punkty końcowe za pośrednictwem zasad grupy, Microsoft Endpoint Manager lub uruchamiając skrypt lokalny do usługi Microsoft Defender for Endpoint. Dla uproszczenia w tym przewodniku jest używany skrypt lokalny.

6. Kliknij **pozycję Pobierz pakiet** i skopiuj skrypt dołączania do punktów końcowych.

   ![Obraz of_page monitowanie o kliknięcie przycisku Pobierz pakiet w celu skopiowania skryptu dołączania do punktu końcowego lub końcowego](../../media/mtp-eval-62.png)

7. W punkcie końcowym uruchom skrypt dołączania jako administrator i wybierz pozycję Y.

   ![Obraz of_the wiersza polecenia, w którym jest uruchamiany skrypt dołączania, i wybierz pozycję Y, aby kontynuować](../../media/mtp-eval-63.png)

8. Gratulacje! Pierwszy punkt końcowy został przez Ciebie wnoszony.

   ![Obraz of_the wiersza polecenia, w którym jest uzyskiwanie potwierdzenia, że pierwszy punkt końcowy został przez Ciebie wnoszony. Naciśnij dowolny klawisz, aby kontynuować](../../media/mtp-eval-64.png)

9. Skopiuj test wykrywania z kreatora Programu Microsoft Defender dla punktu końcowego.

   ![Obraz of_the etap testu wykrywania, w którym należy kliknąć pozycję Kopiuj, aby skopiować skrypt testu wykrywania do wklejenia w wierszu polecenia](../../media/mtp-eval-65.png)

10. Skopiuj skrypt programu PowerShell do wiersza polecenia o podwyższonym poziomie uprawnień i uruchom go.

    ![Obraz of_command monitu o skopiowanie skryptu programu PowerShell do wiersza polecenia z podwyższonym poziomem uprawnień i uruchomienie go](../../media/mtp-eval-66.png)

11. Wybierz **pozycję Rozpocznij korzystanie z usługi Microsoft Defender for Endpoint** z kreatora.

    ![Obraz of_the monitu o potwierdzenie z kreatora, w którym należy kliknąć pozycję Rozpocznij korzystanie z programu Microsoft Defender for Endpoint](../../media/mtp-eval-67.png)

12. Odwiedź [Centrum zabezpieczeń usługi Microsoft Defender.](https://securitycenter.windows.com/) Przejdź do **Ustawienia** a następnie wybierz pozycję **Funkcje zaawansowane**.

    ![Obraz of_Microsoft menu Ustawienia Defender Security Center, w którym należy wybrać pozycję Funkcje zaawansowane](../../media/mtp-eval-68.png)

13. Włącz integrację z usługą **Microsoft Defender for Identity**.

    ![Obraz of_Microsoft zaawansowane funkcje usługi Defender Security Center, przełącznik opcji Microsoft Defender dla tożsamości, który należy włączyć](../../media/mtp-eval-69.png)

14. Włącz integrację z analizą **Office 365 zagrożeniami**.

    ![Obraz of_Microsoft zaawansowane funkcje usługi Defender Security Center, Office 365 przełącznik analizy zagrożeń, który należy włączyć](../../media/mtp-eval-70.png)

15. Włącz integrację z **usługą Microsoft Cloud App Security**.

    ![Obraz of_Microsoft zaawansowane funkcje usługi Defender Security Center Microsoft Cloud App Security przełącznik opcji, który należy włączyć](../../media/mtp-eval-71.png)

16. Przewiń w dół i **kliknij pozycję Zapisz preferencje** , aby potwierdzić nowe integracje.

    ![Obraz of_Save przycisk preferencji, który należy kliknąć](../../media/mtp-eval-72.png)

## <a name="start-the-microsoft-365-defender-service"></a>Uruchom Microsoft 365 Defender sieciowej

> [!NOTE]
> Począwszy od 1 czerwca 2020 r., firma Microsoft automatycznie Microsoft 365 Defender funkcje dla wszystkich uprawnionych dzierżaw. Zobacz ten [artykuł Community technicznej firmy Microsoft na temat uprawnień do licencji,](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/microsoft-threat-protection-will-automatically-turn-on-for/ba-p/1345426) aby uzyskać szczegółowe informacje.

Przejdź do [Microsoft 365 zabezpieczeń](https://security.microsoft.com/homepage). Przejdź do **Ustawienia**, a następnie wybierz pozycję **Microsoft 365 Defender**.

![Obraz of_Microsoft zrzut ekranu Microsoft 365 Usługi Defender 365 ze strony Microsoft 365 zabezpieczeń Ustawienia sieci Web](../../media/mtp-eval-72b.png)

Aby uzyskać bardziej wyczerpujące wskazówki, [zobacz Włączanie Microsoft 365 Defender](m365d-enable.md).

Gratulacje! Właśnie utworzono laboratorium Microsoft 365 Defender lub środowisko pilotażowe! Teraz możesz zapoznać się z Microsoft 365 Defender użytkownikami. Zobacz, czego możesz się dowiedzieć z Microsoft 365 Defender w interakcyjny przewodniku i dowiedz się, jak korzystać z poszczególnych pulpitów nawigacyjnych do wykonywania Twoich codziennie wykonywanych zadań związanych z operacjami zabezpieczeń.

[Zapoznaj się z interakcyjny przewodnik](https://aka.ms/MTP-Interactive-Guide)

Następnie możesz zasymulować atak i zobaczyć, jak funkcje krzyżowe produktu wykrywają, tworzą alerty i automatycznie reagują na ataki bez plików na punkt końcowy.

## <a name="next-step"></a>Następny krok

- [Generowanie alertu testowego](generate-test-alert.md) — uruchom symululę ataków w laboratorium Microsoft 365 Defender próbnego.
