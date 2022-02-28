---
title: Tworzenie alertów aktywności
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 11/7/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MED150
- BCS160
- MET150
ms.assetid: 72bbad69-035b-4d33-b8f4-549a2743e97d
ROBOTS: NOINDEX, NOFOLLOW
description: Dodawanie alertów aktywności w aplikacji i zarządzanie nimi w Centrum zgodności platformy Microsoft 365, Microsoft 365 powiadomienia e-mail będą wysyłane, gdy użytkownicy będą wykonywać określone działania.
ms.openlocfilehash: 593c51a9d85ebb6f687a5e8573df32d4de515e6b
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2021
ms.locfileid: "62989750"
---
# <a name="create-activity-alerts"></a>Tworzenie alertów aktywności

Możesz utworzyć alert aktywności, który będzie ci wysyłać powiadomienie e-mail, gdy użytkownicy wykonują określone działania w Office 365. Alerty aktywności są podobne do wyszukiwania zdarzeń w dzienniku inspekcji z tym wyjątkiem, że otrzymasz wiadomość e-mail w przypadku wystąpienia działania, dla którym został utworzony alert.

 **Dlaczego warto używać alertów aktywności zamiast przeszukiwać dziennik inspekcji?** Mogą być określone rodzaje działań wykonywanych przez określonych użytkowników, o których naprawdę chcesz wiedzieć. Zamiast pamiętać o przeszukiwaniu dziennika inspekcji w celu wyszukania tych działań, można użyć alertów aktywności w celu Microsoft 365 ci wiadomości e-mail, gdy użytkownicy będą wykonywać te działania. Można na przykład utworzyć alert aktywności powiadamiający o usunięciu przez użytkownika plików w programie SharePoint lub utworzyć alert powiadamiający o trwałym usunięciu przez użytkownika wiadomości ze skrzynki pocztowej. W wysłanej do Ciebie wiadomości e-mail wiadomości e-mail znajdują się informacje o tym, które działania zostały wykonane, i o użytkowniku, który to wykonał.

> [!NOTE]
> Alerty aktywności są wy przestarzałe. Zamiast tworzyć nowe alerty dotyczące aktywności, zalecamy rozpoczęcie korzystania z zasad alertów w Centrum zabezpieczeń i zgodności. Zasady alertów zawierają dodatkowe funkcje, takie jak możliwość utworzenia zasad alertów, które powodują wyzwolenie alertu, gdy dowolny użytkownik wykonuje określone działanie, oraz wyświetlanie alertów na stronie Wyświetlanie alertów w Centrum zabezpieczeń i zgodności. Aby uzyskać więcej informacji, zobacz [Zasady alertów](alert-policies.md).

## <a name="confirm-roles-and-configure-audit-logging"></a>Potwierdzanie ról i konfigurowanie rejestrowania inspekcji

- Aby zarządzać alertami aktywności, musisz mieć przypisaną rolę konfiguracja Centrum zgodności platformy Microsoft 365 organizacji w organizacji. Domyślnie ta rola jest przypisana do grup ról Administrator zgodności i Zarządzanie organizacją. Aby uzyskać więcej informacji na temat dodawania członków do grup ról, zobacz [Zapewnianie użytkownikom dostępu do Centrum zgodności platformy Microsoft 365](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).

- Przed rozpoczęciem korzystania z alertów dotyczących aktywności Ty (lub inny administrator) musisz najpierw włączyć rejestrowanie inspekcji dla organizacji. W tym celu po prostu kliknij pozycję **Rozpocznij rejestrowanie aktywności użytkowników i administratorów** na **stronie Alerty** dotyczące aktywności. (Jeśli nie widzisz tego linku, inspekcja już została włączona w organizacji). Możesz również włączyć inspekcję na stronie Przeszukiwanie dziennika **inspekcji** w Centrum zgodności platformy Microsoft 365 (przejdź do tematu **Inspekcja**). Wystarczy to zrobić tylko raz dla organizacji.

