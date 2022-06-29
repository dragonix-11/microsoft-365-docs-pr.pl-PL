---
title: Tworzenie bezpiecznego środowiska udostępniania gościa
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-security-compliance
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.localizationpriority: high
f1.keywords: NOCSH
recommendations: false
description: Dowiedz się więcej o dostępnych opcjach tworzenia bezpiecznego środowiska udostępniania gościa na platformie Microsoft 365, zapewniając dostęp gościa w celu usprawnienia współpracy.
ms.openlocfilehash: 26daea8795084a87a2891a5dd04da172692990cb
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490924"
---
# <a name="create-a-secure-guest-sharing-environment"></a>Tworzenie bezpiecznego środowiska udostępniania gościa

W tym artykule omówimy różne opcje tworzenia bezpiecznego środowiska udostępniania gościa na platformie Microsoft 365. Oto przykłady umożliwiające wyobrażenie o dostępnych opcjach. Tych procedur można używać w różnych kombinacjach, aby spełnić wymagania organizacji dotyczące zabezpieczeń i zgodności.

Ten artykuł zawiera:

- Konfigurowanie uwierzytelniania wieloskładnikowego dla gości.
- Konfigurowanie warunków użytkowania dla gości.
- Konfigurowanie kwartalnych przeglądów dostępu gościa w celu okresowego sprawdzania, czy goście nadal potrzebują uprawnień do zespołów i witryn.
- Ograniczanie gości do dostępu tylko do Internetu dla urządzeń niezarządzanych.
- Konfigurowanie zasad limitu czasu sesji w celu zapewnienia, że goście będą się codziennie uwierzytelniać.
- Tworzenie poufnego typu informacji dla wysoce wrażliwego projektu.
- Automatyczne przypisywanie etykiety poufności do dokumentów zawierających typ informacji poufnych.
- Automatyczne usuwanie dostępu gościa z plików z etykietą poufności.

Niektóre opcje omówione w tym artykule wymagają, aby goście mieli konto w usłudze Azure Active Directory. Aby upewnić się, że goście są dołączane do katalogu podczas udostępniania im plików i folderów, użyj [integracji programu SharePoint i usługi OneDrive z usługą Azure AD B2B Preview](/sharepoint/sharepoint-azureb2b-integration-preview).

Pamiętaj, że w tym artykule nie będziemy omawiać włączania ustawień udostępniania gości. Aby uzyskać szczegółowe informacje na temat włączania udostępniania gości w różnych scenariuszach, zobacz [Współpraca z osobami spoza organizacji](collaborate-with-people-outside-your-organization.md) .

## <a name="set-up-multi-factor-authentication-for-guests"></a>Konfigurowanie uwierzytelniania wieloskładnikowego dla gości

Uwierzytelnianie wieloskładnikowe znacznie zmniejsza prawdopodobieństwo naruszenia zabezpieczeń konta. Ponieważ goście mogą korzystać z osobistych kont e-mail, które nie są zgodne z żadnymi zasadami ładu lub najlepszymi rozwiązaniami, szczególnie ważne jest wymaganie uwierzytelniania wieloskładnikowego dla gości. W przypadku kradzieży nazwy użytkownika i hasła gościa wymaganie drugiego czynnika uwierzytelniania znacznie zmniejsza prawdopodobieństwo uzyskania dostępu do witryn i plików przez nieznane strony.

W tym przykładzie skonfigurujemy uwierzytelnianie wieloskładnikowe dla gości przy użyciu zasad dostępu warunkowego w usłudze Azure Active Directory.

Aby skonfigurować uwierzytelnianie wieloskładnikowe dla gości

