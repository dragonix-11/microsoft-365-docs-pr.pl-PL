---
title: Wdrażanie dodatki w centrum administracyjnym
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: Dowiedz się, jak wdrażać dodatki u użytkowników i grup w organizacji przy użyciu funkcji scentralizowanego wdrażania w centrum administracyjnym.
ms.openlocfilehash: e9f5cb01394d947a6b44e1c34870d33b0d6dd9bd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983943"
---
# <a name="deploy-add-ins-in-the-admin-center"></a>Wdrażanie dodatki w centrum administracyjnym

Dodatki pakietu Office ułatwiają personalizowanie dokumentów i usprawniają uzyskiwanie dostępu do informacji w sieci Web (zobacz [Rozpoczynanie korzystania z dodatków pakietu Office](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862)). Jako administrator możesz wdrażać dodatki Office dla użytkowników w organizacji, korzystając z funkcji scentralizowanego wdrażania w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365.</a> Scentralizowane wdrażanie jest zalecaną dla większości administratorów, najbogatszą w funkcje metodą wdrażania dodatków dla użytkowników oraz grup w organizacji.

Aby uzyskać więcej informacji na temat określania, czy Twoja organizacja może obsługiwać scentralizowane wdrażanie, zobacz Określanie, czy scentralizowane wdrażanie dodatków jest dla [Twojej organizacji.](centralized-deployment-of-add-ins.md)

Aby dowiedzieć się więcej o zarządzaniu dodatki po wdrożeniu, zobacz Zarządzanie dodatki [w centrum administracyjnym.](manage-addins-in-the-admin-center.md)
  
> [!NOTE]
>  W przypadku programu Word usługi Excel i PowerPoint wdrażaj dodatki w wykazie aplikacji SharePoint, aby wdrażać dodatki u użytkowników w środowisku lokalnym bez połączenia z usługą Microsoft 365 i/lub obsługą wymaganych dodatków SharePoint.[](/office/dev/add-ins/publish/publish-task-pane-and-content-add-ins-to-an-add-in-catalog) Do Outlook użyj Exchange sterowania w celu wdrożenia w środowisku lokalnym bez połączenia z Microsoft 365.
  
## <a name="recommended-approach-for-deploying-office-add-ins"></a>Zalecana metoda wdrażania dodatków pakietu Office

Aby wdać dodatki etapami, zalecamy:
  
1. Wdaj dodatek w niewielki zestaw uczestników projektu biznesowego i członków działu IT. Jeśli wdrożenie się powiedzie, przejdź do kroku 2.
    
2. Wdaj dodatek u większej liczby osób w firmie. Ponownie oceń wyniki i, jeśli uda się, przejdź do pełnego wdrożenia.
    
3. Przekonuj pełne rozsyłanie zadań dla wszystkich użytkowników.
    
W zależności od rozmiaru docelowej grupy odbiorców możesz dodać lub usunąć kroki rzutowania.
  
## <a name="deploy-an-office-add-in-using-the-admin-center"></a>Wdrażanie dodatku Office przy użyciu centrum administracyjnego

Przed rozpoczęciem zobacz Określanie, czy scentralizowane wdrażanie dodatków [jest danej organizacji](centralized-deployment-of-add-ins.md).
  
1. W centrum administracyjnym przejdź do strony **Ustawienia** \> **dodatki**. Jeśli nie widzisz strony dodatków,  \>  \> przejdź  do strony Ustawienia dodatki **zintegrowanych** aplikacji.

2. Wybierz **pozycję Wdeksuj** dodatek u góry strony, a następnie wybierz przycisk **Dalej**.

    > [!NOTE]
    > Dodatki można także wdrażać w centrum administracyjnym za [pośrednictwem zintegrowanych aplikacji](test-and-deploy-microsoft-365-apps.md). Zintegrowane aplikacje są widoczne dla administratorów globalnych Exchange administratorów. Jeśli nie widzisz powyższych kroków, przejdź do sekcji Scentralizowane wdrażanie, przechodząc  >  do Ustawienia **Integrrated apps**. W górnej części strony **zintegrowane aplikacje** wybierz **pozycję Dodatki**.

3. Wybierz opcję i postępuj zgodnie z instrukcjami.
  
