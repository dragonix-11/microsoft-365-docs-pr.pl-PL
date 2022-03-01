---
title: Pilotaż Microsoft 365 z mojej domeny niestandardowej
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- Adm_TOC
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
description: Dowiedz się, jak pilotażować funkcje poczty e-mail z domeny niestandardowej do skrzynki Microsoft 365 pocztowej przy użyciu tylko dwóch kont testowych.
ms.openlocfilehash: bde6daacba3e7adad1a69748074638e651445d8f
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63012520"
---
# <a name="pilot-microsoft-365-from-my-custom-domain"></a>Pilotaż Microsoft 365 z mojej domeny niestandardowej

Można pilotaż Microsoft 365 z tymi wymaganiami i ograniczeniami:

- Bieżący dostawca poczty e-mail musi obsługiwać funkcję przesyłania dalej poczty e-mail.

- Musisz zarządzać swoimi Microsoft 365 DNS u dostawcy hostingu DNS, zamiast Microsoft 365 zarządzać tymi rekordami za Ciebie.

    Aby dowiedzieć się więcej, [zobacz Dodawanie rekordów DNS w celu połączenia domeny](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- Informacje o wolny/zajętym dla użytkowników na innym serwerze poczty e-mail są niedostępne.

- Administratorzy nie mogą administrować wszystkimi kontami użytkowników z jednej lokalizacji.

- Użytkownicy mogą nie być w stanie korzystać z Microsoft 365 filtrowania spamu.

- Jest to zalecane dla bardzo małej liczby użytkowników i dotyczy tylko korzystania z poczty e-mail w ramach pilotażu.

## <a name="set-up-a-microsoft-365-pilot"></a>Konfigurowanie pilotażu Microsoft 365 pilotażowego

Wykonaj poniższe czynności, aby skonfigurować pilotaż Microsoft 365 pilotażowego:

### <a name="step-1-sign-in-to-the-microsoft-365-admin-center"></a>Krok 1. Zaloguj się do centrum administracyjne platformy Microsoft 365

1. Zaloguj się [do centrum administracyjne platformy Microsoft 365 za](https://admin.microsoft.com) pomocą konta służbowego.

2. Wybierz **Ustawienia** >  **Domeny w** lewym okienku nawigacji.

### <a name="step-2-verify-that-you-own-the-domain-you-want-to-use"></a>Krok 2. Sprawdzanie, czy jesteś właścicielem domeny, której chcesz użyć

1. Na stronie **Domeny** wybierz pozycję **Dodaj domenę**.

2. Wpisz nazwę domeny w polu, wybierz pozycję **Użyj tej domeny**, a następnie wybierz pozycję **Kontynuuj**.

3. Wybierz usługi, które chcesz przetestować w swojej domenie, takie jak poczta e-mail i wiadomości błyskawiczne.

4. Na stronie **Weryfikowanie** domeny postępuj zgodnie z instrukcjami krok po kroku, a następnie wybierz pozycję **Weryfikuj**.

    Wprowadzanie zmian w systemie DNS trwa od kilku minut do 72 godzin.

    Po pomyślnym weryfikacji zostaniesz poproszony(-a) o zmodyfikowanie rekordów DNS.

### <a name="step-3-mark-the-domain-as-shared-in-exchange-online"></a>Krok 3. Oznaczanie domeny jako udostępnionej w u Exchange Online

1. W centrum Exchange w sekcji **Przepływ poczty e-mail** wybierz pozycję Zaakceptowane **domeny, a** następnie wybierz domenę, którą chcesz zmodyfikować.

2. Kliknij dwukrotnie, aby otworzyć okno, a następnie wybierz pozycję **Przekazywanie wewnętrzne**.

3. Wybierz **Zapisz**.

    Może to potrwać kilka minut.

### <a name="step-4-unblock-the-existing-email-server-optional"></a>Krok 4. Odblokowywanie istniejącego serwera poczty e-mail (opcjonalnie)

Microsoft 365 ochrony przed spamem Exchange Online Protection (EOP). Program EOP może zablokować istniejący serwer poczty, jeśli wykryje dużą ilość spamu przesyłaną dalej przez bieżący serwer poczty. Jeśli ufasz ochronie przed spamem dla innego dostawcy poczty e-mail, możesz odblokować serwer w Microsoft 365.

> [!NOTE]
> Odblokowanie istniejącego serwera poczty e-mail zezwala na dostęp do skrzynek pocztowych programu Microsoft 365 wszystkich wiadomości-śmieci docierających przez oryginalny serwer i nie można ocenić, jak dobrze chroni Microsoft 365 spam.

1. W okienku Exchange centrum administracyjnego wybierz pozycję **Ochrona**, a następnie wybierz pozycję **Filtr połączenia**.

2. Na liście **Zezwalaj na adresy IP** wybierz pozycję **+**, a następnie dodaj adres IP serwera poczty dla bieżącego dostawcy poczty e-mail.

### <a name="step-5-create-user-accounts-and-set-the-primary-reply-to-address"></a>Krok 5. Tworzenie kont użytkowników i ustawianie podstawowego adresu zwrotnego

1. W lewym centrum administracyjne platformy Microsoft 365 nawigacji wybierz pozycję **Użytkownicy** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Aktywuj użytkowników**</a>.

2. Utwórz dwa konta testowe, dodając dwóch istniejących użytkowników.

    Dla każdego konta wybierz pozycję **+ Dodaj użytkownika** i wypełnij wymagane informacje, w tym metodę haseł, którą chcesz przetestować.

    Aby zapewnić, że adres e-mail użytkownika pozostanie taki sam, pole Nazwa użytkownika musi być zgodne z bieżącym adresem e-mail użytkownika.

3. Wybierz odpowiednią licencję, kliknij przycisk **Dalej**, a następnie kliknij pozycję **Zakończ dodawanie**.

4. Obok **pola Nazwa użytkownika** wybierz niestandardową nazwę domeny z listy rozwijanej.

5. Wybierz **pozycję** **CreateClose** > .

### <a name="step-6-configure-mail-to-flow-from-microsoft-365-or-office-365-to-email-server"></a>Krok 6. **Konfigurowanie poczty do przepływu z Microsoft 365 lub Office 365 e-mail

Można to zrobić w dwóch krokach:

1. Skonfiguruj swoje Microsoft 365 lub Office 365.

2. Skonfiguruj łącznik z usługi Microsoft 365 lub Office 365 do serwera poczty e-mail.

### <a name="1-configure-your-microsoft-365-or-office-365-environment"></a>1. Konfigurowanie Microsoft 365 lub Office 365 komputera

Upewnij się, że w programie Microsoft 365 lub Office 365 zostały ukończone następujące Office 365:

1. Aby skonfigurować łączniki, przed rozpoczęciem musisz mieć przypisane uprawnienia. Aby sprawdzić, jakich uprawnień potrzebujesz, zobacz wpis łączników Microsoft 365 i Office 365 w temacie Uprawnienia funkcji [Exchange Online](/exchange/permissions-exo/feature-permissions) temat.

2. Jeśli chcesz, aby program EOP lub Exchange Online przekazy poczty e-mail z serwerów poczty e-mail do Internetu, możesz:

   - Użyj certyfikatu skonfigurowanego z nazwą podmiotu, która jest taka sama jak zaakceptowana domena w Microsoft 365 lub Office 365. Zalecamy, aby nazwa wspólna lub nazwa alternatywna certyfikatu odpowiada podstawowej domenie SMTP organizacji. Aby uzyskać szczegółowe informacje, zobacz [Wymagania wstępne lokalnego środowiska poczty e-mail](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#prerequisites-for-your-on-premises-email-environment).

   — LUB —

   - Upewnij się, że wszystkie domeny i poddomeny nadawcy w organizacji są skonfigurowane jako zaakceptowane domeny Microsoft 365 lub Office 365.

   Aby uzyskać więcej informacji na temat definiowania zaakceptowanych domen, zobacz Zarządzanie zaakceptowanych domen w programie [Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) i Włączanie przepływu poczty e-mail dla [poddomen](/exchange/mail-flow-best-practices/manage-accepted-domains/enable-mail-flow-for-subdomains) w Exchange Online.

3. Zdecyduj, czy chcesz używać reguł przepływu poczty e-mail (nazywanych także regułami transportu), czy nazw domen do dostarczania poczty z usługi Microsoft 365 lub Office 365 do serwerów poczty e-mail. Większość firm decyduje się na dostarczanie poczty dla wszystkich zaakceptowanych domen. Aby uzyskać więcej informacji, zobacz [Scenariusz: Rozsyłanie warunkowe poczty w programie Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/conditional-mail-routing).

> [!NOTE]
> Możesz skonfigurować reguły przepływu poczty e-mail zgodnie z opisem w te sposób: Akcje [reguły przepływu](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions) poczty w Exchange Online. Na przykład możesz chcieć użyć reguł przepływu poczty e-mail z łącznikami, jeśli poczta jest obecnie kierowana za pośrednictwem list dystrybucyjnych do wielu witryn.

### <a name="2-set-up-a-connector-from-microsoft-365-or-office-365-to-your-email-server"></a>2. Konfigurowanie łącznika między Microsoft 365 lub Office 365 e-mail

Aby utworzyć łącznik w aplikacji Microsoft 365 lub Office 365,  >  wybierz pozycję Administrator **Exchange** aby przejść do Exchange administracyjnego. Następnie wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2183136" target="_blank">**flowConnectors poczty**</a> > .

Skonfiguruj łączniki za pomocą kreatora.

Aby uruchomić kreatora, kliknij symbol plus **+**. Na pierwszym ekranie wybierz pozycję **Z** Office 365 **i Do** serwera poczty twojej organizacji.

Kliknij **przycisk** Dalej i postępuj zgodnie z instrukcjami kreatora. Kliknij linki **Pomoc** lub **Dowiedz się więcej** , jeśli potrzebujesz więcej informacji. Kreator przeprowadzi Cię przez konfigurację. Upewnij się, że na końcu jest sprawdzana poprawność łącznika. Jeśli łącznik nie zostanie zweryfikowany, kliknij dwukrotnie wyświetlony komunikat, aby uzyskać więcej informacji, i zobacz [](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/validate-connectors) Sprawdzanie poprawności łączników, aby uzyskać pomoc w rozwiązywaniu problemów.



### <a name="step-7-update-dns-records-at-your-dns-hosting-provider"></a>Krok 7. Aktualizowanie rekordów DNS u dostawcy hostingu DNS

Zaloguj się w witrynie internetowej dostawcy hostingu DNS i postępuj zgodnie z instrukcjami w te sposób: [Dodawanie rekordów DNS w celu połączenia Twojej domeny](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

**Upewnij się, że są dwa następujące wyjątki:**

- Nie twórz nowego rekordu MX i nie zmieniaj istniejącego rekordu MX.

- Jeśli masz już rekord SPF (Sender Policy Framework) dla poprzedniego dostawcy poczty e-mail, zamiast tworzyć nowy rekord SPF (TXT) dla usługi Exchange Online, dodaj ciąg "include:spf.protection.outlook.com" do bieżącego rekordu TXT.

    Na przykład „v=spf1 mx include:adatum.com include:spf.protection.outlook.com ~all”.

    Jeśli nie masz rekordu SPF, zmodyfikuj rekord zalecany przez Microsoft 365, aby uwzględnić domenę bieżącego dostawcy poczty e-mail, a następnie dodaj spf.protection.outlook.com. Zapewni to autoryzację wiadomości wychodzących z obu systemów poczty e-mail.

### <a name="step-8-set-up-email-forwarding-at-your-current-provider"></a>Krok 8. Konfigurowanie przesyłania dalej poczty e-mail u bieżącego dostawcy

U bieżącego dostawcy poczty e-mail skonfiguruj przesyłanie poczty do domeny onmicrosoft.com dla kont e-mail Twoich użytkowników:

- Przesyłanie dalej skrzynki pocztowej użytkownika do usera@yourcompany.onmicrosoft.com

- Przesyłanie dalej skrzynki pocztowej użytkownika B do userb@yourcompany.onmicrosoft.com

Po zakończeniu tego kroku wszystkie wiadomości e-mail wysyłane na usera@yourcompany.com i userb@yourcompany.com będą dostępne w Microsoft 365.

> [!NOTE]
> Aby uzyskać dokładne instrukcje dotyczące skonfigurowania przesyłania dalej poczty e-mail, skontaktuj się z bieżącym dostawcą poczty e-mail.<br/>
> Nie ma konieczności zachowywania kopii wiadomości u bieżącego dostawcy poczty e-mail.<br/>
> Większość dostawców przesyła dalej wiadomości e-mail, pozostawiając niezmieniony adres zwrotny nadawcy, aby odpowiedzi trafiały do pierwotnego nadawcy.

### <a name="step-9-test-mail-flow"></a>Krok 9. Testowanie przepływu poczty e-mail

1. Zaloguj się Outlook Web App przy użyciu poświadczeń użytkownika A.

2. Wykonaj następujące testy:

    - Przetestuj lokalną pocztę e-mail firmy Microsoft, wysyłając wiadomość e-mail, na przykład do użytkownika B. Wiadomość e-mail zostanie dostarczona natychmiast. W tym scenariuszu wiadomość nie jest przekierowyowana do skrzynki pocztowej użytkownika B na oryginalnym serwerze, ponieważ Microsoft 365 jest lokalna.

    - Przetestuj pocztę e-mail do użytkownika w istniejącym systemie poczty e-mail, wysyłając wiadomość e-mail, na przykład do użytkownika C. Wiadomość e-mail zostanie dostarczona do skrzynki pocztowej użytkownika C na oryginalnym serwerze poczty.

    - Sprawdź, czy przesyłanie dalej jest poprawnie skonfigurowane z konta zewnętrznego lub z konta e-mail pracownika w istniejącym systemie poczty e-mail. Na przykład z pierwotnego konta serwera dla użytkownika C lub konta Hotmail wyślij użytkownikowi wiadomość e-mail I sprawdź, czy dotarła do skrzynki Microsoft 365 pocztowej użytkownika A.

### <a name="step-10-move-mailbox-contents"></a>Krok 10. Przenoszenie zawartości skrzynki pocztowej

Ponieważ tylko dwóch użytkowników testowych jest przenoszących, a użytkownik A i użytkownik B używa programu Outlook, możesz przenieść wiadomość e-mail, otwierając starego . Plik PST w nowym profilu Outlook kopiując wiadomości, elementy kalendarza, kontakty i tak dalej. Aby uzyskać więcej informacji, zobacz [Importowanie wiadomości e-mail, kontaktów i kalendarza Outlook pliku pst](https://support.microsoft.com/office/import-email-contacts-and-calendar-from-an-outlook-pst-file-431a8e9a-f99f-4d5f-ae48-ded54b3440ac).

Po zaimportowaniu ich do odpowiednich lokalizacji w skrzynce Microsoft 365 pocztowej usługi Microsoft 365 można uzyskiwać do nich dostęp z dowolnego urządzenia i miejsca.
