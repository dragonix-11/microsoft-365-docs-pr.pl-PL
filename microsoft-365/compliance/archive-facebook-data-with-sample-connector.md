---
title: Konfigurowanie łącznika do archiwizowania danych serwisu Facebook
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Dowiedz się, jak skonfigurować & za pomocą łącznika w portalu zgodności usługi Microsoft Purview w celu zaimportowania & danych archiwum ze stron biznesowych serwisu Facebook do Microsoft 365.
ms.openlocfilehash: 58d1f0efd26d892a4bf206c71dc5ee55c653abfb
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64994947"
---
# <a name="set-up-a-connector-to-archive-facebook-data-preview"></a>Konfigurowanie łącznika do archiwizowania danych serwisu Facebook (wersja zapoznawcza)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj łącznika w portalu zgodności usługi Microsoft Purview, aby zaimportować i zarchiwizować dane ze stron firmy w serwisie Facebook, aby Microsoft 365. Po skonfigurowaniu i skonfigurowaniu łącznika nawiązuje on połączenie ze stroną Facebook Business (zgodnie z harmonogramem), konwertuje zawartość elementów serwisu Facebook na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej w Microsoft 365.

Po zaimportowaniu danych serwisu Facebook do danych serwisu Facebook można zastosować takie funkcje usługi Microsoft Purview, jak blokada postępowania sądowego, wyszukiwanie zawartości, archiwizowanie In-Place, inspekcja, zgodność z komunikacją i zasady przechowywania Microsoft 365. Na przykład po umieszczeniu skrzynki pocztowej w blokadzie postępowania sądowego lub przypisaniu do zasad przechowywania dane serwisu Facebook są zachowywane. Dane innych firm można przeszukiwać przy użyciu wyszukiwania zawartości lub kojarzyć skrzynkę pocztową, w której dane serwisu Facebook są przechowywane z opiekunem w przypadku zbierania elektronicznych materiałów dowodowych (Premium) w usłudze Microsoft Purview. Użycie łącznika do importowania i archiwizowania danych serwisu Facebook w Microsoft 365 może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="prerequisites-for-setting-up-a-connector-for-facebook-business-pages"></a>Wymagania wstępne dotyczące konfigurowania łącznika dla stron biznesowych w serwisie Facebook

Przed skonfigurowaniem i skonfigurowaniem łącznika w portalu zgodności wykonaj następujące wymagania wstępne, aby zaimportować i zarchiwizować dane ze stron biznesowych facebookowych organizacji. 

- Potrzebne jest konto na Facebooku dla stron biznesowych organizacji (musisz zalogować się do tego konta podczas konfigurowania łącznika). Obecnie można archiwizować tylko dane ze stron biznesowych serwisu Facebook; Nie można archiwizować danych z poszczególnych profilów na Facebooku.

