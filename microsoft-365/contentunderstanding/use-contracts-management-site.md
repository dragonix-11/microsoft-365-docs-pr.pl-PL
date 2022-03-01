---
title: Używanie szablonu witryny Zarządzanie umowami dla aplikacji Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.reviewer: kkameth
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Dowiedz się, jak zapewniać i dostosowywać szablon witryny Zarządzanie umowami oraz jak go używać w aplikacji Microsoft SharePoint Syntex.
ms.openlocfilehash: 649596392cf2d7a8fc90ffc479d8875c69f26ffe
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015407"
---
# <a name="use-the-contracts-management-site-template-for-microsoft-sharepoint-syntex"></a>Używanie szablonu witryny Zarządzanie umowami dla aplikacji Microsoft SharePoint Syntex

Witryna Zarządzanie umowami to gotowy do wdrożenia i dostosowywalny SharePoint szablonu witryny, który pomaga organizacji maksymalizować wartość SharePoint Syntex. Witryna została zaprojektowana w taki sposób, aby można było utworzyć profesjonalną witrynę do zarządzania, przetwarzania i śledzenia stanu umów w organizacji.

## <a name="features-of-the-site"></a>Funkcje witryny

![Zrzut ekranu przedstawiający stronę główną szablonu witryny Zarządzanie umowami.](../media/content-understanding/contracts-management-site-home-page.png)

Witryna Zarządzanie umowami zawiera wstępnie wypełnione strony, składników Web Part i nawigację po witrynie. Witrynę można dostosować tak, aby zawierała znakowanie swojej organizacji, informacje o pracownikach, informacje o zasadach i planowaniu, przepływy pracy, kontakty i zasoby.

Witryna korzysta z możliwości modelu dokumentów SharePoint Syntex w bibliotekach dokumentów w celu klasyfikowania dokumentów i wyodrębniania metadanych. Witryna udostępnia wstępnie utworzone biblioteki dokumentów, które są potrzebne do szybkiego rozpoczęcia pracy, ale można również tworzyć własne, zgodnie z potrzebami. Witryna zawiera następujące polecane biblioteki:

- **Regiony** — klasyfikowanie dokumentów kontraktowych według obszaru geograficznego, kraju lub regionu.

- **Szablony** — wybierz odpowiedni szablon umowy dla typu umowy, na przykład umowy o nie ujawnianiu informacji, umowy o świadczenie usług i oświadczenia o pracę.

- **Żądania kontraktu** — rozpoczynanie zlecenia kontraktu bezpośrednio w zespole kontraktowym.

- **Klienci** — znajdowanie informacji o kliencie w jednej wygodnej lokalizacji.

- **Modele** — ta biblioteka modeli pozwala klasyfikować dokumenty i wyodrębniać metadane. Użytkownicy mogą tworzyć własne modele dopasowane do potrzeb i dodawać je do tej biblioteki.

- **Przykładowa biblioteka umów** — znajdź pliki, które były klasyfikowane i miały metadane wyodrębnione przy użyciu SharePoint Syntex projektu. 

W bibliotece istnieje osobny widok, w którym można śledzić inne metadane, takie jak stan, i który korzysta z formatowania biblioteki dokumentów w celu pokazania ich w bardziej wizualny sposób.

## <a name="provision-the-site"></a>Inicjowanie obsługi administracyjnej witryny

