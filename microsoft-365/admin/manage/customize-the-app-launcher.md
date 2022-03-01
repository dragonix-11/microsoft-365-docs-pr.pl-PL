---
title: Dodawanie kafelków niestandardowych do obszaru Uruchamianie aplikacji
f1.keywords:
- CSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 1136115a-75af-4497-b693-640c4ce70bc6
description: Twórz szybkie linki do wiadomości e-mail, dokumentów, aplikacji, witryn SharePoint, witryn zewnętrznych i innych zasobów, dodając kafelki niestandardowe do ikony Uruchamianie aplikacji.
ms.openlocfilehash: 31121df0e1af6b8fc2be1e61ba7e0cd0714affa2
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2022
ms.locfileid: "63016568"
---
# <a name="add-custom-tiles-to-the-app-launcher"></a>Dodawanie kafelków niestandardowych do obszaru Uruchamianie aplikacji

W Microsoft 365 Uruchamianie aplikacji możesz szybko i łatwo uzyskać dostęp do poczty e-mail, kalendarzy, dokumentów i [aplikacji (dowiedz się więcej](https://support.microsoft.com/office/79f12104-6fed-442f-96a0-eb089a3f476a)). Są to aplikacje, które możesz uzyskać razem Microsoft 365, a także aplikacje niestandardowe, które możesz dodać ze sklepu [SharePoint Store](https://support.microsoft.com/office/dd98e50e-d3db-4ecb-9bb7-82b189822d43) lub [Azure AD](/previous-versions/office/office-365-api/).
  
Do obszaru Uruchamianie aplikacji możesz dodawać własne kafelki niestandardowe, które wskazują witryny programu SharePoint, witryny zewnętrzne, starsze aplikacje i inne. Kafelek niestandardowy zostanie wyświetlony na karcie aplikacji **Wszystkie** obszaru Uruchamianie aplikacji, ale możesz go przypiąć do karty aplikacji **Strona główna** i poprosić swoich użytkowników, aby postąpili w ten sam sposób. Pozwoli Ci to łatwo wyszukiwać witryny, aplikacje i zasoby, których potrzebujesz do wykonywania swoich zadań. W poniższym przykładzie kafelek niestandardowy o nazwie „Portal firmy Contoso" służy do uzyskiwania dostępu do intranetowej witryny programu SharePoint organizacji. 
  
![Uruchamianie aplikacji.](../../media/7acc06cc-ac7a-4c6e-8ea7-81570a5bdbab.png)
  
## <a name="add-a-custom-tile-to-the-app-launcher"></a>Dodawanie kafelka niestandardowego do obszaru Uruchamianie aplikacji

1. Zaloguj się do centrum administracyjnego jako administrator globalny,  >  przejdź do Ustawienia **Org Ustawienia** i wybierz **kartę Profil** organizacji.
    
2. Na karcie **Profil organizacji** wybierz pozycję **Niestandardowe kafelki uruchamianie aplikacji**.
  
3. Wybierz **pozycję Dodaj kafelek niestandardowy**. 
  
4. W polu **Nazwa kafelka** wprowadź nazwę nowego kafelka. Nazwa będzie wyświetlana na kafelku. 
    
5. Wprowadź adres **URL witryny internetowej** kafelka. Jest to miejsce, do którego użytkownicy będą mieli dostęp, gdy wybierzą kafelek w ikony Uruchamianie aplikacji. W adresie URL użyj protokołu HTTPS.

    > [!TIP]
    > Jeśli tworzysz kafelek dla witryny programu SharePoint, przejdź do tej witryny, skopiuj jej adres URL i wklej go w tym miejscu. Adres URL domyślnej witryny zespołu wygląda następująco: `https://<company_name>.sharepoint.com` 
  
6. Wprowadź **adres URL obrazu** dla kafelka. Obraz pojawi się na stronie Moje aplikacje i w obszarze ikony Uruchamianie aplikacji.

    > [!TIP]
    > Obraz powinien mieć rozmiar 60x60 pikseli i być dostępny dla wszystkich osób w organizacji bez konieczności uwierzytelniania.

7. Wprowadź **Opis** kafelka. Jest on wyświetlony po wybraniu kafelka na stronie Moje aplikacje i wybraniu **opcji Szczegóły aplikacji**. 
  
8. Wybierz **pozycję Zapisz zmiany** , aby utworzyć kafelek niestandardowy. 
    
    Kafelek niestandardowy pojawi się w obszarze Uruchamianie aplikacji na karcie Wszystkie dla Ciebie i Twoich użytkowników  w ciągu 24 godzin. 

    > [!NOTE]
    > Jeśli nie widzisz kafelka niestandardowego utworzonego w poprzednich krokach, upewnij się, że masz przypisaną skrzynkę pocztową usługi Exchange Online i zalogowano się do niej co najmniej raz. Te kroki są wymagane w przypadku kafelków niestandardowych w Microsoft 365. 
  
## <a name="edit-or-delete-a-custom-tile"></a>Edit or delete a custom tile

1. W centrum administracyjnym przejdź **do karty Ustawienia** >  **Org Ustawienia** >  **Organizacja** profilu.
    
2. Na stronie **Profil organizacji** przejdź do kafelków Niestandardowe uruchamianie **aplikacji. Jeśli** wybierzesz trzy kropki obok kafelka niestandardowego i wybierzesz **Edytuj kafelek niestandardowy**.

3. Zaktualizuj informacje w polach **Nazwa kafelka**, **Adres URL**, **Opis** i **Adres URL obrazu** dla kafelka niestandardowego (zobacz [Dodawanie kafelka niestandardowego do obszaru Uruchamianie aplikacji](#add-a-custom-tile-to-the-app-launcher)).
    
4. Wybierz **pozycję Aktualizuj** \> **zamknij**. 
    
Aby usunąć kafelek niestandardowy, w **oknie Kafelki** niestandardowe zaznacz ten kafelek i wybierz pozycję **Usuń** **kafelekDeletuj** > . 
  
## <a name="next-steps"></a>Następne kroki

 Aby dostosować wygląd i sposób Microsoft 365 do marki organizacji, zobacz Dostosowywanie Microsoft 365 [motywu](../setup/customize-your-organization-theme.md).

## <a name="related-content"></a>Zawartość pokrewna

[Przypinanie aplikacji do ikony Uruchamianie aplikacji](pin-apps-to-app-launcher.md) użytkowników (artykuł)\
[Uaktualnianie Microsoft 365 użytkowników biznesowych do najnowszej wersji Office klienta](../setup/upgrade-users-to-latest-office-client.md) (artykuł)\
[Zarządzanie dodatki w centrum](../manage/manage-addins-in-the-admin-center.md) administracyjnym (artykuł)
