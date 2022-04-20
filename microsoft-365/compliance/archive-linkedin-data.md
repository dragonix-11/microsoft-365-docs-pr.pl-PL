---
title: Konfigurowanie łącznika do archiwizowania danych linkedin
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 04/06/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Dowiedz się, jak administratorzy mogą skonfigurować & za pomocą łącznika natywnego do importowania danych ze strony firmy LinkedIn do Microsoft 365.
ms.openlocfilehash: de39d0e3e95164a39f9aed1a227ab15f6e4fd7d6
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64937240"
---
# <a name="set-up-a-connector-to-archive-linkedin-data"></a>Konfigurowanie łącznika do archiwizowania danych linkedin

Użyj łącznika w portalu zgodności usługi Microsoft Purview, aby zaimportować i zarchiwizować dane ze stron firmy LinkedIn. Po skonfigurowaniu i skonfigurowaniu łącznika łączy się on z kontem dla określonej strony firmy LinkedIn raz na 24 godziny. Łącznik konwertuje komunikaty opublikowane na stronie firmy na wiadomość e-mail, a następnie importuje te elementy do skrzynki pocztowej w Microsoft 365.

Po zapisaniu danych strony firmy LinkedIn w skrzynce pocztowej można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, wyszukiwanie zawartości, In-Place archiwizowanie, inspekcja i zasady przechowywania Microsoft 365 do danych linkedin. Możesz na przykład wyszukać te elementy przy użyciu funkcji wyszukiwania zawartości lub skojarzyć skrzynkę pocztową magazynu z opiekunem w przypadku zbierania elektronicznych materiałów dowodowych w usłudze Microsoft Purview (Premium). Utworzenie łącznika do importowania i archiwizowania danych linkedin w Microsoft 365 może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Użytkownikowi tworzącemu łącznik strony firmy LinkedIn musi zostać przypisana rola administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Musisz mieć poświadczenia logowania (adres e-mail lub numer telefonu i hasło) konta użytkownika LinkedIn, które jest administratorem strony firmy LinkedIn, którą chcesz zarchiwizować. Te poświadczenia są używane do logowania się do usługi LinkedIn podczas konfigurowania łącznika.

- Łącznik LinkedIn może zaimportować łącznie 200 000 elementów w ciągu jednego dnia. Jeśli w ciągu dnia jest więcej niż 200 000 elementów LinkedIn, żaden z tych elementów nie zostanie zaimportowany do Microsoft 365.

## <a name="create-a-linkedin-connector"></a>Tworzenie łącznika linkedin

1. Przejdź do strony<https://compliance.microsoft.com>, a następnie kliknij pozycję **Łączniki** >  **danychŁącz strony firmy**.

2. Na stronie produktu **strony firmy LinkedIn** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania** wybierz pozycję **Akceptuj**.

4. Na stronie **Zaloguj się przy użyciu linkedin** kliknij pozycję **Zaloguj się przy użyciu linkedin**.

   Zostanie wyświetlona strona logowania linkedin.

   ![Strona logowania linkedin.](../media/LinkedInSigninPage.png)

5. Na stronie logowania linkedin wprowadź adres e-mail (lub numer telefonu) i hasło dla konta LinkedIn skojarzonego ze stroną firmy, którą chcesz zarchiwizować, a następnie kliknij pozycję **Zaloguj się**.

   Zostanie wyświetlona strona kreatora z listą wszystkich stron firmy LinkedIn skojarzonych z kontem, na które się zalogowano. Łącznik można skonfigurować tylko dla jednej strony firmowej. Jeśli Twoja organizacja ma wiele stron firmy LinkedIn, musisz utworzyć łącznik dla każdej z nich.

   ![Zostanie wyświetlona strona z listą stron firmy LinkedIn.](../media/LinkedInSelectCompanyPage.png)

6. Wybierz stronę firmy, z których chcesz zarchiwizować elementy, a następnie kliknij przycisk **Dalej**.

7. Na stronie **Wybieranie lokalizacji magazynu** kliknij w polu, wybierz adres e-mail skrzynki pocztowej Microsoft 365, do których zostaną zaimportowane elementy LinkedIn, a następnie kliknij przycisk **Dalej**. Elementy są importowane do folderu skrzynki odbiorczej w tej skrzynce pocztowej.

8. Kliknij **przycisk Dalej** , aby przejrzeć ustawienia łącznika, a następnie kliknij przycisk **Zakończ** , aby ukończyć konfigurację łącznika.

Po utworzeniu łącznika możesz wrócić do strony **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika (w razie potrzeby wybierz pozycję **Odśwież** , aby zaktualizować listę łączników). Wartość w kolumnie **Stan** to **Oczekiwanie na rozpoczęcie**. Rozpoczęcie początkowego procesu importowania trwa do 24 godzin. Po pierwszym uruchomieniu łącznika i zaimportowaniu elementów linkedin łącznik będzie uruchamiany raz na 24 godziny i importuje wszystkie nowe elementy utworzone na stronie firmy LinkedIn w ciągu ostatnich 24 godzin.

Aby wyświetlić więcej szczegółów, wybierz łącznik na liście na stronie **Łączniki danych** , aby wyświetlić stronę wysuwaną. W obszarze **Stan** wyświetlany zakres dat wskazuje filtr wieku wybrany podczas tworzenia łącznika.

## <a name="more-information"></a>Więcej informacji

Elementy linkedin są importowane do podfolderu LinkedIn w skrzynce odbiorczej skrzynki pocztowej magazynu w Microsoft 365. Są one wyświetlane jako wiadomości e-mail.