---
title: Przypinanie aplikacji do ikony Uruchamianie aplikacji użytkowników
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.collection:
- Adm_O365
- M365-subscription-management
- Adm_TOC
ms.service: o365-administration
ms.custom: admindeeplinkMAC
ms.localizationpriority: medium
description: Jako administrator globalny możesz przypiąć do ikony Uruchamianie aplikacji użytkowników maksymalnie trzy aplikacje.
ms.openlocfilehash: 7ff85e379198312666f03c2d7d6c8bb42b9e08d0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985449"
---
# <a name="pin-apps-to-your-users-app-launcher"></a>Przypinanie aplikacji do ikony Uruchamianie aplikacji użytkowników

Za pomocą kontrolek w portalu Azure Active Directory możesz przypiąć maksymalnie trzy aplikacje do witryny Office.com oraz uruchamianie aplikacji dla wszystkich użytkowników w organizacji. Możesz także organizować grupy aplikacji. Dowolna aplikacja, która zostanie dodasz, może zostać później odpięta przez użytkownika w dowolnym momencie. Aby przypiąć aplikację dla użytkowników, musisz być administratorem aplikacji w chmurze, administratorem aplikacji w usłudze Azure Active Directory lub administratorem globalnym w Office 365. Aby uzyskać więcej informacji o rolach administratorów, zobacz [Wbudowane role i role](/azure/active-directory/roles/permissions-reference) administratorów w usłudze Azure AD [w usłudze Microsoft 365](../add-users/about-admin-roles.md). 

Aby uzyskać więcej informacji na temat ikony Uruchamianie aplikacji i Office.com, zobacz [](https://support.microsoft.com/office/79f12104-6fed-442f-96a0-eb089a3f476a) artykuł w blogu office.com i poświęcony Office 365 [uruchamianie aplikacji](https://techcommunity.microsoft.com/t5/office-365-blog/updates-to-office-com-and-the-office-365-app-launcher/ba-p/1150503).

## <a name="use-the-azure-active-directory-portal-to-pin-apps"></a>Przypinanie Azure Active Directory za pomocą portalu sieci Web

1. Przejdź do centrum administracyjne platformy Microsoft 365 stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.
2. W lewym obszarze narracji wybierz pozycję **Pokaż wszystko**, a następnie w obszarze **Centra** administracyjne **wybierz** pozycję Azure Active Directory.
3. W **Azure Active Directory** wybierz pozycję Enterprise **udostępnianie aplikacjiUżytkownia** > .
4. W sekcji **Office 365 Ustawienia** wybierz pozycję **Dodaj aplikację**.
5. Wybierz aplikacje, które chcesz przypiąć do ikony Uruchamianie aplikacji użytkowników, a następnie wybierz pozycję **Dodaj**.

:::image type="content" source="../../media/add-apps.png" alt-text="Microsoft 365, aby przypiąć aplikacje.":::

### <a name="pin-a-custom-app"></a>Przypinanie aplikacji niestandardowej

> [!NOTE]
> Interfejs użytkownika wskaże, czy musisz kupić dodatkowe licencje usługi Azure AD, aby korzystać z tej funkcji. Aby uzyskać więcej informacji, [Azure Active Directory ceny](https://azure.microsoft.com/pricing/details/active-directory/).

1. W **Azure Active Directory** aplikacji wybierz pozycję **Enterprise Najnowa** >  **aplikacja** w górnej części **strony Wszystkie** aplikacje.
2. Na stronie **Dodawanie aplikacji** wybierz pozycję Aplikacja niebędące  galerią lub Utwórz własną aplikację, jeśli jesteś w wersji Preview pakietu Azure Active Directory. 
3. Wpisz nazwę aplikacji, a następnie przypisz użytkownika na **karcie Użytkownicy i** grupy.
4. Użyj karty **Właściwości** , aby przekazać ikonę aplikacji.
5. Aby przypisać adres URL aplikacji, na karcie **Logowanie** pojedyncze wybierz pozycję Połączone, **a następnie wprowadź** adres URL.
6. Wybierz pozycję **Zapisz**.

## <a name="create-application-collections"></a>Tworzenie kolekcji aplikacji

Możesz również tworzyć kolekcje aplikacji dla użytkowników w organizacji. Aby uzyskać instrukcje, [zobacz Tworzenie kolekcji w portalu Moje aplikacje w portalu Azure Portal](/azure/active-directory/manage-apps/access-panel-collections).