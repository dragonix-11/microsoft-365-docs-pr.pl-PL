---
title: Korzystanie z samodzielnego logowania się w organizacji
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: seemg, pablom
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_signup
- AdminSurgePortfolio
- okr_SMB
search.appverid: MET150
description: Dowiedz się Microsoft 365 o samodzielnym rejestracji i dostępnych programach samoobsługowych, takich jak Microsoft Power Apps, Microsoft Power Automate i Dynamics 365 for Finance.
ms.date: 03/17/2021
ms.openlocfilehash: 67f0955a4485ea0f668b143f485b34cf2935404b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319861"
---
# <a name="using-self-service-sign-up-in-your-organization"></a>Korzystanie z samodzielnego logowania się w organizacji

Samodzielne logowanie się ułatwia użytkownikom w twojej organizacji korzystanie z usług online firmy Microsoft. Ten proces rejestracji nazywa się "samodzielnym logowaniem", ponieważ użytkownicy mogą tworzyć konta w celu korzystania z usług płatnych w ramach subskrypcji lub korzystać z bezpłatnych usług bez konieczności prosząc Cię o działanie w ich imieniu.

## <a name="how-self-service-sign-up-works"></a>Jak działa samodzielne logowanie się

W poniższym przykładzie opisano działanie samodzielnego rejestracji w szkole. Ten sam proces działa w przypadku każdej organizacji, w przypadku których w dzierżawie włączono programy samoobsługowe.