- Twoja organizacja musi mieć prawidłową subskrypcję platformy Azure. Jeśli nie masz istniejącej subskrypcji platformy Azure, możesz utworzyć konto, aby skorzystać z jednej z następujących opcji:

    - [Utwórz konto, aby uzyskać bezpłatną roczną subskrypcję platformy Azure](https://azure.microsoft.com/free)

    - [Tworzenie konta w celu subskrypcji platformy Azure z płatnością zgodnie z rzeczywistym użyciem](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > [Bezpłatna subskrypcja Azure Active Directory](use-your-free-azure-ad-subscription-in-office-365.md) dołączona do subskrypcji Microsoft 365 nie obsługuje łączników w portalu zgodności.

- Łącznik dla stron biznesowych serwisu Facebook może zaimportować łącznie 200 000 elementów w ciągu jednego dnia. Jeśli w ciągu dnia istnieje ponad 200 000 elementów biznesowych Facebooka, żaden z tych elementów nie zostanie zaimportowany do Microsoft 365.

- Użytkownik, który konfiguruje łącznik niestandardowy w portalu zgodności (w kroku 5), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Krok 1. Tworzenie aplikacji w Azure Active Directory

Pierwszym krokiem jest zarejestrowanie nowej aplikacji w Azure Active Directory (AAD). Ta aplikacja odpowiada zasobowi aplikacji internetowej zaimplementowanemu w kroku 4 i kroku 5 dla łącznika usługi Facebook.

Aby uzyskać instrukcje krok po kroku, zobacz [Tworzenie aplikacji w Azure Active Directory](deploy-facebook-connector.md#step-1-create-an-app-in-azure-active-directory).

Podczas wykonywania tego kroku (przy użyciu poprzednich instrukcji krok po kroku) zapiszesz następujące informacje w pliku tekstowym. Te wartości są używane w kolejnych krokach procesu wdrażania.

- identyfikator aplikacji AAD

- AAD wpis tajny aplikacji

- Identyfikator dzierżawy

## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>Krok 2. Wdrażanie usługi internetowej łącznika z GitHub na koncie platformy Azure

Następnym krokiem jest wdrożenie kodu źródłowego aplikacji łącznika stron biznesowych Facebooka, która będzie używać interfejsu API facebooka do łączenia się z kontem w Serwisie Facebook i wyodrębniania danych, aby można było je zaimportować do Microsoft 365. Łącznik usługi Facebook wdrażany dla organizacji przekaże elementy ze stron biznesowych usługi Facebook do lokalizacji Storage platformy Azure utworzonej w tym kroku. Po utworzeniu łącznika stron biznesowych serwisu Facebook w portalu zgodności (w kroku 5) usługa Import skopiuje dane stron biznesowych serwisu Facebook z lokalizacji Storage platformy Azure do skrzynki pocztowej w organizacji Microsoft 365. Jak wyjaśniono wcześniej w sekcji [Wymagania](#prerequisites-for-setting-up-a-connector-for-facebook-business-pages) wstępne, musisz mieć prawidłową subskrypcję platformy Azure, aby utworzyć konto usługi Azure Storage.

Aby uzyskać instrukcje krok po kroku, zobacz [Deploy the connector web service from GitHub to your Azure account (Wdrażanie usługi internetowej łącznika z GitHub na koncie platformy Azure](deploy-facebook-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account)).

W instrukcjach krok po kroku, aby wykonać ten krok, podasz następujące informacje:

- APISecretKey: ten wpis tajny jest utworzony podczas wykonywania tego kroku. Jest on używany w kroku 5.

- TenantId: identyfikator dzierżawy organizacji Microsoft 365 skopiowany po utworzeniu aplikacji łącznika Facebook w Azure Active Directory w kroku 1.

Po wykonaniu tego kroku skopiuj adres URL usługi Azure App Service (na przykład https://fbconnector.azurewebsites.net). Ten adres URL należy użyć do wykonania kroków 3, 4 i 5.

## <a name="step-3-register-the-web-app-on-facebook"></a>Krok 3. Rejestrowanie aplikacji internetowej na Facebooku

Następnym krokiem jest utworzenie i skonfigurowanie nowej aplikacji w serwisie Facebook. Łącznik stron biznesowych facebooka utworzony w kroku 5 używa aplikacji internetowej Facebook do interakcji z interfejsem API facebooka w celu uzyskania danych ze stron biznesowych facebookowych organizacji.

Aby uzyskać instrukcje krok po kroku, zobacz [Rejestrowanie aplikacji Facebook](deploy-facebook-connector.md#step-3-register-the-facebook-app).

Podczas wykonywania tego kroku (postępjąc zgodnie z instrukcjami krok po kroku) zapisz następujące informacje w pliku tekstowym. Te wartości służą do konfigurowania aplikacji łącznika Facebooka w kroku 4.

- Identyfikator aplikacji Facebook

- Wpis tajny aplikacji Facebook

- Elementy webhook serwisu Facebook weryfikują token

## <a name="step-4-configure-the-facebook-connector-app"></a>Krok 4. Konfigurowanie aplikacji łącznika Facebooka

Następnym krokiem jest dodanie ustawień konfiguracji do aplikacji łącznika Facebook przekazanej podczas tworzenia zasobu aplikacji internetowej platformy Azure w kroku 1. Można to zrobić, przechodząc do strony głównej aplikacji łącznika i konfigurując ją.

Aby uzyskać instrukcje krok po kroku, zobacz [Konfigurowanie aplikacji łącznika Facebooka](archive-facebook-data-with-sample-connector.md#step-4-configure-the-facebook-connector-app).

Podczas wykonywania tego kroku (postępując zgodnie z instrukcjami krok po kroku) należy podać następujące informacje (skopiowane do pliku tekstowego po wykonaniu poprzednich kroków):

- Identyfikator aplikacji Facebook (uzyskany w kroku 3)

- Wpis tajny aplikacji Facebooka (uzyskany w kroku 3)

- Elementy webhook na Facebooku weryfikują token (uzyskany w kroku 3)

- Azure Active Directory identyfikator aplikacji (identyfikator aplikacji AAD uzyskany w kroku 1)

- Azure Active Directory wpis tajny aplikacji (wpis tajny aplikacji AAD uzyskany w kroku 1)

## <a name="step-5-set-up-a-facebook-business-pages-connector-in-the-compliance-portal"></a>Krok 5. Konfigurowanie łącznika stron biznesowych serwisu Facebook w portalu zgodności

Ostatnim krokiem jest skonfigurowanie łącznika w portalu zgodności, który zaimportuje dane ze stron biznesowych serwisu Facebook do określonej skrzynki pocztowej w Microsoft 365. Po wykonaniu tego kroku usługa Microsoft 365 Import rozpocznie importowanie danych ze stron biznesowych serwisu Facebook do Microsoft 365.

Aby uzyskać instrukcje krok po kroku, zobacz [Krok 5: Konfigurowanie łącznika usługi Facebook w portalu zgodności](deploy-facebook-connector.md#step-5-set-up-a-facebook-connector-in-the-compliance-portal).

Podczas wykonywania tego kroku (postępując zgodnie z instrukcjami krok po kroku) należy podać następujące informacje (skopiowane do pliku tekstowego po wykonaniu kroków).

- AAD identyfikator aplikacji (uzyskany w kroku 1)

- Adres URL usługi Azure App Service (uzyskany w kroku 1; na przykład https://fbconnector.azurewebsites.net)

- APISecretKey (utworzony w kroku 2)
