---
title: Zbiorcze importowanie kontaktów zewnętrznych do programu Exchange Online
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
audience: End User
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOP150
ms.assetid: bed936bc-0969-4a6d-a7a5-66305c14e958
ms.custom: admindeeplinkEXCHANGE
description: Dowiedz się, jak administratorzy mogą Exchange Online programu PowerShell i pliku CSV do zbiorczego importowania kontaktów zewnętrznych do globalnej listy adresowej.
ms.openlocfilehash: fbb2d9bb93d9275e662872d945254d6bf27deb92
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63017809"
---
# <a name="bulk-import-external-contacts-to-exchange-online"></a>Zbiorcze importowanie kontaktów zewnętrznych do programu Exchange Online

**Ten artykuł jest dla administratorów. Czy próbujesz zaimportować kontakty do swojej skrzynki pocztowej? Zobacz [Importowanie kontaktów do Outlook](https://support.office.com/article/bb796340-b58a-46c1-90c7-b549b8f3c5f8)**
   
Czy Twoja firma ma wiele istniejących kontaktów biznesowych, które chcesz uwzględnić w udostępnionej książce adresowej (nazywanej również globalną listą adresową) w programie Exchange Online? Chcesz dodać kontakty zewnętrzne jako członków grup dystrybucyjnych, tak jak użytkowników wewnątrz firmy? Jeśli tak, możesz zbiorczo zaimportować kontakty zewnętrzne Exchange Online do programu PowerShell i pliku CSV (wartości rozdzielane przecinkami), aby zbiorczo zaimportować kontakty Exchange Online. Jest to proces trzystopniowy:
  
[Krok 1. Tworzenie pliku CSV zawierającego informacje o kontaktach zewnętrznych](#step-1-create-a-csv-file-that-contains-information-about-the-external-contacts)

[Krok 2. Tworzenie kontaktów zewnętrznych za pomocą programu PowerShell](#step-2-create-the-external-contacts-with-powershell) 

[Krok 3. Dodawanie informacji do właściwości kontaktów zewnętrznych](#step-3-add-information-to-the-properties-of-the-external-contacts)

Po zakończeniu importowania kontaktów możesz wykonać następujące dodatkowe zadania:
  
- [Dodawanie kolejnych kontaktów zewnętrznych](#add-more-external-contacts)
  
- [Ukrywanie kontaktów zewnętrznych w udostępnionej książce adresowej](#hide-external-contacts-from-the-shared-address-book)
  
## <a name="step-1-create-a-csv-file-that-contains-information-about-the-external-contacts"></a>Krok 1. Tworzenie pliku CSV zawierającego informacje o kontaktach zewnętrznych

Pierwszym krokiem jest utworzenie pliku CSV zawierającego informacje o każdym kontakcie zewnętrznym, który chcesz zaimportować do Exchange Online. 
  
1. Skopiuj poniższy tekst do pliku tekstowego w Notatniku i zapisz go na pulpicie jako plik CSV, używając sufiksu nazwy pliku .csv; na przykład: ExternalContacts.csv.
    
    > [!TIP]
    > Jeśli język zawiera znaki specjalne (takie jak **å**, **ä** i **ö** w języku szwedzkim), zapisz plik CSV przy użyciu kodowania UTF-8 lub innego kodowania Unicode podczas zapisywania pliku w Notatniku. 
  
    ```text
    ExternalEmailAddress,Name,FirstName,LastName,StreetAddress,City,StateorProvince,PostalCode,Phone,MobilePhone,Pager,HomePhone,Company,Title,OtherTelephone,Department,CountryOrRegion,Fax,Initials,Notes,Office,Manager
    danp@fabrikam.com,Dan Park,Dan,Park,1234 23rd Ave,Golden,CO,80215,206-111-1234,303-900-1234,555-1212,123-456-7890,Fabrikam,Shipping clerk,555-5555,Shipping,US,123-4567,R.,Good worker,31/1663,Dan Park
    pilar@contoso.com,Pilar Pinilla,Pilar,Pinilla,1234 Main St.,Seattle,WA,98017,206-555-0100,206-555-0101,206-555-0102,206-555-1234,Contoso,HR Manager,206-555-0104,Executive,US,206-555-0105,P.,Technical decision maker,31/1000,Dan Park
    ```

    Pierwszy wiersz w pliku CSV, czyli wiersz nagłówka, zawiera właściwości kontaktów, których można użyć podczas importowania kontaktów do Exchange Online. Poszczególne nazwy właściwości są rozdzielone przecinkami. Każdy wiersz poniżej wiersza nagłówka reprezentuje wartości właściwości do zaimportowania pojedynczego kontaktu zewnętrznego. 
    
    > [!NOTE]
    > Ten tekst zawiera przykładowe dane, które możesz usunąć. Nie usuwaj jednak pierwszego wiersza (nagłówka). Zawiera on wszystkie właściwości kontaktów zewnętrznych. 
  
2. Otwórz plik CSV w programie Microsoft Excel, aby edytować ten plik CSV, ponieważ znacznie łatwiej jest Excel pliku CSV.
    
3. Utwórz wiersz dla każdego kontaktu, który chcesz zaimportować do Exchange Online. Wypełnij jak najwięcej komórek. Te informacje będą wyświetlane w udostępnionej książce adresowej dla każdego kontaktu. 
    
    > [!IMPORTANT]
    >  Następujące właściwości (czyli pierwsze cztery elementy w wierszu nagłówka) są wymagane do utworzenia kontaktu zewnętrznego i muszą być wypełnione w pliku CSV: **ExternalEmailAddress**, **Name**, **FirstName**, **LastName**. Polecenie programu PowerShell uruchomione w kroku 2 spowoduje utworzenie kontaktów przy użyciu wartości tych właściwości. 

## <a name="step-2-create-the-external-contacts-with-powershell"></a>Krok 2. Tworzenie kontaktów zewnętrznych za pomocą programu PowerShell

Następnym krokiem jest zbiorcze zaimportowanie kontaktów zewnętrznych wymienionych w pliku CSV za pomocą pliku CSV utworzonego w kroku 1 i programu PowerShell w celu Exchange Online. 
  
1.  Połączenie PowerShell do Twojej Exchange Online organizacji. Instrukcje krok po kroku można znaleźć w [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pamiętaj, aby podczas łączenia się z programem PowerShell użyć nazwy użytkownika i hasła Exchange Online administratora globalnego. 
    
2. Po połączeniu programu PowerShell z programem Exchange Online przejdź do folderu pulpitu, w którym zapisano na przykład plik CSV w kroku 1`C:\Users\Administrator\desktop`.
    
3. Uruchom następujące polecenie, aby utworzyć kontakty zewnętrzne:

    ```powershell
    Import-Csv .\ExternalContacts.csv|%{New-MailContact -Name $_.Name -DisplayName $_.Name -ExternalEmailAddress $_.ExternalEmailAddress -FirstName $_.FirstName -LastName $_.LastName}
    ```

    Utworzenie nowych kontaktów może zająć trochę czasu w zależności od tego, ile ich importujesz. Po zakończeniu uruchamiania polecenia program PowerShell wyświetli listę nowych kontaktów, które zostały utworzone. 
    
4. Aby wyświetlić nowe kontakty zewnętrzne, przejdź do centrum Exchange administracyjnego, a następnie kliknij pozycję **Kontakty adresatów**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2182970" target="_blank"></a> 
    
    > [!TIP]
    > Aby uzyskać instrukcje dotyczące nawiązywania połączenia z Centrum administracyjnym programu [Exchange w programie Exchange Online](/exchange/exchange-admin-center). 
  
5. W razie potrzeby kliknij **pozycję Odśwież** , aby zaktualizować listę i wyświetlić zaimportowane kontakty zewnętrzne. 
    
    Zaimportowane kontakty pojawią się w udostępnionej książce adresowej w folderze Outlook i Outlook w sieci Web.
    
    > [!NOTE]
    > Kontakty można także wyświetlać w centrum administracyjne platformy Microsoft 365, przechodząc do strony **Kontakty** \> **użytkowników**. 

## <a name="step-3-add-information-to-the-properties-of-the-external-contacts"></a>Krok 3. Dodawanie informacji do właściwości kontaktów zewnętrznych

Po uruchomieniu polecenia w kroku 2 kontakty zewnętrzne zostaną utworzone, ale nie będą zawierać żadnych informacji dotyczących kontaktu lub organizacji, czyli informacji z większości komórek w pliku CSV. Wynika to z tego, że podczas tworzenia nowych kontaktów zewnętrznych wypełniane są tylko właściwości wymagane. Nie martw się, jeśli nie wszystkie informacje w pliku CSV zostały wypełnione. Jeśli jej tam nie ma, nie zostanie dodana.
  
1.  Połączenie PowerShell do Twojej Exchange Online organizacji. Instrukcje krok po kroku można znaleźć w [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
    
2. Przejdź do folderu pulpitu, w którym został zapisany plik CSV w kroku 1. na przykład `C:\Users\Administrator\desktop`.
    
3. Uruchom następujące dwa polecenia, aby dodać inne właściwości z pliku CSV do kontaktów zewnętrznych utworzonych w kroku 2.
    
    ```powershell
    $Contacts = Import-CSV .\ExternalContacts.csv
  
    ```

    ```powershell
    $contacts | ForEach {Set-Contact $_.Name -StreetAddress $_.StreetAddress -City $_.City -StateorProvince $_.StateorProvince -PostalCode $_.PostalCode -Phone $_.Phone -MobilePhone $_.MobilePhone -Pager $_.Pager -HomePhone $_.HomePhone -Company $_.Company -Title $_.Title -OtherTelephone $_.OtherTelephone -Department $_.Department -Fax $_.Fax -Initials $_.Initials -Notes  $_.Notes -Office $_.Office -Manager $_.Manager}
    ```

    > [!NOTE]
    > Parametr  _Manager_ może być problematyczny. Jeśli komórka w pliku CSV jest pusta, zostanie wyświetlany komunikat o błędzie i żadne z informacji o właściwościach nie zostaną dodane do kontaktu. Jeśli nie chcesz określać menedżera,  ` -Manager $_.Manager ` po prostu usuń je z poprzedniego polecenia programu PowerShell. 
  
    Aktualizacja kontaktów może zająć trochę czasu w zależności od tego, ile ich zaimportowano w kroku 1. 
    
4. Aby sprawdzić, czy właściwości zostały dodane do kontaktów: 
    
1. W centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange przejdź</a> do **pozycji Kontakty adresatów**\>.
    
2. Kliknij kontakt, a następnie kliknij **ikonę** ![Edytuj.](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) , aby wyświetlić właściwości kontaktu. 
    
To wszystko! Użytkownicy mogą zobaczyć kontakty i dodatkowe informacje w książce adresowej w Outlook i Outlook w sieci Web.
  
## <a name="add-more-external-contacts"></a>Dodawanie kolejnych kontaktów zewnętrznych

Możesz powtórzyć kroki od 1 do 3, aby dodać nowe kontakty zewnętrzne w Exchange Online. Ty lub użytkownicy w Twojej firmie możecie po prostu dodać nowy wiersz w pliku CSV dla nowego kontaktu. Następnie możesz uruchomić polecenia programu PowerShell z kroków 2 i 3, aby utworzyć i dodać informacje do nowych kontaktów.
  
> [!NOTE]
> Po uruchomieniu polecenia tworzenia nowych kontaktów może zostać wyświetlany komunikat o błędzie z informacją, że kontakty, które zostały utworzone wcześniej, już istnieją. Jednak każdy nowy kontakt dodany do pliku CSV zostanie utworzony. 
  
## <a name="hide-external-contacts-from-the-shared-address-book"></a>Ukrywanie kontaktów zewnętrznych w udostępnionej książce adresowej>

Niektóre firmy mogą korzystać z kontaktów zewnętrznych tylko po to, aby można je było dodawać jako członków grup dystrybucyjnych. W tym scenariuszu mogą zechcieć ukryć kontakty zewnętrzne w udostępnionej książce adresowej. W tym celu wykonaj następujące czynności:
  
1.  Połączenie PowerShell do Twojej Exchange Online organizacji. Instrukcje krok po kroku można znaleźć w [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
    
2. Aby ukryć jeden kontakt zewnętrzny, uruchom następujące polecenie.
    
    ```powershell
    Set-MailContact <external contact> -HiddenFromAddressListsEnabled $true 
    ```

    Aby na przykład ukryć pilar Pinilla w udostępnionej książce adresowej, uruchom to polecenie:

    ```powershell
    Set-MailContact "Pilar Pinilla" -HiddenFromAddressListsEnabled $true
    ```

3. Aby ukryć wszystkie kontakty zewnętrzne w udostępnionej książce adresowej, uruchom to polecenie:

    ```powershell
    Get-Contact -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'MailContact')} | Set-MailContact -HiddenFromAddressListsEnabled $true  
    ```

Po ukryciu kontakty zewnętrzne nie są wyświetlane w udostępnionej książce adresowej, ale nadal można je dodawać jako członków grupy dystrybucyjnej.