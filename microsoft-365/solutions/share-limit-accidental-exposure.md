---
title: Ograniczanie przypadkowej ekspozycji
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
ms.custom: admindeeplinkSPO
ms.localizationpriority: high
f1.keywords: NOCSH
recommendations: false
description: Dowiedz się, jak ograniczyć przypadkowy dostęp do informacji podczas udostępniania plików osobom spoza organizacji.
ms.openlocfilehash: c1bf6424e2be70118dd2d85671a857a8a33ef2f9
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329061"
---
# <a name="limit-accidental-exposure-to-files-when-sharing-with-people-outside-your-organization"></a>Ograniczanie przypadkowego udostępnienia plików osobom spoza organizacji

Udostępniając pliki i foldery osobom spoza organizacji, możesz ograniczyć ryzyko przypadkowego udostępnienia poufnych informacji. Możesz wybrać jedną z opcji w tym artykule, aby jak najlepiej spełniać potrzeby Twojej organizacji.

## <a name="use-best-practices-for-anyone-links"></a>Linki Każdy mogą korzystać z najlepszych rozwiązań

Jeśli osoby w Organizacji muszą udostępniać bez uwierzytelniania, ale martwi Cię, że nieuwierzytane osoby modyfikują zawartość, przeczytaj Najlepsze rozwiązania dotyczące nieuwierzytanego udostępniania, aby uzyskać wskazówki dotyczące pracy z nieuwierzytnionym udostępnianiem w organizacji.[](best-practices-anonymous-sharing.md)

## <a name="turn-off-anyone-links"></a>Wyłączanie linków Każdy

Zalecamy pozostawienie *włączonych* linków Każdy dla odpowiedniej zawartości, ponieważ jest to najprostszy sposób udostępniania i może zmniejszyć ryzyko szukania innych rozwiązań, które znajdują się poza kontrolą działu IT. *Każdy* link może być przesyłany dalej innym osobom, ale dostęp do plików jest dostępny tylko dla osób, które mają link.

Jeśli chcesz, aby osoby spoza organizacji zawsze były uwierzytelniane podczas uzyskiwania dostępu do zawartości w SharePoint, grupach lub Teams, możesz wyłączyć *każdy* udostępniający. Uniemożliwi to użytkownikom nieuwierzyszczone udostępnianie zawartości.

Jeśli wyłączysz *linki Każdy* , użytkownicy nadal mogą łatwo udostępniać gościom linki *Określone* osoby. W takim przypadku od wszystkich osób spoza organizacji będzie wymagane uwierzytelnienie się w celu uzyskania dostępu do udostępnianej zawartości.

W zależności od potrzeb możesz *wyłączyć linki Każdy* dla konkretnych witryn lub dla całej organizacji.

Aby wyłączyć linki *Każdy* w organizacji

1. W centrum SharePoint w lewym okienku nawigacji wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Udostępnianie**</a>.
2. Ustaw SharePoint udostępniania zewnętrznego na **wartość Nowi i istniejący goście**.

   ![Zrzut ekranu przedstawiający ustawienia SharePoint udostępniania zewnętrznego witryny na poziomie organizacji.](../media/sharepoint-organization-external-sharing-controls-new-users.png)

3. Kliknij **Zapisz**.

Aby wyłączyć linki *Każdy* dla witryny

1. W centrum SharePoint w lewym okienku nawigacji rozwiń pozycję **Witryny** i wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktywne witryny**</a>.
2. Wybierz witrynę, którą chcesz skonfigurować.
3. Na wstążce wybierz pozycję **Udostępnianie**.
4. Upewnij się, że udostępnianie jest ustawione na **wartość Nowi i istniejący goście**.

   ![Zrzut ekranu przedstawiający poziom witryny SharePoint ustawień udostępniania zewnętrznego witryny.](../media/sharepoint-site-external-sharing-settings.png)

5. Jeśli zostały wprowadzone zmiany, wybierz pozycję **Zapisz**.

## <a name="domain-filtering"></a>Filtrowanie domeny

Listy domen mogą być zezwalane na domeny lub listy odmów, aby określić domeny, których użytkownicy mogą używać podczas udostępniania osobom spoza organizacji.

Za pomocą listy zezwalań możesz określić listę domen, które użytkownicy w Twojej organizacji mogą udostępniać osobom spoza organizacji. Udostępnianie innym domenom jest zablokowane. Jeśli Twoja organizacja współpracuje tylko z osobami z listy określonych domen, możesz użyć tej funkcji, aby uniemożliwić udostępnianie innym domenom.