1. Przejdź do [obszaru Zasady dostępu warunkowego platformy Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
2. Na **| dostępu warunkowego W bloku Zasady** kliknij pozycję **Nowe zasady**.
3. W polu **Nazwa** wpisz nazwę.
4. W obszarze **Przypisania** kliknij pozycję **Użytkownicy i grupy**.
5. W bloku **Użytkownicy i grupy** wybierz pozycję **Wybierz użytkowników i grupy**, zaznacz pole wyboru **Wszyscy goście i użytkownicy zewnętrzni** .
6. W obszarze **Przypisania** kliknij pozycję **Aplikacje lub akcje w chmurze**.
7. W bloku **Aplikacje lub akcje w chmurze** wybierz pozycję **Wszystkie aplikacje w chmurze** na karcie **Dołącz** .
8. W obszarze **Kontrolki dostępu** kliknij pozycję **Udziel**.
9. W bloku **Udzielanie** zaznacz pole wyboru **Wymagaj uwierzytelniania wieloskładnikowego** , a następnie kliknij pozycję **Wybierz**.
10. W bloku **Nowy** w obszarze **Włącz zasady** kliknij pozycję **Włączone**, a następnie kliknij pozycję **Utwórz**.

Teraz gość będzie musiał zarejestrować się w uwierzytelnianiu wieloskładnikowym, zanim będzie mógł uzyskać dostęp do udostępnionej zawartości, witryn lub zespołów.

### <a name="more-information"></a>Więcej informacji

[Planowanie wdrożenia uwierzytelniania wieloskładnikowego Azure AD](/azure/active-directory/authentication/howto-mfa-getstarted)

## <a name="set-up-a-terms-of-use-for-guests"></a>Konfigurowanie warunków użytkowania dla gości

W niektórych sytuacjach goście mogą nie mieć podpisanych umów o zachowaniu poufności ani innych umów prawnych z Organizacją. Przed uzyskaniem dostępu do plików, które są im udostępniane, goście mogą wymagać zgody na warunki użytkowania. Warunki użytkowania mogą być wyświetlane przy pierwszej próbie uzyskania dostępu do udostępnionego pliku lub witryny.

Aby utworzyć warunki użytkowania, musisz najpierw utworzyć dokument w programie Word lub innym programie do tworzenia, a następnie zapisać go jako plik .pdf. Ten plik można następnie przekazać do Azure AD.

Aby utworzyć warunki użytkowania Azure AD

1. Zaloguj się do platformy Azure jako administrator globalny, administrator zabezpieczeń lub administrator dostępu warunkowego.
2. Przejdź do [obszaru Warunki użytkowania](https://aka.ms/catou).
3. Kliknij **pozycję Nowe terminy**.

   ![Zrzut ekranu przedstawiający Azure AD nowych ustawień warunków użytkowania.](../media/azure-ad-guest-terms-of-use.png)

4. Wpisz **nazwę** i **nazwę wyświetlaną**.
6. W obszarze **Dokument warunków użytkowania** przejdź do utworzonego pliku pdf i wybierz go.
7. Wybierz język dokumentu warunków użytkowania.
8. Ustaw **opcję Wymagaj od użytkowników, aby rozszerzyć warunki użytkowania** na **Włączone**.
9. W obszarze **Dostęp warunkowy** na liście **Szablon zasad wymuszania przy użyciu dostępu warunkowego** wybierz pozycję **Utwórz zasady dostępu warunkowego później**.
10. Kliknij **pozycję Utwórz**.

Po utworzeniu warunków użytkowania następnym krokiem jest utworzenie zasad dostępu warunkowego, które wyświetlają warunki użytkowania gościom.

Aby utworzyć zasady dostępu warunkowego

1. Przejdź do [obszaru Zasady dostępu warunkowego platformy Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
2. Na **| dostępu warunkowego W bloku Zasady** kliknij pozycję **Nowe zasady**.
3. W polu **Nazwa** wpisz nazwę.
4. W obszarze **Przypisania** kliknij pozycję **Użytkownicy i grupy**.
5. W bloku **Użytkownicy i grupy** wybierz pozycję **Wybierz użytkowników i grupy**, zaznacz pole wyboru **Wszyscy goście i użytkownicy zewnętrzni** .
6. W obszarze **Przypisania** kliknij pozycję **Aplikacje lub akcje w chmurze**.
7. Na karcie **Dołączanie** wybierz pozycję **Wybierz aplikacje**, a następnie kliknij pozycję **Wybierz**.
8. W bloku **Wybierz** wybierz pozycję **Microsoft Teams**, **Office 365 SharePoint Online** i **Grupy programu Outlook**, a następnie kliknij pozycję **Wybierz**.
9. W obszarze **Kontrolki dostępu** kliknij pozycję **Udziel**.
10. W bloku **Udzielanie** wybierz pozycję **Warunki użytkowania gościa**, a następnie kliknij pozycję **Wybierz**.
11. W bloku **Nowy** w obszarze **Włącz zasady** kliknij pozycję **Włączone**, a następnie kliknij pozycję **Utwórz**.

Teraz, gdy gość po raz pierwszy próbuje uzyskać dostęp do zawartości, zespołu lub witryny w organizacji, będzie musiał zaakceptować warunki użytkowania.

> [!NOTE]
> Korzystanie z dostępu warunkowego wymaga licencji Azure AD — wersja Premium P1. Aby uzyskać więcej informacji, zobacz [Co to jest dostęp warunkowy](/azure/active-directory/conditional-access/overview).

### <a name="more-information"></a>Więcej informacji

[Warunki użytkowania usługi Azure Active Directory](/azure/active-directory/conditional-access/terms-of-use)

## <a name="set-up-guest-access-reviews"></a>Konfigurowanie przeglądów dostępu gościa

Przeglądy dostępu w Azure AD umożliwiają automatyzację okresowego przeglądu dostępu użytkowników do różnych zespołów i grup. Wymagając przeglądu dostępu dla gości, możesz pomóc w zapewnieniu, że goście nie zachowają dostępu do poufnych informacji organizacji dłużej niż jest to konieczne.

Aby skonfigurować przegląd dostępu gościa

1. Na [stronie Zarządzanie tożsamościami](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade) w menu po lewej stronie kliknij pozycję **Przeglądy dostępu**.
2. Kliknij pozycję **Nowy przegląd dostępu**.
3. Wybierz opcję **Teams + Groups (Zespoły i grupy** ).
4. Wybierz opcję **Wszystkie grupy platformy Microsoft 365 z użytkownikami-gośćmi** . Kliknij **pozycję Wybierz grupy, aby wykluczyć** , jeśli chcesz wykluczyć dowolne grupy.
5. Wybierz **opcję Tylko użytkownicy-goście** , a następnie kliknij przycisk **Dalej: Recenzje**.
6. W obszarze **Wybierz recenzentów** wybierz pozycję **Właściciele grupy**.
7. Kliknij **pozycję Wybierz rezerwowych recenzentów**, wybierz, kto powinien być rezerwowym recenzentem, a następnie kliknij pozycję **Wybierz**.
8. W obszarze **Określ cykl przeglądu** wybierz pozycję **Kwartalne**.
9. Wybierz datę rozpoczęcia i czas trwania.
10. W polu **Koniec** wybierz pozycję **Nigdy**, a następnie kliknij przycisk **Dalej: Ustawienia**.

    ![Zrzut ekranu przedstawiający kartę przeglądu dostępu Azure AD.](../media/azure-ad-create-access-review.png)

11. Na karcie **Ustawienia** przejrzyj ustawienia zgodności z regułami biznesowymi.

    ![Zrzut ekranu przedstawiający kartę ustawień przeglądu dostępu Azure AD.](../media/azure-ad-create-access-review-settings.png)

12. Kliknij **przycisk Dalej: Przejrzyj i utwórz**.
13. Wpisz **nazwę przeglądu** i przejrzyj ustawienia.
14. Kliknij **pozycję Utwórz**.

Należy pamiętać, że w przypadku lokalizacji programu SharePoint i usługi OneDrive dokumenty będą aktywnie blokowane bezpośrednio po wykryciu informacji poufnych, niezależnie od tego, czy dokument jest udostępniony, czy nie, dla wszystkich gości, podczas gdy użytkownicy wewnętrzni będą nadal mieć dostęp do dokumentu.

### <a name="more-information"></a>Więcej informacji

[Zarządzanie dostępem gościa za pomocą przeglądów dostępu Azure AD](/azure/active-directory/governance/manage-guest-access-with-access-reviews)

[Tworzenie przeglądu dostępu grup lub aplikacji w Azure AD przeglądów dostępu](/azure/active-directory/governance/create-access-review)

## <a name="set-up-web-only-access-for-guests"></a>Konfigurowanie dostępu tylko do Internetu dla gości

Możesz wymagać od gości dostępu do zespołów, witryn i plików tylko za pomocą przeglądarki internetowej. Zmniejsza to prawdopodobieństwo pobrania poufnych plików i pozostawienia ich na niezarządzanym urządzeniu. Jest to również przydatne podczas udostępniania środowiskom korzystającym z urządzeń udostępnionych.

W przypadku Grupy Microsoft 365 i aplikacji Teams odbywa się to przy użyciu Azure AD zasad dostępu warunkowego. W przypadku programu SharePoint jest to skonfigurowane w centrum administracyjnym programu SharePoint. (Możesz również [użyć etykiet poufności, aby ograniczyć gościom dostęp tylko do Internetu](../compliance/sensitivity-labels-teams-groups-sites.md)).

Aby ograniczyć gościom dostęp tylko do Internetu dla grup i aplikacji Teams:

1. Przejdź do [obszaru Zasady dostępu warunkowego platformy Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
2. W bloku **Dostęp warunkowy — zasady** kliknij pozycję **Nowe zasady**.
3. W polu **Nazwa** wpisz nazwę.
4. W obszarze **Przypisania** kliknij pozycję **Użytkownicy i grupy**.
5. W bloku **Użytkownicy i grupy** wybierz pozycję **Wybierz użytkowników i grupy**, zaznacz pole wyboru **Wszyscy goście i użytkownicy zewnętrzni** .
6. W obszarze **Przypisania** kliknij pozycję **Aplikacje lub akcje w chmurze**.
7. Na karcie **Dołączanie** wybierz pozycję **Wybierz aplikacje**, a następnie kliknij pozycję **Wybierz**.
8. W bloku **Wybierz** wybierz pozycję **Microsoft Teams** i **grupy programu Outlook**, a następnie kliknij pozycję **Wybierz**.
9. W obszarze **Przypisania** kliknij pozycję **Warunki**.
10. W bloku **Warunki** kliknij pozycję **Aplikacje klienckie**.
11. W bloku **Aplikacje klienckie** kliknij pozycję **Tak**, aby **skonfigurować**, a następnie wybierz ustawienia **Aplikacje mobilne i klienci klasyczni**, **Exchange ActiveSync klientów** i **Inni klienci**. Wyczyść pole wyboru **Przeglądarka** .

    ![Zrzut ekranu przedstawiający Azure AD ustawień aplikacji klienckich dostępu warunkowego.](../media/azure-ad-conditional-access-client-mobile.png)

12. Kliknij pozycję **Gotowe**.
13. W obszarze **Kontrolki dostępu** kliknij pozycję **Udziel**.
14. W bloku **Udzielanie** wybierz pozycję **Wymagaj, aby urządzenie było oznaczone jako zgodne** i **Wymagaj urządzenia przyłączonego do hybrydowego Azure AD**.
15. **W obszarze Dla wielu kontrolek** wybierz pozycję **Wymagaj jednej z wybranych kontrolek**, a następnie kliknij pozycję **Wybierz**.
16. W bloku **Nowy** w obszarze **Włącz zasady** kliknij pozycję **Włączone**, a następnie kliknij pozycję **Utwórz**.

Aby ograniczyć gościom dostęp do internetu w programie SharePoint

1. W centrum administracyjnym programu SharePoint rozwiń węzeł **Zasady** i wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185071" target="_blank">**Kontrola dostępu**</a>.
2. Wybierz pozycję **Urządzenia niezarządzane**.
3. Wybierz opcję **Zezwalaj na ograniczony dostęp tylko do Internetu** , a następnie wybierz pozycję **Zapisz**.

Należy pamiętać, że to ustawienie w centrum administracyjnym programu SharePoint powoduje utworzenie pomocniczych zasad dostępu warunkowego w Azure AD.

## <a name="configure-a-session-timeout-for-guests"></a>Konfigurowanie limitu czasu sesji dla gości

Wymaganie od gości regularnego uwierzytelniania może zmniejszyć możliwość uzyskania przez nieznanych użytkowników dostępu do zawartości organizacji, jeśli urządzenie gościa nie jest zabezpieczone. Możesz skonfigurować zasady dostępu warunkowego limitu czasu sesji dla gości w Azure AD.

Aby skonfigurować zasady limitu czasu sesji gościa

1. Przejdź do [obszaru Zasady dostępu warunkowego platformy Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
2. W bloku **Dostęp warunkowy — zasady** kliknij pozycję **Nowe zasady**.
3. W polu **Nazwa** wpisz *limit czasu sesji gościa*.
4. W obszarze **Przypisania** kliknij pozycję **Użytkownicy i grupy**.
5. W bloku **Użytkownicy i grupy** wybierz pozycję **Wybierz użytkowników i grupy**, zaznacz pole wyboru **Wszyscy goście i użytkownicy zewnętrzni** .
6. W obszarze **Przypisania** kliknij pozycję **Aplikacje lub akcje w chmurze**.
7. Na karcie **Dołączanie** wybierz pozycję **Wybierz aplikacje**, a następnie kliknij pozycję **Wybierz**.
8. W bloku **Wybierz** wybierz pozycję **Microsoft Teams**, **Office 365 SharePoint Online** i **Grupy programu Outlook**, a następnie kliknij pozycję **Wybierz**.
9. W obszarze **Kontrolki dostępu** kliknij pozycję **Sesja**.
10. W bloku **Sesja** wybierz pozycję **Częstotliwość logowania**.
11. Wybierz **1** i **dni** dla okresu, a następnie kliknij przycisk **Wybierz**.
12. W bloku **Nowy** w obszarze **Włącz zasady** kliknij pozycję **Włączone**, a następnie kliknij pozycję **Utwórz**.

## <a name="create-a-sensitive-information-type-for-a-highly-sensitive-project"></a>Tworzenie poufnego typu informacji dla wysoce wrażliwego projektu

Typy informacji poufnych to wstępnie zdefiniowane ciągi, których można używać w przepływach pracy zasad w celu wymuszania wymagań dotyczących zgodności. Portal zgodności Microsoft Purview zawiera ponad sto poufnych typów informacji, w tym numery praw jazdy, numery kart kredytowych, numery kont bankowych itp.

Możesz tworzyć niestandardowe typy informacji poufnych, aby ułatwić zarządzanie zawartością specyficzną dla organizacji. W tym przykładzie utworzymy niestandardowy typ informacji poufnych dla wysoce wrażliwego projektu. Następnie możemy użyć tego typu informacji poufnych, aby automatycznie zastosować etykietę poufności.

Aby utworzyć typ informacji poufnych

1. W [portal zgodności Microsoft Purview](https://compliance.microsoft.com) w obszarze nawigacji po lewej stronie rozwiń węzeł **Klasyfikacja**, a następnie kliknij pozycję **Typy informacji poufnych**.
2. Kliknij **pozycję Utwórz**.
3. W **polu Nazwa** i **opis** wpisz **Project Saturn**, a następnie kliknij przycisk **Dalej**.
4. Kliknij **pozycję Dodaj element**.
5. Na liście **Wykryj zawartość zawierającą** wybierz pozycję **Słowa kluczowe**, a następnie wpisz *ciąg Project Saturn* w polu słowa kluczowego.
6. Kliknij **przycisk Dalej**, a następnie kliknij przycisk **Zakończ**.
7. Jeśli zostanie wyświetlone pytanie, czy chcesz przetestować typ informacji poufnych, kliknij przycisk **Nie**.

### <a name="more-information"></a>Więcej informacji

[Niestandardowe typy informacji poufnych](/Office365/SecurityCompliance/custom-sensitive-info-types)

## <a name="create-an-auto-labeling-policy-to-assign-a-sensitivity-label-based-on-a-sensitive-information-type"></a>Tworzenie zasad automatycznego etykietowania w celu przypisania etykiety poufności na podstawie typu informacji poufnych

Jeśli używasz etykiet poufności w organizacji, możesz automatycznie zastosować etykietę do plików zawierających zdefiniowane typy informacji poufnych. 

Aby utworzyć zasady automatycznego etykietowania

1. Otwórz [centrum administracyjne usługi Microsoft Purview](https://compliance.microsoft.com).
2. W obszarze nawigacji po lewej stronie kliknij pozycję **Ochrona informacji**.
3. Na karcie **Automatyczne etykietowanie** kliknij pozycję **Utwórz zasady automatycznego etykietowania**.
4. Na stronie **Wybierz informacje, do których ma zostać zastosowana ta etykieta** , wybierz pozycję **Niestandardowe** , a następnie kliknij przycisk **Dalej**.
5. Wpisz nazwę i opis zasad, a następnie kliknij przycisk **Dalej**.
6. Na stronie **Wybieranie lokalizacji, w których chcesz zastosować etykietę** , włącz **witryny programu SharePoint** i kliknij pozycję **Wybierz witryny**.
7. Dodaj adresy URL witryn, w których chcesz włączyć automatyczne etykietowanie, a następnie kliknij przycisk **Gotowe**.
8. Kliknij **Dalej**.
9. Na stronie **Konfigurowanie reguł typowych lub zaawansowanych** wybierz pozycję **Typowe reguły** , a następnie kliknij przycisk **Dalej**.
10. Na stronie **Definiowanie reguł zawartości we wszystkich lokalizacjach** kliknij pozycję **Nowa reguła**.
11. Na stronie **Nowa reguła** nadaj regule nazwę, kliknij pozycję **Dodaj warunek**, a następnie kliknij pozycję **Zawartość zawiera typy informacji poufnych**.
12. Kliknij **przycisk Dodaj**, kliknij pozycję **Typy informacji poufnych**, wybierz typy informacji poufnych, których chcesz użyć, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **Zapisz**.
13. Kliknij **Dalej**.
14. Kliknij **pozycję Wybierz etykietę**, wybierz etykietę, która ma być używana, a następnie kliknij przycisk **Dodaj**.
15. Kliknij **Dalej**.
16. Pozostaw zasady w trybie symulacji i kliknij przycisk **Dalej**.
17. Kliknij **pozycję Utwórz zasady**, a następnie kliknij pozycję **Gotowe**.

Gdy zasady zostaną wprowadzone, gdy użytkownik wpisze ciąg "Project Saturn" do dokumentu, zasady automatycznego etykietowania automatycznie zastosują określoną etykietę podczas skanowania pliku.

### <a name="more-information"></a>Więcej informacji

[Automatyczne stosowanie etykiety poufności do zawartości](../compliance/apply-sensitivity-label-automatically.md)

## <a name="create-a-dlp-policy-to-remove-guest-access-to-highly-sensitive-files"></a>Tworzenie zasad DLP w celu usunięcia dostępu gościa do wysoce poufnych plików

Możesz użyć [Ochrona przed utratą danych w Microsoft Purview (DLP),](../compliance/dlp-learn-about-dlp.md) aby zapobiec niepożądanemu udostępnianiu przez gości poufnej zawartości. Zapobieganie utracie danych może podjąć działania na podstawie etykiety poufności pliku i usunąć dostęp gościa.

Aby utworzyć regułę DLP

1. W centrum administracyjnym usługi Microsoft Purview przejdź do [strony Zapobieganie utracie danych](https://compliance.microsoft.com/datalossprevention).
2. Kliknij **pozycję Utwórz zasady**.
3. Wybierz pozycję **Niestandardowe** i kliknij przycisk **Dalej**.
4. Wpisz nazwę zasad i kliknij przycisk **Dalej**.
5. Na stronie **Lokalizacje, aby zastosować zasady** wyłącz wszystkie ustawienia z wyjątkiem **witryn programu SharePoint** i **kont usługi OneDrive**, a następnie kliknij przycisk **Dalej**.
6. Na stronie **Definiowanie ustawień zasad** kliknij przycisk **Dalej**.
7. Na stronie **Dostosowywanie zaawansowanych reguł DLP** kliknij pozycję **Utwórz regułę** i wpisz nazwę reguły.
8. W obszarze **Warunki** kliknij pozycję **Dodaj warunek** i wybierz pozycję **Zawartość zawiera**.
9. Kliknij **przycisk Dodaj**, wybierz pozycję **Etykiety poufności**, wybierz etykiety, których chcesz użyć, a następnie kliknij przycisk **Dodaj**.

   ![Zrzut ekranu przedstawiający opcje warunków, typy informacji poufnych, etykiety poufności i etykiety przechowywania.](../media/limit-accidental-exposure-dlp-conditions.png)

10. W obszarze **Akcje** kliknij **pozycję Dodaj akcję** i wybierz pozycję **Ogranicz dostęp lub zaszyfruj zawartość w lokalizacjach platformy Microsoft 365**.
11. Zaznacz pole wyboru **Ogranicz dostęp lub zaszyfruj zawartość w lokalizacjach platformy Microsoft 365** , a następnie wybierz opcję **Tylko osoby spoza organizacji** .

      ![Zrzut ekranu przedstawiający opcje akcji regułY DLP.](../media/dlp-remove-guest-access-sensitive-files.png)

12. Kliknij **przycisk Zapisz,** a następnie kliknij przycisk **Dalej**.
13. Wybierz opcje testu i kliknij przycisk **Dalej**.
14. Kliknij pozycję **Prześlij**, a następnie kliknij pozycję **Gotowe**.

Należy pamiętać, że te zasady nie usuwają dostępu, jeśli gość jest członkiem witryny lub całego zespołu. Jeśli planujesz mieć wysoce poufne dokumenty w witrynie lub zespole z członkami-gośćmi, rozważ następujące opcje:

- Używaj [kanałów prywatnych](/MicrosoftTeams/private-channels) i zezwalaj tylko członkom organizacji w kanałach prywatnych.
- [Współużytkuj kanały udostępnione](/MicrosoftTeams/shared-channels), aby współpracować z osobami spoza organizacji, mając tylko osoby z Twojej organizacji w samym zespole.

## <a name="additional-options"></a>Opcje dodatkowe

Istnieją pewne dodatkowe opcje w usługach Microsoft 365 i Azure Active Directory, które mogą pomóc w zabezpieczeniu środowiska udostępniania gościa.

- Możesz utworzyć listę dozwolonych lub niedozwolonych domen udostępniania, aby ograniczyć liczbę użytkowników, którzy mogą udostępniać. Aby uzyskać więcej informacji, zobacz [Ograniczanie udostępniania zawartości programu SharePoint i usługi OneDrive według domeny](/sharepoint/restricted-domains-sharing) oraz [Zezwalaj lub blokuj zaproszenia dla użytkowników B2B z określonych organizacji](/azure/active-directory/b2b/allow-deny-list) .
- Możesz ograniczyć inne dzierżawy usługi Azure Active Directory, z którymi użytkownicy mogą się łączyć. Aby uzyskać informacje, zobacz [Używanie ograniczeń dzierżawy do zarządzania dostępem do aplikacji w chmurze SaaS](/azure/active-directory/manage-apps/tenant-restrictions) .
- Możesz utworzyć środowisko zarządzane, w którym partnerzy mogą pomóc w zarządzaniu kontami gości. Aby uzyskać informacje [, zobacz Tworzenie ekstranetu B2B z zarządzanymi gośćmi](/Office365/Enterprise/b2b-extranet) .

## <a name="see-also"></a>Zobacz też

[Ograniczanie przypadkowego narażenia na pliki podczas udostępniania gościom](share-limit-accidental-exposure.md)

[Najlepsze rozwiązania dotyczące udostępniania plików i folderów nieuwierzytelnionym użytkownikom](best-practices-anonymous-sharing.md)

[Tworzenie ekstranetu B2B z zarządzanymi gośćmi](b2b-extranet.md)
