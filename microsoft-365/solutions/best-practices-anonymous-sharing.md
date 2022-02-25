---
title: Najlepsze rozwiązania dotyczące udostępniania bez uwierzytelniania
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
ms.custom:
- seo-marvel-apr2020
ms.localizationpriority: high
f1.keywords: NOCSH
recommendations: false
description: W tym artykule znajdziesz najlepsze rozwiązania dotyczące udostępniania plików i folderów nieuwierzytanych użytkownikom.
ms.openlocfilehash: 40bf61820f28656e6f038e76f066e9b122b30177
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62959556"
---
# <a name="best-practices-for-sharing-files-and-folders-with-unauthenticated-users"></a>Najlepsze rozwiązania dotyczące udostępniania plików i folderów nieuwierzytanych użytkownikom

Nieuwierzyszczone *udostępnianie (linki* Każdy) może być wygodne i jest przydatne w różnych scenariuszach. *Każdy* link to najprostszy sposób udostępnienia: inne osoby mogą otworzyć link bez uwierzytelniania i mogą go przekazać innym osobom.

Zwykle nie cała zawartość w organizacji jest odpowiednia dla udostępniania bez uwierzytelniania. W tym artykule oczone są dostępne opcje, które ułatwiają utworzenie środowiska, w którym użytkownicy mogą korzystać z nieuwierzytanego udostępniania plików i folderów, ale tam, gdzie są dostępne zabezpieczenia chroniące zawartość organizacji.

> [!NOTE]
> Aby nieuwierzyszczone udostępnianie działało, musisz włączyć tę funkcję dla organizacji i dla indywidualnej witryny lub zespołu, z których będziesz korzystać. Zobacz [Współpraca z osobami spoza organizacji,](collaborate-with-people-outside-your-organization.md) aby zobaczyć scenariusz, który chcesz włączyć.

## <a name="set-an-expiration-date-for-anyone-links"></a>Ustawianie daty wygaśnięcia dla linków Każdy

Pliki są często przechowywane w witrynach, grupach i zespołach przez długi czas. Czasem istnieją zasady przechowywania danych, które wymagają przechowywania plików przez lata. Jeśli takie pliki są udostępniane nieuwierzytanych osobom, w przyszłości może to spowodować nieoczekiwany dostęp do plików i ich zmiany. Aby zminimalizować to możliwe, możesz skonfigurować czas wygaśnięcia dla linków *Każdy* .

Gdy link *Każdy* wygaśnie, nie można go już używać do uzyskiwania dostępu do zawartości.

Aby ustawić datę wygaśnięcia dla linków Każdy w organizacji