4. Jeśli wybrano opcję dodawania dodatku ze Sklepu Office, wybierz dodatek. </br>

    Dostępne dodatki można wyświetlać według kategorii: **Sugerowane dla Ciebie**, **Klasyfikacja** lub **Nazwa**. Ze Sklepu Office dostępne są tylko dodatki bezpłatne. Dodatki płatne nie są obecnie obsługiwane. Po wybraniu dodatku zaakceptuj postanowienia i kontynuuj. <br/> 

    > [!NOTE]
    > Dzięki opcji Office Store aktualizacje i ulepszenia są automatycznie wdrażane u użytkowników.

5. Na następnej stronie wybierz pozycję **Wszyscy**, Określeni użytkownicy **/** grupy lub Po  prostu ja, aby określić, u kogo jest wdrożony dodatek. Użyj pola wyszukiwania, aby znaleźć konkretnych użytkowników lub grupy. <br/>

    > [!NOTE]
    > Aby poznać inne stany dotyczące dodatku, zobacz Stany [dodatku](./manage-addins-in-the-admin-center.md).
  
6. Wybierz **pozycję Wdeksuj**.
  
7. Po wdrożeniu dodatku pojawi się zielony znacznik. Postępuj zgodnie z instrukcjami na stronie, aby przetestować dodatek.

    > [!NOTE]
    > Użytkownicy mogą potrzebować ponownego Office, aby wyświetlić ikonę dodatku na wstążce aplikacji. Outlook dodatki na wstążce aplikacji mogą pojawiać się w ciągu 24 godzin.

8. Po zakończeniu wybierz pozycję **Dalej**. Jeśli wdrożono dodatek tylko u siebie, możesz wybrać pozycję Zmień osoby, które mają dostęp do dodatku, aby wdrożyć dodatek u większej liczby użytkowników.

    Jeśli dodatek został wdrożony u innych członków organizacji, postępuj zgodnie z instrukcjami, aby poinformować o wdrożeniu dodatku. <br/>
  
    Warto poinformować użytkowników i grupy, że wdrożony dodatek jest dostępny. Rozważ wysłanie wiadomości e-mail z opisem, kiedy i jak używać dodatku. Dołącz zawartość Pomocy lub często zadawane pytania (lub link do nich), które mogą pomóc użytkownikom w przypadku problemów z tym dodatku.
  
### <a name="considerations-when-assigning-an-add-in-to-users-and-groups"></a>Zagadnienia dotyczące przypisywania dodatku do użytkowników i grup

Administratorzy globalni Exchange administratorami globalnymi mogą przypisywać dodatek wszystkim lub określonym użytkownikom i grupom. Z każdą z tych opcji wiążą się pewne konsekwencje:
  
- **Wszyscy** Ta opcja powoduje przypisanie dodatku każdemu użytkownikowi w organizacji. Tej opcji używaj oszczędnie i tylko w przypadku dodatków, które są naprawdę uniwersalne dla Twojej organizacji.

- **Użytkownicy** Jeśli przypiszesz dodatek do pojedynczego użytkownika, a następnie wdrożysz dodatek u nowego użytkownika, musisz najpierw dodać nowego użytkownika.

- **Grupy** Jeśli przypiszesz dodatek do grupy, dodatek zostanie automatycznie przypisany do użytkowników dodanych do grupy. Gdy użytkownik zostanie usunięty z grupy, traci dostęp do dodatku. W obu przypadkach administrator nie musi nic więcej akcję.

- **Tylko ja** Jeśli przypiszesz dodatek tylko do siebie, zostanie on przypisany tylko do Twojego konta, które jest idealnym rozwiązaniem do testowania dodatku.

Wybór odpowiedniej opcji dla organizacji zależy od konfiguracji. Jednak zalecamy wykonywanie zadań za pomocą grup. Jako administrator, możesz łatwiej zarządzać dodatki za pomocą grup i kontrolować członkostwo w tych grupach, zamiast przypisywać poszczególnych użytkowników za każdym razem. W niektórych sytuacjach może być konieczne ograniczenie dostępu do niewielkiego zestawu użytkowników przez przypisanie ich do określonych użytkowników przez ich ręczne przypisanie.
  
## <a name="more-about-office-add-ins-security"></a>Więcej informacji Office zabezpieczeń dodatków

Dodatki pakietu Office zawierają plik manifestu w formacie XML, w którym znajdują się pewne metadane dotyczące dodatku oraz, co najważniejsze, który wskazuje aplikację internetową zawierającą cały kod i logikę. Dodatki mogą mieć różnorodne możliwości. Na przykład dodatki mogą:
  
- wyświetlać dane,

- odczytywać dokument użytkownika w celu dostarczenia usług kontekstowych,

- odczytywać i zapisywać dane w dokumencie użytkownika w celu podania wartości dla tego użytkownika.

Aby uzyskać więcej informacji na temat typów dodatków pakietu Office i ich funkcji, zobacz [Omówienie platformy dodatków pakietu Office](/office/dev/add-ins/overview/office-add-ins)  zwłaszcza sekcję „Anatomia dodatku pakietu Office".
  
Aby współdziałać z dokumentem użytkownika, dodatek musi zadeklarować, jakich uprawnień potrzebuje, w pliku manifestu. Pięciopoziomowy model uprawnień dostępu interfejsu API języka JavaScript stanowi podstawę dla prywatności i zabezpieczeń dla użytkowników dodatków okienek zadań. Większość dodatków w witrynie Sklep Office obsługuje poziom odczytu i zapisu dokumentu, a niemal wszystkie dodatki obsługują co najmniej poziom odczytu dokumentu. Aby uzyskać więcej informacji o poziomach uprawnień, zobacz [Żądanie poświadczeń na potrzeby używania interfejsu API w dodatkach zawartości i okienek zadań](/office/dev/add-ins/develop/requesting-permissions-for-api-use-in-content-and-task-pane-add-ins).
  
Podczas aktualizowania pliku manifestu typowe zmiany dotyczą ikony i tekstu dodatku. Od czasu do czasu zmieniają się polecenia dodatku. Jednak uprawnienia dodatku nie są zmieniane. Aplikacja internetowa, gdzie jest uruchamiany cały kod i logika dla dodatku, może zmienić się w dowolnym momencie, co jest normalne w przypadku aplikacji internetowych.
  
Aktualizacje dodatków są przeprowadzane w następujący sposób:
  
- **Dodatek biznesowy:** W takim przypadku, kiedy administrator jawnie przekazał manifest, dodatek wymaga, aby administrator przekazał nowy plik manifestu w celu obsługi zmian metadanych. Przy kolejnym uruchomieniu odpowiednich aplikacji pakietu Office dodatek zostanie zaktualizowany. Aplikacja internetowa może się zmienić w dowolnym momencie.

    > [!NOTE]
    > Administrator nie musi usuwać dodatku LOB w celu wykonywania aktualizacji.   W sekcji Dodatki administrator może po prostu kliknąć dodatek LOB i wybrać przycisk Aktualizuj w prawym dolnym rogu. Aktualizacja będzie działać tylko wtedy, gdy wersja nowego dodatku jest większa niż wersja istniejącego dodatku.

- **Dodatek ze Sklepu Office:** Jeśli administrator wybrał dodatek w witrynie Sklep Office, to w przypadku aktualizacji tego dodatku w witrynie Sklep Office zostanie on następnie zaktualizowany w funkcji Scentralizowane wdrażanie. Przy kolejnym uruchomieniu odpowiednich aplikacji pakietu Office dodatek zostanie zaktualizowany. Aplikacja internetowa może się zmienić w dowolnym momencie.
  
## <a name="related-content"></a>Zawartość pokrewna

[Zarządzanie dodatki w centrum administracyjnym](manage-addins-in-the-admin-center.md) (artykuł)\
[Tworzenie pierwszego dodatku okienko zadań Word](/office/dev/add-ins/quickstarts/word-quickstart?tabs=yeomangenerator) (artykuł\
[Osoby niepełnoletnie i uzyskiwanie dodatków ze sklepu](minors-and-acquiring-addins-from-the-store.md) (artykuł)\
[Zarządzanie dodatkimi za pomocą poleceń cmdlet programu PowerShell](../../enterprise/use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md) dla funkcji Scentralizowane wdrażanie (artykuł)\
[Rozwiązywanie problemów: Użytkownik nie widzi dodatków](/office365/troubleshoot/access-management/user-not-seeing-add-ins) (artykuł)
