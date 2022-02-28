---
title: Uaktualnianie Office 2010 do wersji Microsoft 365 — Microsoft 365 administratorem
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- Adm_TOC
search.appverid:
- BCS160
- MET150
- MOE150
ms.custom:
- fwlink 824861; CampaignID
- O365_Comm_SR_UpgradeOffice
- seo-marvel-may2020
- fwlink 824861; CampaignID O365_Comm_SR_UpgradeOffice
- AdminSurgePortfolio
ms.assetid: f6b00895-b5fd-4af6-a656-b7788ea20cbb
description: Dowiedz się, jak Microsoft Office do najnowszej wersji Office klienta usługi dla użytkowników w organizacji.
ms.topic: article
ms.openlocfilehash: 0dad3c22e9011dd0453f719178d94ef67138220c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987788"
---
# <a name="upgrade-your-microsoft-365-for-business-users-to-the-latest-office-client"></a>Uaktualnianie Microsoft 365 użytkowników biznesowych do najnowszej wersji Office klienta

## <a name="office-2010-reaches-end-of-support"></a>Office 2010 kończy się wsparcie techniczne

Office 13 października 2020 r. zakończyło się wsparcie techniczne. Firma Microsoft nie będzie już zapewniać następujących usług:

- Pomoc techniczna w zakresie problemów

- Poprawki błędów dotyczące wykrytych problemów

- Poprawki zabezpieczeń dotyczące wykrytych luk