1. Otwórz SharePoint [administracyjnego](https://admin.microsoft.com/sharepoint).
2. W lewym okienku nawigacji rozwiń **pozycję Zasady**, a następnie kliknij pozycję **Udostępnianie**.
3. W **obszarze Wybierz opcje wygasania i uprawnień dla** linków Każdy zaznacz pole wyboru Te **linki muszą wygasać w ciągu tej wielu** dni.</br>
   ![Zrzut ekranu SharePoint wygasania linku każdy na poziomie organizacji.](../media/sharepoint-organization-anyone-link-expiration.png)
4. Wpisz liczbę dni w polu, a następnie kliknij przycisk **Zapisz**.

Aby ustawić datę wygaśnięcia dla linków Każdy w konkretnej witrynie

1. Otwórz SharePoint [administracyjnego](https://admin.microsoft.com/sharepoint).
2. W lewym okienku nawigacji rozwiń **pozycję Witryny**, a następnie kliknij pozycję **Aktywne witryny**.
3. Wybierz witrynę, którą chcesz zmienić, a następnie kliknij pozycję **Udostępnianie**.
4. W **obszarze Ustawienia zaawansowane dla linków Każda osoba** w obszarze Wygasanie linków Każdy wyczyść  pole wyboru Ustawienia na poziomie organizacji.</br>
   ![Zrzut ekranu SharePoint ustawienia wygasania linku każdy na poziomie witryny.](../media/sharepoint-organization-anyone-link-expiration-site.png)
5. Zaznacz opcję **Te linki muszą wygasać w ciągu tej** liczby dni, a następnie wpisz liczbę dni w polu.
6. Kliknij **Zapisz**.

Pamiętaj *, że po* wygaśnięciu linku Każda osoba plik lub folder można ponownie udostępnić noweowi *linkowi Każdy* .

Możesz ustawić *wygasanie* linków Każda osoba dla określonego OneDrive przy użyciu [set-SPOSite](/powershell/module/sharepoint-online/set-sposite).

## <a name="set-link-permissions"></a>Ustawianie uprawnień linku

Domyślnie linki *Każdy* dla pliku umożliwiają edytowanie pliku, a linki Każdy w folderze umożliwiają  edytowanie i wyświetlanie plików oraz przekazywanie nowych plików do tego folderu. Te uprawnienia można zmieniać dla plików i folderów niezależnie od siebie, aby były dostępne tylko do odczytu.

Jeśli chcesz zezwolić na udostępnianie bez uwierzytelniania, ale martwiSz się o nieuwierzytane osoby modyfikujące zawartość organizacji, rozważ ustawienie uprawnień do plików i folderów na **Wyświetlanie**.

Aby ustawić uprawnienia dla linków Każdy w organizacji

1. Otwórz SharePoint [administracyjnego](https://admin.microsoft.com/sharepoint).
2. W lewym okienku nawigacji kliknij pozycję **Udostępnianie**.
3. W **obszarze Ustawienia zaawansowane linków "Każdy"** wybierz uprawnienia do plików i folderów, których chcesz użyć.</br>
   ![Zrzut ekranu przedstawiający SharePoint uprawnień na poziomie organizacji Każdy link.](../media/sharepoint-organization-anyone-link-permissions.png)

Jeśli *dla linków* Każdy jest **ustawiona wartość Widok**, użytkownicy mogą nadal udostępniać pliki i foldery gościom oraz nadawać im uprawnienia do edytowania za pomocą *linków Określone* osoby. Te linki wymagają, aby osoby spoza organizacji uwierzytelniły się jako goście, a Ty możesz śledzić i monitorować aktywność gościa w plikach i folderach udostępnionych za pomocą tych linków.

## <a name="set-default-link-type-to-only-work-for-people-in-your-organization"></a>Ustawianie domyślnego typu linku tak, aby działał tylko dla osób w organizacji

Gdy *w organizacji* jest włączona funkcja udostępniania Każda osoba, domyślny link udostępniania jest zwykle **ustawiony na każdy**. Takie rozwiązanie może być wygodne dla użytkowników, ale może zwiększyć ryzyko niezamierzonego nieuwierzytania udostępniania. Jeśli użytkownik zapomni zmienić typ linku podczas udostępniania poufnego dokumentu, może przypadkowo utworzyć link do udostępniania, który nie wymaga uwierzytelniania.

To ryzyko można zminimalizować, zmieniając domyślne ustawienie linku na link, który działa tylko dla osób w organizacji. Użytkownicy, którzy chcą udostępniać nieuwierzyte osoby, będą wówczas muszą wybrać tę opcję.

Aby ustawić domyślny link do udostępniania plików i folderów dla organizacji
1. Otwórz SharePoint [administracyjnego](https://admin.microsoft.com/sharepoint).
2. W lewym okienku nawigacji kliknij pozycję **Udostępnianie**.
3. W **obszarze Linki do plików i folderów** wybierz pozycję **Tylko osoby w Twojej organizacji**.

   ![Zrzut ekranu przedstawiający SharePoint domyślnego typu linku.](../media/sharepoint-default-sharing-link-company-link.png)

4. Kliknij **przycisk Zapisz.**

Aby ustawić domyślny link do udostępniania plików i folderów dla konkretnej witryny
1. Otwórz SharePoint [administracyjnego](https://admin.microsoft.com/sharepoint).
2. W lewym okienku nawigacji rozwiń **pozycję Witryny**, a następnie kliknij pozycję **Aktywne witryny**.
3. Wybierz witrynę, którą chcesz zmienić, a następnie kliknij pozycję **Udostępnianie**.
4. W **obszarze Domyślny typ linku** udostępniania wyczyść pole wyboru Takie samo jak ustawienie **na** poziomie organizacji.

   ![Zrzut ekranu SharePoint domyślnych ustawień typu linku na poziomie witryny.](../media/sharepoint-organization-anyone-link-permissions-site.png)

5. Wybierz opcję **Tylko osoby w twojej organizacji i** kliknij przycisk **Zapisz**.

## <a name="prevent-unauthenticated-sharing-of-sensitive-content"></a>Zapobieganie nieuwierzytaniu zawartości poufnej

Możesz użyć funkcji [ochrony przed utratą danych (DLP, data loss prevention),](../compliance/dlp-learn-about-dlp.md) aby zapobiec nieuwierzyfaniu bez uwierzytelniania udostępniania poufnej zawartości. Zapobieganie utracie danych może podjąć działanie na podstawie etykiety wrażliwości pliku, etykiety przechowywania lub informacji poufnych w samym pliku.

Aby utworzyć regułę DLP
1. W centrum Microsoft 365 zgodności przejdź do strony [Ochrona przed utratą danych](https://compliance.microsoft.com/datalossprevention).
2. Kliknij **pozycję Utwórz zasady**.
3. Wybierz **pozycję Niestandardowe** i kliknij przycisk **Dalej**.
4. Wpisz nazwę zasad i kliknij przycisk **Dalej**.
5. Na stronie **Lokalizacje do zastosowania zasad** wyłącz wszystkie ustawienia z wyjątkiem witryn **SharePoint** i kont **OneDrive, a** następnie kliknij przycisk **Dalej**.
6. Na stronie **Definiowanie ustawień zasad** kliknij przycisk **Dalej**.
7. Na stronie **Dostosowywanie zaawansowanych reguł DLP** kliknij pozycję **Utwórz regułę** i wpisz nazwę reguły.
8. W **obszarze Warunki** kliknij **pozycję Dodaj warunek** i wybierz **pozycję Zawartość zawiera**.
9. Kliknij **pozycję** Dodaj i wybierz typ informacji, dla których chcesz zapobiec udostępnianiu bez uwierzytelniania.

   ![Zrzut ekranu przedstawiający opcje warunków, typy informacji poufnych, etykiety wrażliwości i etykiety przechowywania.](../media/limit-accidental-exposure-dlp-conditions.png)

10. W **obszarze** Akcje **kliknij pozycję Dodaj akcję** i wybierz **pozycję Ogranicz dostęp lub szyfruj zawartość w Microsoft 365 lokalizacjach**.
11. Zaznacz pole wyboru Ogranicz dostęp lub zaszyfruj zawartość Microsoft 365 lokalizacji, **a** następnie wybierz opcję Tylko osoby, którym udzielono dostępu do zawartości, za pomocą opcji "Każda osoba z **linkiem**".

      ![Zrzut ekranu przedstawiający opcje akcji reguły DLP.](../media/limit-accidental-exposure-dlp-anyone-links.png)

12. Kliknij **przycisk Zapisz** , a następnie kliknij przycisk **Dalej**.
13. Wybierz opcje testowania i kliknij przycisk **Dalej**.
14. Kliknij **pozycję Prześlij**, a następnie kliknij pozycję **Gotowe**.

## <a name="protect-against-malicious-files"></a>Ochrona przed złośliwymi plikami

Gdy zezwalasz użytkownikom anonimowym na przekazywanie plików, istnieje większe ryzyko, że ktoś przekaże złośliwy plik. W Microsoft 365 można użyć funkcji załączników wiadomości Sejf  programu Defender dla systemu Office 365 w celu automatycznego skanowania przekazanych plików i kwarantanny plików, które zostały uznanych za niebezpieczne.

Aby włączyć bezpieczne załączniki
1. Otwórz stronę [załączników załączników atP Sejf](https://protection.office.com/safeattachmentv2) w centrum administracyjnym Zabezpieczenia i zgodność.
2. Kliknij **pozycję Ustawienia globalne**.
3. Włącz atP dla SharePoint, OneDrive i Microsoft Teams.

   ![Zrzut ekranu przedstawiający ustawienie bezpiecznych załączników w Centrum zabezpieczeń i zgodności.](../media/safe-attachments-setting.png)

4. Opcjonalnie możesz również włączyć Sejf Dokumenty, a następnie kliknąć przycisk **Zapisz.**

Aby [uzyskać dodatkowe wskazówki, zobacz atP SharePoint, OneDrive i Microsoft Teams](../security/office-365-security/mdo-for-spo-odb-and-teams.md) oraz [Włączanie atP dla SharePoint, OneDrive i Microsoft Teams](../security/office-365-security/turn-on-mdo-for-spo-odb-and-teams.md).

## <a name="add-copyright-information-to-your-files"></a>Dodawanie informacji o prawach autorskich do plików

Jeśli korzystasz z etykiet wrażliwości w centrum administracyjnym zgodności usługi Microsoft 365, możesz skonfigurować etykiety w celu automatycznego dodawania znaku wodnego albo nagłówka lub stopki do dokumentów Office organizacji. W ten sposób możesz się upewnić, że pliki udostępnione zawierają informacje o prawach autorskich lub innych prawach własności.

Aby dodać stopkę do pliku z etykietą

1. Otwórz centrum [Microsoft 365 zgodności](https://compliance.microsoft.com).
2. W lewym obszarze nawigacji w **obszarze Rozwiązania** kliknij pozycję **Ochrona informacji**.
3. Kliknij etykietę, do której chcesz dodać stopkę, a następnie kliknij pozycję **Edytuj etykietę**.
4. Kliknij **przycisk Dalej** , aby dotrzeć do karty **Oznaczanie** zawartości, a następnie włącz opcję **Oznaczanie** zawartości.
5. Zaznacz pole wyboru obok typu tekstu, który chcesz dodać, a następnie kliknij pozycję **Dostosuj tekst**.
6. Wpisz tekst, który chcesz dodać do dokumentów, zaznacz odpowiednie opcje tekstu, a następnie kliknij przycisk **Zapisz**.</br>
   ![Zrzut ekranu przedstawiający zawartość oznaczania ustawień wrażliwości.](../media/content-marking-for-anonymous-sharing.png)
7. Kliknij **przycisk** Dalej, aby na koniec kreatora, a następnie kliknij przycisk **Zapisz etykietę**.

Jeśli dla etykiety jest włączone oznaczanie zawartości, określony tekst zostanie dodany do Office, gdy użytkownik nałoi na nie etykietę.

## <a name="see-also"></a>Zobacz też

[Omówienie etykiet wrażliwości](/Office365/SecurityCompliance/sensitivity-labels)

[Ograniczanie przypadkowego udostępnienia plików podczas udostępniania gościom](share-limit-accidental-exposure.md)

[Tworzenie bezpiecznego środowiska udostępniania gości](create-secure-guest-sharing-environment.md)