W przypadku listy domen odrzucanych możesz określić listę domen, z których użytkownicy w Twojej organizacji nie mogą udostępniać osobom spoza organizacji. Udostępnianie domenom na liście jest zablokowane. Może to być przydatne, jeśli masz konkurentów, na przykład tych, którym chcesz uniemożliwić dostęp do zawartości w Twojej organizacji.

Listy zezwalania i odmów mają wpływ tylko na udostępnianie gościom. Użytkownicy mogą nadal udostępniać użytkownikom niedozwolone domeny za pomocą linków Każdy, jeśli ich nie wyłączysz. Aby uzyskać najlepsze wyniki z listami domen zezwalających i odrzucanych, rozważ wyłączenie linków *Każdy* zgodnie z powyższym opisem.

Aby skonfigurować listę domen ze zezwalania lub odrzucania

1. W centrum SharePoint w lewym okienku nawigacji wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Udostępnianie.**</a>
2. W **obszarze Zaawansowane ustawienia udostępniania zewnętrznego** zaznacz **pole wyboru Ogranicz udostępnianie zewnętrzne według** domeny.
3. Kliknij **pozycję Dodaj domeny**.
4. Określ, czy chcesz blokować domeny, wpisz domeny i kliknij przycisk **OK**.

   ![Zrzut ekranu SharePoint udostępniania zewnętrznego według ustawienia domeny.](../media/sharepoint-sharing-block-domain.png)

5. Kliknij **Zapisz**.

Jeśli chcesz ograniczyć udostępnianie według domeny na poziomie wyższym niż SharePoint i OneDrive, możesz zezwolić na udostępnianie lub zablokować zaproszenia do użytkowników [B2B](/azure/active-directory/b2b/allow-deny-list) z określonych organizacji w Azure Active Directory. (Aby te ustawienia wpłynąć na SharePoint i OneDrive [B2B w usłudze Azure AD Preview](/sharepoint/sharepoint-azureb2b-integration-preview), należy skonfigurować integrację usług i usług SharePoint i OneDrive).

## <a name="limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups"></a>Ograniczanie udostępniania plików, folderów i witryn osobom spoza organizacji do określonych grup zabezpieczeń

Możesz ograniczyć udostępnianie plików, folderów i witryn osobom spoza organizacji członkom określonej grupy zabezpieczeń. Jest to przydatne, jeśli chcesz włączyć udostępnianie zewnętrzne, ale z przepływem pracy zatwierdzania lub procesem żądania. Możesz również wymagać od użytkowników ukończenia kursu szkoleniowego, zanim zostaną dodani do grupy zabezpieczeń i mogą udostępniać je zewnętrznie.

Aby ograniczyć udostępnianie zewnętrzne do członków grupy zabezpieczeń

1. W centrum SharePoint w lewym obszarze nawigacji w **obszarze Zasady wybierz** pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Udostępnianie**</a>.
2. W **obszarze Udostępnianie zewnętrzne** **rozwiń pozycję Więcej ustawień udostępniania zewnętrznego**.

3. Wybierz **pozycję Zezwalaj tylko użytkownikom w określonych grupach zabezpieczeń** na udostępnianie zewnętrzne, a następnie wybierz pozycję **Zarządzaj grupami zabezpieczeń**.

    ![Zrzut ekranu przedstawiający panel Zarządzanie grupami zabezpieczeń.](/sharepoint/sharepointonline/media/manage-security-groups.png)

4. W **polu Dodaj grupę zabezpieczeń** wprowadź nazwę grupy zabezpieczeń. Zostanie wyświetlone okno grupy zabezpieczeń.

5. Obok nazwy grupy zabezpieczeń z listy rozwijanej **Może udostępniać** za pomocą wybierz jedną z tych opcji:

    - **Tylko uwierzytelnieni goście** (domyślnie)
    - **Każdy**

6. Wybierz **Zapisz**.

Pamiętaj, że dotyczy to plików, folderów i witryn, ale nie wpływa Microsoft 365 grup ani Teams. Gdy członkowie zapraszają gości do grupy Microsoft 365 grupy lub prywatnego zespołu w programie Microsoft Teams, zaproszenie jest wysyłane do grupy lub właściciela zespołu w celu zatwierdzenia.

## <a name="see-also"></a>Zobacz też

[Tworzenie bezpiecznego środowiska udostępniania gości](create-secure-guest-sharing-environment.md)

[Najlepsze rozwiązania dotyczące udostępniania plików i folderów użytkownikom anonimowym](best-practices-anonymous-sharing.md)