Witryna Zarządzanie umowami może być zapewniana za pomocą SharePoint [książki adresowej](https://lookbook.microsoft.com/).

![Zrzut ekranu przedstawiający stronę inicjowania obsługi szablonu witryny Zarządzanie umowami.](../media/content-understanding/contracts-management-site-provisioning-page.png)

> [!NOTE]
> Aby aprowizować witrynę, SharePoint administrator globalny Microsoft 365 administratorem globalnym. Aby dodać ten szablon witryny SharePoint Syntex organizacji, musisz również mieć licencję witryny.

1. Na stronie głównej książki [SharePoint w](https://lookbook.microsoft.com/) **menu** >  Wyświetl projekty wybierz pozycję SharePoint Syntex **SharePoint Syntex Zarządzanie umowami**.

2. Na stronie **Zarządzanie umowami** wybierz pozycję **Dodaj do dzierżawy**.

    ![Zrzut ekranu przedstawiający przycisk Dodaj do dzierżawy na stronie inicjowania obsługi administracyjnej szablonu witryny Zarządzanie umowami.](../media/content-understanding/contracts-management-site-add-to-your-tenant.png)

3. Wprowadź swój adres e-mail (w celu powiadomienia o tym, kiedy witryna będzie gotowa do użycia), adres URL witryny, którego chcesz użyć, oraz tytuł, którego chcesz użyć dla witryny. 

    ![Zrzut ekranu przedstawiający pola adresu e-mail i adresu URL witryny na stronie inicjowania obsługi administracyjnej szablonu witryny Zarządzanie umowami.](../media/content-understanding/contracts-management-email-and-site-url.png)

4. Wybierz **pozycję Inicjowanie** obsługi administracyjnej i w krótkim czasie Twoja witryna będzie gotowa do użycia. Otrzymasz wiadomość e-mail (wysłaną na podany przez Ciebie adres e-mail) z informacją o zakończeniu procesu inicjowania obsługi szablonu witryny Zarządzanie umowami.

5. Wybierz **pozycję Otwórz** witrynę, aby wyświetlić witrynę Zarządzanie umowami. Tutaj możesz eksplorować witrynę oraz dostosowywać strony i zawartość. 

Aby uzyskać więcej informacji na temat inicjowania obsługi z SharePoint książki adresowej, zobacz [Zapewnianie nowych ścieżek edukacyjnych](/office365/customlearning/custom_provision).

## <a name="customize-the-site"></a>Dostosowywanie witryny

Przed udostępnieniem witryny Zarządzanie umowami innym użytkownikom należy dostosować witrynę do swoich wymagań. 

### <a name="customize-the-look-and-feel-of-your-site"></a>Dostosowywanie wyglądu i wyglądu witryny

Dostosuj następujące elementy witryny do potrzeb organizacji:

- Zaktualizuj [znakowanie w](https://support.microsoft.com/office/customize-your-sharepoint-site-320b43e5-b047-4fda-8381-f61e8ac7f59b) witrynie Zarządzanie umowami, aby dopasować je do organizacji.
- Dostosuj element [web part Element hero](https://support.microsoft.com/office/use-the-hero-web-part-d57f449b-19a0-4b0d-8ce3-be5866430645) , aby zawierał obrazy rzeczywistych witryn w organizacji, jeśli to możliwe.
- Dostosuj składników [Web Part Kontakty](https://support.microsoft.com/office/show-people-profiles-on-your-page-with-the-people-web-part-7e52c5f6-2d72-48fa-a9d3-d2750765fa05) , aby zawierał informacje kontaktowe dla menedżerów kontraktu lub innych osób.
- Dostosuj część [Web Part Tekst](https://support.microsoft.com/office/add-text-and-tables-to-your-page-with-the-text-web-part-729c0aa1-bc0d-41e3-9cde-c60533f2c801) , aby dodać akapity do opcji formatowania, takich jak style, punktory, wcięcia, wyróżnienia i linki.
- Dostosowywanie składników [Web Part Obraz](https://support.microsoft.com/office/use-the-image-web-part-a63b335b-ad0a-4954-a65d-33c6af68beb2) w celu dodania obrazu do strony.
- Dostosowywanie składników [Web Part Szybkich linków w](https://support.microsoft.com/office/use-the-quick-links-web-part-e1df7561-209d-4362-96d4-469f85ab2a82) celu organizowania i wyświetlania linków do innych zasobów.
- Dodaj [inne składników Web Part](https://support.microsoft.com/office/using-web-parts-on-sharepoint-pages-336e8e92-3e2d-4298-ae01-d404bbe751e0) do witryny zgodnie z potrzebami.
- Dostosuj [układy stron zgodnie](https://support.microsoft.com/office/add-sections-and-columns-on-a-sharepoint-modern-page-fc491eb4-f733-4825-8fe2-e1ed80bd0899) z potrzebami.
- Dodaj [nowe strony,](https://support.microsoft.com/office/create-and-use-modern-pages-on-a-sharepoint-site-b3d46deb-27a6-4b1e-87b8-df851e503dec) aby dodać dodatkową pomoc techniczną lub zasoby informacyjne.

### <a name="customize-the-site-navigation"></a>Dostosowywanie nawigacji w witrynie

Masz kontrolę nad nawigacją w witrynie Zarządzanie umowami. Skorzystaj z następujących zasobów, które pomogą Ci wprowadzić zmiany zgodne z Twoją organizacją:

- Dostosowywanie [nawigacji witryny](https://support.microsoft.com/office/customize-the-navigation-on-your-sharepoint-site-3cd61ae7-a9ed-4e1e-bf6d-4655f0bf25ca).
- [Skojarz tę witrynę z centrum](https://support.microsoft.com/office/associate-a-sharepoint-site-with-a-hub-site-ae0009fd-af04-4d3d-917d-88edb43efc05).
- [Docelowa grupa odbiorców](https://support.microsoft.com/office/target-navigation-news-and-files-to-specific-audiences-33d84cb6-14ed-4e53-a426-74c38ea32293) umożliwia kierowanie konkretnych linków nawigacyjnych do określonych użytkowników. 
- [W razie potrzeby usuń](https://support.microsoft.com/office/delete-a-page-from-a-sharepoint-site-1d4197b8-31b6-460d-906b-3fb492a51db1) niechciane strony.

## <a name="share-the-site-with-others"></a>Udostępnianie witryny innym osobom

[Udostępnianie witryny innym osobom](https://support.microsoft.com/office/share-a-site-958771a8-d041-4eb8-b51c-afea2eae3658). Współpraca z innymi osobami w organizacji w celu zapewnienia, że witryna Zarządzanie umowami jest powszechnie znana i przyjęte.

Najważniejsze czynniki sukcesu w zarządzaniu witryną Zarządzanie umowami:

- Świętuj wprowadzenie witryny Zarządzanie umowami.
- Tworzenie i ogłaszanie wiadomości z ogłaszania nowego zasobu.
- Zadbaj o to, aby użytkownicy mieli dosyć pytań i opinii.
- Skorzystaj z [analiz witryny,](https://support.microsoft.com/office/view-usage-data-for-your-sharepoint-site-2fa8ddc2-c4b3-4268-8d26-a772dc55779e) aby promować zawartość na stronie głównej, aktualizować nawigację lub ponownie pisać zawartość w celu zwiększenia przejrzystości.
- Przejrzyj witrynę Zarządzanie umowami zgodnie z potrzebami, aby upewnić się, że zawartość jest świeża i nadal potrzebna.

## <a name="see-also"></a>Zobacz też

[Zarządzanie umowami przy użyciu Microsoft 365 rozwiązania](solution-manage-contracts-in-microsoft-365.md)