1. Uczniowie lub studenci i wykładowcy mają szkolne adresy e-mail, które wskazują, że są skojarzone z Twoją instytucją. Na przykład adres e-jakob@uw.edu może wskazywać ucznia na University of Washington.
2. Uczniowie, studenci i wykładowcy przejdą do naszej witryny [internetowej i za](https://go.microsoft.com/fwlink/p/?LinkId=536628) pomocą ich adresów e-mail zamówią konta w usługach oferowanych przez Twoją organizację, takich jak Aplikacje Microsoft 365 dla przedsiębiorstw. Mogą oni również utworzyć konta w innych bezpłatnych usługach, które oferujemy.
3. Sprawdzamy ich adresy e-mail i od razu mogą zacząć korzystać z Microsoft 365, Power BI lub innych usług.
4. Jako administrator biznesowy możesz sprawdzić, kto utworzyć konto w ramach subskrypcji, wybierając subskrypcję na stronie Licencjonowanie  w centrum administracyjne platformy Microsoft 365. Dzięki temu możesz sprawdzić, czy w Twojej dzierżawie istnieją nowe lub nierozpoznane licencje usług. Aby określić, czy użytkownicy mogą samodzielnie utworzyć konta w celu korzystania z subskrypcji, użyj polecenia cmdlet [Set-MsolCompanySettings programu](/powershell/module/msonline/set-msolcompanysettings) PowerShell z parametrem **AllowAdHocSubscriptions** . Aby uzyskać więcej informacji, [zobacz Jak kontrolować ustawienia samoobsługi?](/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)

## <a name="available-self-service-programs"></a>Dostępne programy samoobsługowe

Poniżej przedstawiono obecnie dostępne programy samoobsługowe. Ta lista będzie aktualizowana po dodaniu nowych programów.

| Program <br/> | Opis <br/> | Dodatkowe informacje <br/> | Witryna internetowa do samodzielnego rejestracji <br/> |
|:-----|:-----|:-----|:-----|
|Office 365 A1**** <br/> |Każdy uczeń lub nauczyciel może użyć szkolnego adresu e-mail, aby bezpłatnie utworzyć konto w usłudze Office 365 i uzyskać aplikacje Office dla sieci Web, 1 OneDrive TB przestrzeni dyskowej w chmurze i usługę SharePoint Online na witryny zajęć,  zespołu i projektów.  <br/> |[Office 365 Education — często zadawane pytania techniczne](/microsoft-365/education/deploy/office-365-education-self-sign-up) <br/> |[Office 365 Education](https://go.microsoft.com/fwlink/p/?linkid=140841) <br/> |
|**Office 365 A1 Plus** <br/> |Uprawnieni uczniowie i nauczyciele mogą utworzyć konta w programie Office 365 A1 Plus, który zawiera wszystko wymienione powyżej oraz Aplikacje Microsoft 365 dla przedsiębiorstw. Aplikacje Microsoft 365 dla przedsiębiorstw oprogramowania zwiększającego produktywność, w tym programów Word, PowerPoint, Excel, Outlook, OneNote, Publisher, Access i Skype dla firm , który jest zainstalowany na komputerze stacjonarnym lub przenośnym.  <br/> |[Office 365 Education — często zadawane pytania techniczne](/microsoft-365/education/deploy/office-365-education-self-sign-up) <br/> |[Office 365 Education](https://go.microsoft.com/fwlink/p/?linkid=140841) <br/> |
|**Power BI** <br/> |Power BI umożliwia użytkownikom wizualizowanie danych, udostępnianie odnajdowania i współpracę przy użyciu nowych, intuicyjnych metod. <br/> Jeśli Twoja organizacja już subskrybuje, możesz dodatkowo wyświetlić licencje "Power BI Pro wersji próbnej dla poszczególnych użytkowników", które zapewniają użytkownikom ograniczony, bezpłatny dostęp do zaawansowanych możliwości.  <br/> |[Power BI organizacji](./power-bi-in-your-organization.md) <br/> |[Microsoft Power BI](https://go.microsoft.com/fwlink/p/?LinkId=536629) <br/> |
|**Usługi zarządzania prawami (RMS)** <br/> |Rms dla użytkowników to bezpłatna subskrypcja samoobsługowa dla użytkowników w organizacji, którzy wysłali poufne pliki, które zostały chronione przez usługę Azure Rights Management (Azure RMS), ale ich dział IT nie zaimplementował usługi Azure Rights Management (Azure RMS) ani usługi Usługi Active Directory Rights Management (AD RMS).  <br/> |[Usługi RMS dla użytkowników indywidualnych i usługi Azure Rights Management](/azure/information-protection/rms-for-individuals) <br/> |[Portalu zarządzania prawami dostępu firmy Microsoft](https://portal.azure.com/) w celu sprawdzenia, czy można otworzyć dany dokument chroniony prawami.  <br/> |
|**Microsoft Power Apps** <br/> |W Power Apps możesz zarządzać danymi organizacyjnymi, uruchamiając aplikację utworzoną przez Ciebie lub utworzoną i udostępnioną Ci przez inną osobę. Aplikacje działają na urządzeniach przenośnych, takich jak telefony, lub można uruchamiać je w przeglądarce, otwierając usługę Dynamics 365. Możesz utworzyć nieskończoną liczbę różnych aplikacji — wszystko to bez uczenia się języka programowania, takiego jak C#.  <br/> |[Samodzielne rejestracja w Power Apps](/powerapps/maker/signup-for-powerapps) <br/> |[Microsoft Power Apps](https://go.microsoft.com/fwlink/p/?linkid=841462) <br/> |
|**Dynamics 365 for Financials** <br/> |Uzyskaj kompletne rozwiązanie do zarządzania biznesowego i finansowego dla małych i średnich firm. Usługa Dynamics 365 dla instytucji finansowych ułatwia zamawianie, sprzedaż, fakturowanie i raportowanie — począwszy od pierwszego dnia.  <br/> |[Microsoft Dynamics 365 for Financials](https://go.microsoft.com/fwlink/p/?linkid=841466) <br/> |[Microsoft Dynamics 365 for Financials](https://go.microsoft.com/fwlink/p/?linkid=841466) <br/> |
|**Microsoft Dynamics 365 for Operations** <br/> |Zwiększ szybkość swojej pracy biznesowej. Kompleksowe narzędzia ERP w umiecie Dynamics 365 for Operations zapewniają globalną skalowalność i analizę cyfrową, ułatwiając rozwój we własnym tempie.  <br/> |[Microsoft Dynamics 365 for Operations](https://go.microsoft.com/fwlink/p/?linkid=841467) <br/> |[Microsoft Dynamics 365 for Operations](https://go.microsoft.com/fwlink/p/?linkid=841467) <br/> |
|**Microsoft AppSource** <br/> |Aplikacja Microsoft AppSource to miejsce docelowe aplikacji biznesowych typu "oprogramowanie jako usługa" zbudowanych na platformie chmurowej firmy Microsoft. Aplikacja AppSource oferuje setki aplikacji, dodatków i pakietów zawartości, które rozszerzają funkcjonalność produktów firmy Microsoft, takich jak Azure, Dynamics 365, Office 365 i Power BI.  <br/> |[Microsoft AppSource](https://go.microsoft.com/fwlink/p/?linkid=841474) <br/> |[Microsoft AppSource](https://go.microsoft.com/fwlink/p/?linkid=841474) <br/> |
|**Microsoft Partner Incentives** <br/> |Sieć partnerów firmy Microsoft udostępnia trzy typy członkostwa. Każdy typ zapewnia zestaw korzyści, które ułatwiają rozwój firmy. W ramach realizacji swoich celów weź udział w programie na poziomie, który odpowiada Twoim unikatowym potrzebom, aby uzyskać dostęp do większej liczby korzyści i rozwijać swoją relację z nami i innymi partnerami w sieci.  <br/> |[Microsoft Partner Incentives](https://go.microsoft.com/fwlink/p/?linkid=841469) <br/> |[Microsoft Partner Incentives](https://go.microsoft.com/fwlink/p/?linkid=841469) <br/> |
|**Microsoft Business Center** <br/> |Microsoft Business Center to portal dla klientów, którzy dokonano zakupów w ramach umowy Microsoft Products and Services Agreement (MPSA). <br/> |[Szybki start: rejestrowanie się w witrynie Microsoft Business Center](https://go.microsoft.com/fwlink/p/?linkid=841479) <br/> |[Microsoft Business Center](https://go.microsoft.com/fwlink/p/?linkid=841470) <br/> |
|**Centrum usługi firmy Microsoft w licencjonowaniu licencjonowanym (Volume License Service Center) firmy Microsoft** <br/> |Centrum usług licencjonowania zbiorowego firmy Microsoft wyświetla licencje zakupione w ramach Enterprise, Select, Education (Campus lub School), Open Value, Open License i ISV w ramach umów licencyjnych.  <br/> |[Szkolenia i zasoby VLSC](https://www.microsoft.com/en-us/Licensing/existing-customer/vlsc-training-and-resources.aspx) <br/> |[Volume License Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx) <br/> |
|**Minecraft Education Edition** <br/> |Używając Minecraft jako platformy nauki, nauczyciele mogą motywować i zainspirować wszystkich uczniów, aby osiągnąć więcej, oraz zainspirować pasję do nauki. Dołącz do społeczności nauczycieli uczących się, jak za pomocą Minecraft odblokować potencjał uczniów.  <br/> |[Minecraft Education Edition](https://go.microsoft.com/fwlink/p/?linkid=841480) <br/> |[Minecraft Education Edition](https://go.microsoft.com/fwlink/p/?linkid=841471) <br/> |
|**Microsoft Stream** <br/> |Upload i udostępniać klipy wideo w organizacji w celu ulepszania komunikacji, uczestnictwa i nauki.  <br/> |[Środowisko logowania &amp; w dniu 0](https://go.microsoft.com/fwlink/p/?linkid=841472) <br/> |[Microsoft Stream](https://go.microsoft.com/fwlink/p/?linkid=841473) <br/> |
|**Power Automate** <br/> |Power Automate to produkt ułatwiający konfigurowanie automatycznych przepływów pracy między ulubionymi aplikacjami i usługami w celu synchronizowania plików, powiadomień, zbierania danych i wykonywania innych czynności.  <br/> |[Zarejestruj się i zaloguj się w celu Power Automate](/power-automate/sign-up-sign-in) <br/> |[Power Automate](https://go.microsoft.com/fwlink/p/?linkid=841465) <br/> |
|**Power Virtual Agents** <br/> |Power Virtual Agents umożliwia zespołom łatwe tworzenie zaawansowanych botów przy użyciu zaawansowanego, nie code graficznego interfejsu bez konieczności tworzenia danych i deweloperów. Power Virtual Agents wiele z głównych problemów związanych z tworzeniem botów w branży. Eliminuje to przerwy między ekspertami w  dziedzinie i zespołami programistów, które wybudowania botów, oraz długie opóźnienia między zespołami rozpoznania problemu i zaktualizowania bota w celu jego rozwiązania.  <br/> |[Licencjonowanie i szczegóły dostępu](/power-virtual-agents/requirements-licensing) <br/> |[Zarejestruj się w celu Power Virtual Agents](https://aka.ms/TryPVA) <br/> |
|**Azure AD B2B** <br/> |Azure Active Directory między firmami (B2B, Azure AD) pozwala zapraszać użytkowników zewnętrznych (czyli "gości") do korzystania z płatnych usług Azure AD. Niektóre funkcje są bezpłatne, ale w przypadku dowolnych płatnych funkcji usługi Azure AD możesz zaprosić maksymalnie pięciu użytkowników-gości na każdą licencję wersji usługi Azure AD, która należy do Ciebie dla pracownika lub użytkownika bez gościa w Twojej dzierżawie. <br/> |[Samoobsługowe logowanie się do współpracy między użytkownikami usługi Azure AD](/azure/active-directory/b2b/self-service-portal) <br/> |[Azure Active Directory licencjonowania współpracy B2B](/azure/active-directory/b2b/licensing-guidance) <br/> |