Aby [uzyskać Office, zobacz zakończenie 2010 r.](/deployoffice/endofsupport/office-2010-end-support-roadmap) planu pomocy technicznej.

 **Czy ten temat jest dla Ciebie odpowiedni?**
  
 Jeśli jesteś administratorem odpowiedzialnym za subskrypcję usługi Microsoft 365 dla firm w Twojej organizacji, jesteś we właściwym miejscu. Administratorzy są zazwyczaj odpowiedzialni za zadania, takie jak zarządzanie użytkownikami, resetowanie haseł, zarządzanie Office instalacjami oraz dodawanie lub usuwanie licencji.

 Jeśli nie jesteś administratorem i masz produkt pakietu Microsoft 365 Family, zobacz Jak uaktualnić usługę [Office](https://support.microsoft.com/office/ee68f6cf-422f-464a-82ec-385f65391350), aby uzyskać informacje na temat uaktualniania starszej wersji pakietu [Office](https://support.microsoft.com/office/28cbc8cf-1332-4f04-9123-9b660abb629e#BKMK_OfficePlans).

## <a name="get-ready-to-upgrade-to-microsoft-365"></a>Przygotuj się do uaktualnienia do Microsoft 365

Jako administrator możesz kontrolować, jaką wersję pakietu Office mogą instalować osoby w Twojej organizacji. Zdecydowanie zalecamy, aby pomóc użytkownikom w organizacji w uruchamianiu starszych wersji programu Office, takich jak Office 2010, Office 2013 lub Office 2016, uaktualnienie do najnowszej wersji w celu skorzystania z ulepszeń zabezpieczeń i produktywności.

## <a name="upgrade-steps"></a>Czynności uaktualniania

Poniższe kroki poprowadzi Cię przez proces uaktualniania użytkowników do najnowszej wersji Office klasycznego. Zalecamy zapoznanie się z tymi krokami przed rozpoczęciem procesu uaktualniania.
  
## <a name="step-1---check-system-requirements"></a>Krok 1. Sprawdzanie wymagań systemowych

[Sprawdź wymagania systemowe pakietu](https://www.microsoft.com/microsoft-365/microsoft-365-and-office-resources) Office, aby się upewnić, że Twoje urządzenia są zgodne z najnowszą wersją pakietu Office. Na przykład nowszych wersji programu Office nie można zainstalować na komputerach z systemem Windows XP lub Windows Vista.
  
> [!TIP]
> Jeśli masz w organizacji użytkowników korzystających ze starszych wersji programu Windows na swoich komputerach PC lub laptopach, zalecamy uaktualnienie do Windows 10. Windows 7 zakończyło wsparcie techniczne. Przeczytaj [Pomoc techniczna dla Windows 7 kończy się stycznia 2020 r](https://www.microsoft.com/microsoft-365/windows/end-of-windows-7-support?rtc=1)., aby uzyskać więcej informacji.

Zapoznaj się z [Windows 10 systemowymi](https://www.microsoft.com/windows/windows-10-specifications), aby sprawdzić, czy możesz uaktualnić ich systemy operacyjne.

### <a name="check-application-compatibility"></a>Sprawdzanie zgodności aplikacji

Aby zapewnić pomyślne uaktualnienie, zalecamy zidentyfikowanie aplikacji pakietu Office, w tym skryptów VBA, makr, dodatków innych firm oraz złożonych dokumentów i arkuszy kalkulacyjnych, a także ocenę ich zgodności z najnowszą wersją pakietu Office.
  
Jeśli na przykład używasz dodatków innych firm w bieżącej instalacji pakietu Office, skontaktuj się z producentem, aby upewnić się, że są one zgodne z najnowszą wersją Office.
  
## <a name="step-2---check-your-existing-subscription-plan"></a>Krok 2. Sprawdzanie istniejącego planu subskrypcji

Niektóre Microsoft 365 nie zawierają pełnych wersji klasycznych pakietu Office, a kroki uaktualniania są inne, jeśli Twój plan nie zawiera Office.
  
Nie masz pewności, jaki masz plan subskrypcji? Zobacz [Microsoft 365 subskrypcji dla firm?](../admin-overview/what-subscription-do-i-have.md)
  
Jeśli Twój istniejący plan obejmuje Office, przejdź do kroku 3. — [Odinstalowywanie i Office](#step-3---uninstall-office).
  
Jeśli Twój istniejący plan nie zawiera opcji Office, wybierz jedną z poniższych opcji:
  
### <a name="upgrade-options-for-plans-that-dont-include-office"></a>Opcje uaktualniania w przypadku planów, które nie zawierają Office

 **Opcja 1. Przełączanie Office subskrypcji**

Przełączanie do subskrypcji, która obejmuje Office. Zobacz [Przełączanie się do innego Microsoft 365 dla firm](../../commerce/subscriptions/switch-to-a-different-plan.md).

**Opcja 2. Zakup indywidualny, indywidualny zakup Office zakup albo Office w ramach licencji licencjonowania**

 - Kup indywidualny, indywidualny zakup Office. Zobacz [Office Dla Użytkowników &amp; Domowych lub](https://www.microsoft.com/microsoft-365/buy/compare-all-microsoft-365-products-b) [Office Professional](https://www.microsoft.com/microsoft-365/p/office-professional-2019/CFQ7TTC0K7C5/)

     LUB

 - Kup wiele kopii Office w ramach licencji licencjonowania volume. Zobacz Porównanie [pakietów dostępnych w ramach licencjonowania zbiorowego](https://products.office.com/business/microsoft-office-volume-licensing-suites-comparison).

## <a name="step-3---uninstall-office"></a>Krok 3. Odinstalowywanie Office

Przed zainstalowaniem najnowszej wersji pakietu Office zalecamy odinstalowanie wszystkich starszych wersji pakietu Office. Jeśli jednak zmienisz zdanie na temat uaktualniania pakietu Office, zwróć uwagę na następujące przypadki, w których po odinstalowaniu nie będzie można ponownie zainstalować Office instalacji.
  
Zalecamy, jeśli masz dodatki innych firm, skontaktuj się z producentem, aby sprawdzić, czy jest dostępna aktualizacja, która będzie działać z najnowszą wersją pakietu Office.

> [!TIP]
> Jeśli podczas odinstalowywania pakietu Office się problemy, możesz skorzystać z narzędzia Microsoft Asystent odzyskiwania i pomocy technicznej, które pomoże Ci usunąć aplikację Office: Pobieranie i uruchamianie narzędzia [Microsoft Asystent odzyskiwania i pomocy technicznej](https://go.microsoft.com/fwlink/?LinkID=2155008).

### <a name="select-the-version-of-office-you-want-to-uninstall"></a>Wybierz wersję pakietu Office chcesz odinstalować

- [Z komputera](https://support.microsoft.com/office/9dd49b83-264a-477a-8fcc-2fdf5dbf61d8)

- [Z komputera Mac](https://support.microsoft.com/office/eefa1199-5b58-43af-8a3d-b73dc1a8cae3)
  
### <a name="known-issues-trying-to-reinstall-older-versions-of-office-after-an-uninstall"></a>Znane problemy podczas próby ponownej instalacji starszych wersji pakietu Office po odinstalowaniu

 **Office w ramach licencji licencjonowania volume Jeśli** nie masz już dostępu do plików źródłowych tych wersji programu Office z licencją Office, nie będzie można zainstalować go ponownie.

 **Office preinstalowany** na komputerze Jeśli nie masz już dysku lub klucza produktu (jeśli Office został zainstalowany), nie będzie można go ponownie zainstalować.

 **Nie obsługiwane subskrypcje** Jeśli Twoja kopia usługi Office została uzyskana w ramach wycofanych subskrypcji, takich jak Office 365 Small Business Premium lub Office 365 Mid-size Business, nie możesz zainstalować starszej wersji programu Office, jeśli nie masz klucza produktu otrzymanego w ramach subskrypcji.

Jeśli wolisz zainstalować starszą wersję programu Office obok najnowszej wersji, możesz zobaczyć listę wersji, w których jest to obsługiwane w: Instalowanie i używanie różnych wersji programu Office na tym samym [komputerze](https://support.microsoft.com/office/6ebb44ce-18a3-43f9-a187-b78c513788bf). Instalacja obok siebie może być dla Ciebie odpowiednim wyborem, jeśli na przykład zainstalowano dodatki innych firm, których używasz ze starszą wersją programu Office i nie masz jeszcze pewności, że są one zgodne z najnowszą wersją.

## <a name="step-4---assign-office-licenses-to-users"></a>Krok 4. Przypisywanie Office użytkowników

Jeśli jeszcze tego nie zrobiono, przypisz licencje do wszystkich użytkowników w organizacji, którzy muszą zainstalować usługę Office, zobacz Przypisywanie licencji użytkownikom w programie [Microsoft 365 dla firm](../manage/assign-licenses-to-users.md).
  
## <a name="step-5---install-office"></a>Krok 5. Instalowanie Office

Po zweryfikowaniu użytkowników, którzy chcą uaktualnić wszystkie licencje, ostatnim krokiem jest zainstalowanie pakietu Office — zobacz Pobieranie i instalowanie lub ponowne instalowanie programu [Office na komputerze PC lub Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658).
  
> [!TIP]
> Jeśli nie chcesz, aby użytkownicy samodzielnie Office, zobacz Zarządzanie ustawieniami pobierania oprogramowania w [Office 365](/DeployOffice/manage-software-download-settings-office-365). Za pomocą Narzędzia [wdrażania pakietu Office](/DeployOffice/overview-office-deployment-tool) możesz pobrać oprogramowanie pakietu Office do sieci lokalnej, Office następnie wdrożyć program Office, używając metody wdrażania oprogramowania, z których zwykle korzystasz.