- Można tworzyć alerty dotyczące tych samych działań, które można wyszukiwać w dzienniku inspekcji. Zobacz [sekcję Więcej informacji](#more-information) , aby uzyskać listę typowych scenariuszy (i określonych działań do monitorowania), dla których możesz tworzyć alerty.

- Za pomocą strony **Alerty** aktywności w aplikacji Centrum zgodności platformy Microsoft 365 <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank"></a> tworzyć alerty tylko dla działań wykonywanych przez użytkowników wymienionych w książce adresowej organizacji. Na tej stronie nie można tworzyć alertów dotyczących działań wykonywanych przez użytkowników zewnętrznych, których nie wymieniono w książce adresowej.

## <a name="create-an-activity-alert"></a>Tworzenie alertu o aktywności

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a>.

2. Zaloguj się przy użyciu konta służbowego.

3. Na stronie **Alerty aktywności** kliknij ikonę ![Dodaj.](../media/8ee52980-254b-440b-99a2-18d068de62d3.gif) **Nowy**.

   Zostanie wyświetlona strona wysuuwana w celu utworzenia alertu o aktywności.


    ![Tworzenie alertu aktywności.](../media/53888bd5-9fa2-4398-8ccc-1a9dc72517ac.png)

4. Wypełnij następujące pola, aby utworzyć alert o działaniu:

    1. **Nazwa** — wpisz nazwę alertu. Nazwy alertów muszą być unikatowe w organizacji.

    1. **Opis** (opcjonalnie) — opis alertu, na przykład działań i użytkowników, do których są wysyłane powiadomienia e-mail, oraz użytkowników, do których są wysyłane powiadomienia. Opisy zapewniają szybki i łatwy sposób opisywania przeznaczenia alertu innym administratorom.

    1. **Typ alertu** — upewnij się, że **jest zaznaczona** opcja Niestandardowe.

    1. **Wyślij ten alert, gdy** — kliknij pozycję **Wyślij ten alert, gdy** i skonfiguruj te dwa pola:

       - **Działania** — kliknij listę rozwijaną, aby wyświetlić działania, dla których można utworzyć alert. Jest to ta sama lista działań, która jest wyświetlana podczas przeszukiwania dziennika inspekcji. Możesz wybrać co najmniej jedno konkretne działanie lub kliknąć nazwę grupy działań, aby zaznaczyć wszystkie działania w grupie. Opis tych działań można znaleźć w sekcji "Działania inspekcji" w sekcji [Przeszukiwanie dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md#audited-activities). Gdy użytkownik wykona jakiekolwiek działania dodane do alertu, zostanie wysłana wiadomość e-mail z powiadomieniem.

       - **Użytkownicy** — kliknij to pole, a następnie wybierz co najmniej jednego użytkownika. Jeśli użytkownicy w tym polu wykonają działania dodane do pola Działania, zostanie  wysłany alert. Pozostaw **pole Użytkownicy** puste, aby wysłać alert, gdy dowolny użytkownik w organizacji wykona działania określone przez alert.

    1. Wyślij ten **alert** do — kliknij pozycję Wyślij **ten alert**, a następnie kliknij w polu Adresaci i wpisz nazwę, aby dodać użytkowników, którzy otrzymają powiadomienie e-mail, gdy użytkownik (określony w polu Użytkownicy) wykona działanie (określone w  polu Działania). Pamiętaj, że domyślnie jesteś dodany do listy adresatów. Możesz usunąć swoją nazwę z tej listy.

5. Kliknij **przycisk Zapisz** , aby utworzyć alert.

    Nowy alert zostanie wyświetlony na liście na stronie **Alerty** aktywności.

    ![Na stronie Alerty aktywności zostanie wyświetlona lista alertów.](../media/02b774f2-1719-41de-bbc9-5e5b7576f335.png)

    Stan alertu zostanie ustawiony na **Wł**. Pamiętaj, że na liście są również adresaci, którzy otrzymają powiadomienie e-mail po wysłaniu alertu.

## <a name="turn-off-an-activity-alert"></a>Wyłączanie alertu aktywności

Możesz wyłączyć alert aktywności, aby nie wysyłać powiadomienia e-mail. Gdy wyłączysz alert o aktywności, będzie on nadal wyświetlany na liście alertów aktywności dla Twojej organizacji i nadal będzie można wyświetlać jego właściwości.

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a>.

2. Zaloguj się przy użyciu konta służbowego.

3. Na liście alertów aktywności dla organizacji kliknij alert, który chcesz wyłączyć.

4. Na stronie **Edytowanie alertu** kliknij przełącznik **Wł** ., aby zmienić stan na **Wyłączone, a** następnie kliknij przycisk **Zapisz**.

    Stan alertu na stronach Alerty **aktywności jest ustawiony** na **wartość Wyłączone**.

Aby ponownie włączyć alert aktywności, po prostu powtórz te czynności i kliknij przełącznik  Wyłącz, aby zmienić stan na **Włączony**.

## <a name="more-information"></a>Więcej informacji

- Oto przykład powiadomienia e-mail wysyłanego do użytkowników określonych w polu Wysłano ten alert do (i wyświetlane w obszarze Adresaci na stronie Alerty dotyczące aktywności)  w Centrum zgodności platformy Microsoft 365.

    ![Przykład powiadomienia e-mail wysłanego dla alertu o aktywności.](../media/a5f91611-fae6-4fe9-82f5-58521a2e2541.png)

- Oto niektóre typowe działania związane z dokumentami i pocztą e-mail, dla których można tworzyć alerty dotyczące aktywności. W tabelach opisano działanie, nazwę działania, dla których ma być utworzyć alert, oraz nazwę grupy działań, w ramach których dane działanie znajduje się na **liście** rozwijanej Działania. Aby wyświetlić pełną listę działań, dla których można tworzyć alerty dotyczące działań, zobacz sekcję "Działania zweryfikowane" w sekcji Przeszukiwanie [dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md#audited-activities).

    > [!TIP]
    > Możesz utworzyć alert aktywności tylko dla jednego działania wykonanego przez dowolnego użytkownika. Możesz też utworzyć alert aktywności, który śledzi wiele działań wykonanych przez co najmniej jednego użytkownika.

    W poniższej tabeli wymieniono niektóre typowe działania związane z dokumentem w SharePoint lub OneDrive dla Firm.

    | Gdy użytkownik to robi... | Tworzenie alertu dla tego działania | Grupa działań |
    |:-----|:-----|:-----|
    |Widoki dokumentu w witrynie.  |Uzyskano dostęp do pliku  |Działania związane z plikami i folderami  |
    |Edytuje lub zmienia dokument.  |Zmodyfikowano plik  |Działania związane z plikami i folderami  |
    |Udostępnia dokument użytkownikowi spoza organizacji.  |Udostępnianie pliku, folderu lub witryny  <br/> Oraz  <br/> Utworzono zaproszenie do udostępniania  <br/> Aby uzyskać więcej informacji, [zobacz Korzystanie z inspekcji udostępniania w dzienniku inspekcji](use-sharing-auditing.md).  |Działania związane z udostępnianiem i żądaniami dostępu  |
    |Przekazywanie lub pobieranie dokumentu.  |Przekazany plik  <br/> I/lub  <br/> Pobrano plik  |Działania związane z plikami i folderami  |
    |Zmienia uprawnienia dostępu do witryny.  |Zmodyfikowano uprawnienia witryny  |Działania administracyjne witryny  |

    W poniższej tabeli wymieniono niektóre typowe działania związane z pocztą e-mail w Exchange Online.

    | Gdy użytkownik to robi... | Tworzenie alertu dla tego działania | Grupa działań |
    |:-----|:-----|:-----|
    |Trwałe usuwanie (czyszczenie) wiadomości e-mail ze skrzynki pocztowej.  |Przeczyszczone wiadomości ze skrzynki pocztowej  | Exchange działań w skrzynce pocztowej  |
    |Wysyła wiadomość e-mail z udostępnionej skrzynki pocztowej.  |Wysłano wiadomość przy użyciu uprawnień Wyślij jako  <br/> Oraz  <br/> Wysłano wiadomość przy użyciu uprawnień Wyślij w imieniu  | Exchange działań w skrzynce pocztowej  |

- Za pomocą poleceń cmdlet **New-ActivityAlert** i **Set-ActivityAlert** w programie PowerShell w centrum zabezpieczeń & zgodności można także tworzyć i edytować alerty aktywności. Jeśli używasz tych polecenia cmdlet do tworzenia lub edytowania alertów dotyczących aktywności, pamiętaj o następujących kwestiach:

  - Jeśli za pomocą polecenia cmdlet dodasz działanie do alertu, który nie jest wymieniony na liście  rozwijanej Działania, na stronie właściwości zostanie wyświetlony komunikat z ostrzeżeniem o treści "Ten alert ma operacje niestandardowe, których nie wymieniono w szermierce".

  - Dobrym powodem tworzenia i edytowania alertów dotyczących aktywności przy użyciu tych polecenia cmdlet jest wysyłanie powiadomień e-mail do osób spoza organizacji. Ten użytkownik zewnętrzny zostanie wymieniony na liście adresatów alertu. Jeśli usuniesz tego użytkownika zewnętrznego z alertu, nie będzie można go ponownie dodać do alertu za pomocą **strony Edytowanie alertu** . Musisz ponownie dodać użytkownika zewnętrznego za pomocą polecenia cmdlet **Set-ActivityAlert** lub użyć polecenia cmdlet **New-ActivityAlert** , aby dodać tego samego (lub innego) użytkownika zewnętrznego do nowego alertu.
