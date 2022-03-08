---
title: Konfigurowanie łącznika do archiwizowania danych z usługi LinkedIn
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Dowiedz się, jak administratorzy mogą & używać natywnego łącznika do importowania danych ze strony firmy serwisu LinkedIn w celu Microsoft 365.
ms.openlocfilehash: 944a8bcbd06a07653ccf5e98e28807d279b66023
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322201"
---
# <a name="set-up-a-connector-to-archive-linkedin-data"></a>Konfigurowanie łącznika do archiwizowania danych z usługi LinkedIn

Za pomocą łącznika w Centrum zgodności platformy Microsoft 365 importować i archiwizować dane ze stron Firmy LinkedIn. Po skonfigurowaniu i skonfigurowaniu łącznika połączy się on z kontem konkretnej strony Firmy LinkedIn co 24 godziny. Łącznik konwertuje wiadomości opublikowane na stronie Firma na wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej w Microsoft 365.

Po zapisaniu danych strony LinkedIn Company w skrzynce pocztowej możesz zastosować funkcje zgodności usługi Microsoft 365, takie jak archiwizacja w związku z postępowaniem sądowym, wyszukiwanie zawartości, In-Place archiwizowanie, inspekcja i zasady przechowywania Microsoft 365 do danych usługi LinkedIn. Można na przykład wyszukać te elementy przy użyciu funkcji Przeszukiwanie zawartości lub skojarzyć skrzynkę pocztową magazynu ze współpracownikiem w Advanced eDiscovery przypadku. Utworzenie łącznika do importowania i archiwizowania danych z usługi LinkedIn Microsoft 365 organizacji zgodnie z zasadami rządowymi i przepisami.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Użytkownik, który tworzy łącznik strony firmy w serwisie LinkedIn, musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Musisz mieć poświadczenia logowania (adres e-mail lub numer telefonu i hasło) konta użytkownika w serwisie LinkedIn, które jest administratorem strony firmy LinkedIn, którą chcesz zarchiwizować. Poświadczenia te są używane do logowania się do usługi LinkedIn podczas konfigurowania łącznika.

- Łącznik usługi LinkedIn może importować łącznie 200 000 elementów w jednym dniu. Jeśli dziennie istnieje więcej niż 200 000 elementów z usługi LinkedIn, żaden z tych elementów nie zostanie zaimportowany do Microsoft 365.

## <a name="create-a-linkedin-connector"></a>Tworzenie łącznika usługi LinkedIn

1. Przejdź do, <https://compliance.microsoft.com> a następnie kliknij pozycję **Łączniki** **danychLinkedW** >  stronach firmy.

2. Na stronie **produktu w serwisie LinkedIn** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania usługi** wybierz pozycję **Zaakceptuj**.

4. Na stronie **Zaloguj się za pomocą usługi LinkedIn** kliknij pozycję **Zaloguj się za pomocą usługi LinkedIn**.

   Zostanie wyświetlona strona logowania do usługi LinkedIn.

   ![Stronie logowania do usługi LinkedIn.](../media/LinkedInSigninPage.png)

5. Na stronie logowania do usługi LinkedIn wprowadź adres e-mail (lub numer telefonu) i hasło dla konta w serwisie LinkedIn skojarzonego ze stroną firmy, którą chcesz zarchiwizować, a następnie kliknij pozycję **Zaloguj się.**

   Zostanie wyświetlona strona kreatora z listą wszystkich stron firmowych w serwisie LinkedIn skojarzonych z kontem, do których się zalogowano. Łącznik można skonfigurować tylko dla jednej strony firmowej. Jeśli Twoja organizacja ma wiele stron firmowych w serwisie LinkedIn, musisz utworzyć łącznik dla każdej z nich.

   ![Zostanie wyświetlona strona z listą stron firmy w serwisie LinkedIn.](../media/LinkedInSelectCompanyPage.png)

6. Wybierz stronę firmy, z której chcesz zarchiwizować elementy, a następnie kliknij przycisk **Dalej**.

7. Na stronie **Wybieranie lokalizacji przechowywania** kliknij w polu, wybierz adres e-mail skrzynki pocztowej usługi Microsoft 365, do których będą importowane elementy z usługi LinkedIn, a następnie kliknij przycisk **Dalej**. Elementy są importowane do folderu skrzynki odbiorczej w tej skrzynce pocztowej.

8. Kliknij **przycisk Dalej** , aby przejrzeć ustawienia łącznika, a następnie kliknij przycisk **Zakończ,** aby zakończyć konfigurację łącznika.

Po utworzeniu łącznika możesz wrócić na stronę Łączniki danych, aby zobaczyć postęp procesu importowania nowego łącznika (w razie potrzeby wybierz pozycję Odśwież, aby zaktualizować listę łączników). Wartość w kolumnie **Stan** to **Oczekiwanie na rozpoczęcie**. Aby rozpocząć początkowy proces importowania, może upłynie do 24 godzin. Po pierwszym uruchomieniu łącznika i zaimportowaniu elementów z usługi LinkedIn łącznik będzie uruchamiany raz na 24 godziny i zaimportować wszystkie nowe elementy utworzone na stronie firmy LinkedIn w ciągu poprzednich 24 godzin.

Aby wyświetlić więcej szczegółów, zaznacz łącznik na liście na stronie **Łączniki** danych w celu wyświetlenia strony wysuwu. W **obszarze** Stan wyświetlany zakres dat wskazuje filtr wieku wybrany podczas tworzenia łącznika.

## <a name="more-information"></a>Więcej informacji

Elementy z usługi LinkedIn są importowane do podfolderu usługi LinkedIn w skrzynce odbiorczej skrzynki pocztowej magazynu w Microsoft 365. Są one wyświetlane jako wiadomości e-mail.