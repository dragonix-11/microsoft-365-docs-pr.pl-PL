---
title: Konfigurowanie łącznika do archiwizowania danych serwisu Facebook
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Dowiedz się, jak skonfigurować & za pomocą łącznika w portal zgodności Microsoft Purview importować & dane archiwum ze stron biznesowych serwisu Facebook na platformę Microsoft 365.
ms.openlocfilehash: d8b951e7f0b9733dacca7cfd16eed1042d84c460
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623358"
---
# <a name="set-up-a-connector-to-archive-facebook-data-preview"></a>Konfigurowanie łącznika do archiwizowania danych serwisu Facebook (wersja zapoznawcza)

Użyj łącznika w portal zgodności Microsoft Purview, aby zaimportować i zarchiwizować dane ze stron biznesowych serwisu Facebook na platformę Microsoft 365. Po skonfigurowaniu i skonfigurowaniu łącznika nawiązuje on połączenie ze stroną Facebook Business (zgodnie z harmonogramem), konwertuje zawartość elementów serwisu Facebook na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej na platformie Microsoft 365.

Po zaimportowaniu danych serwisu Facebook do danych serwisu Facebook można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, wyszukiwanie zawartości, archiwizowanie In-Place, inspekcja, zgodność z komunikacją i zasady przechowywania usługi Microsoft 365. Na przykład po umieszczeniu skrzynki pocztowej w blokadzie postępowania sądowego lub przypisaniu do zasad przechowywania dane serwisu Facebook są zachowywane. Dane innych firm można przeszukiwać przy użyciu wyszukiwania zawartości lub kojarzyć skrzynkę pocztową, w której dane serwisu Facebook są przechowywane u opiekuna w przypadku Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Premium). Importowanie i archiwizowanie danych serwisu Facebook na platformie Microsoft 365 przy użyciu łącznika może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="prerequisites-for-setting-up-a-connector-for-facebook-business-pages"></a>Wymagania wstępne dotyczące konfigurowania łącznika dla stron biznesowych w serwisie Facebook

Przed skonfigurowaniem i skonfigurowaniem łącznika w portalu zgodności wykonaj następujące wymagania wstępne, aby zaimportować i zarchiwizować dane ze stron biznesowych facebookowych organizacji. 

- Potrzebne jest konto na Facebooku dla stron biznesowych organizacji (musisz zalogować się do tego konta podczas konfigurowania łącznika). Obecnie można archiwizować tylko dane ze stron biznesowych serwisu Facebook; Nie można archiwizować danych z poszczególnych profilów na Facebooku.

- Twoja organizacja musi mieć prawidłową subskrypcję platformy Azure. Jeśli nie masz istniejącej subskrypcji platformy Azure, możesz utworzyć konto, aby skorzystać z jednej z następujących opcji:

    - [Utwórz konto, aby uzyskać bezpłatną roczną subskrypcję platformy Azure](https://azure.microsoft.com/free)

    - [Tworzenie konta w celu subskrypcji platformy Azure z płatnością zgodnie z rzeczywistym użyciem](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > [Bezpłatna subskrypcja usługi Azure Active Directory](use-your-free-azure-ad-subscription-in-office-365.md) dołączona do subskrypcji platformy Microsoft 365 nie obsługuje łączników w portalu zgodności.

- Łącznik dla stron biznesowych serwisu Facebook może zaimportować łącznie 200 000 elementów w ciągu jednego dnia. Jeśli w ciągu dnia będzie więcej niż 200 000 elementów biznesowych facebooka, żaden z tych elementów nie zostanie zaimportowany na platformę Microsoft 365.

- Użytkownik, który konfiguruje łącznik niestandardowy w portalu zgodności (w kroku 5), musi mieć przypisaną rolę Administracja łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę Administracja łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Krok 1. Tworzenie aplikacji w usłudze Azure Active Directory

Pierwszym krokiem jest zarejestrowanie nowej aplikacji w usłudze Azure Active Directory (AAD). Ta aplikacja odpowiada zasobowi aplikacji internetowej zaimplementowanemu w kroku 4 i kroku 5 dla łącznika usługi Facebook.

Aby uzyskać instrukcje krok po kroku, zobacz [Tworzenie aplikacji w usłudze Azure Active Directory](deploy-facebook-connector.md#step-1-create-an-app-in-azure-active-directory).

Podczas wykonywania tego kroku (przy użyciu poprzednich instrukcji krok po kroku) zapiszesz następujące informacje w pliku tekstowym. Te wartości są używane w kolejnych krokach procesu wdrażania.

- Identyfikator aplikacji usługi AAD

- Wpis tajny aplikacji usługi AAD

- Identyfikator dzierżawy

## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>Krok 2. Wdrażanie usługi internetowej łącznika z usługi GitHub na koncie platformy Azure

Następnym krokiem jest wdrożenie kodu źródłowego aplikacji łącznika stron biznesowych Facebooka, która będzie używać interfejsu API serwisu Facebook do łączenia się z kontem w serwisie Facebook i wyodrębniania danych, aby można było je zaimportować na platformę Microsoft 365. Łącznik usługi Facebook wdrażany dla organizacji przekaże elementy ze stron biznesowych serwisu Facebook do lokalizacji usługi Azure Storage utworzonej w tym kroku. Po utworzeniu łącznika stron biznesowych serwisu Facebook w portalu zgodności (w kroku 5) usługa Import skopiuje dane stron biznesowych serwisu Facebook z lokalizacji usługi Azure Storage do skrzynki pocztowej w organizacji platformy Microsoft 365. Jak wyjaśniono wcześniej w sekcji [Wymagania wstępne](#prerequisites-for-setting-up-a-connector-for-facebook-business-pages) , musisz mieć prawidłową subskrypcję platformy Azure, aby utworzyć konto usługi Azure Storage.

Aby uzyskać instrukcje krok po kroku, zobacz [Deploy the connector web service from GitHub to your Azure account (Wdrażanie usługi internetowej łącznika z usługi GitHub na koncie platformy Azure](deploy-facebook-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account)).

W instrukcjach krok po kroku, aby wykonać ten krok, podasz następujące informacje:

- APISecretKey: ten wpis tajny jest utworzony podczas wykonywania tego kroku. Jest on używany w kroku 5.

- TenantId: identyfikator dzierżawy organizacji platformy Microsoft 365 skopiowany po utworzeniu aplikacji łącznika Facebook w usłudze Azure Active Directory w kroku 1.

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

- Identyfikator aplikacji usługi Azure Active Directory (identyfikator aplikacji usługi AAD uzyskany w kroku 1)

- Wpis tajny aplikacji usługi Azure Active Directory (wpis tajny aplikacji usługi AAD uzyskany w kroku 1)

## <a name="step-5-set-up-a-facebook-business-pages-connector-in-the-compliance-portal"></a>Krok 5. Konfigurowanie łącznika stron biznesowych serwisu Facebook w portalu zgodności

Ostatnim krokiem jest skonfigurowanie łącznika w portalu zgodności, który zaimportuje dane ze stron biznesowych usługi Facebook do określonej skrzynki pocztowej na platformie Microsoft 365. Po wykonaniu tego kroku usługa Import platformy Microsoft 365 rozpocznie importowanie danych ze stron biznesowych serwisu Facebook na platformę Microsoft 365.

Aby uzyskać instrukcje krok po kroku, zobacz [Krok 5: Konfigurowanie łącznika usługi Facebook w portalu zgodności](deploy-facebook-connector.md#step-5-set-up-a-facebook-connector-in-the-compliance-portal).

Podczas wykonywania tego kroku (postępując zgodnie z instrukcjami krok po kroku) należy podać następujące informacje (skopiowane do pliku tekstowego po wykonaniu kroków).

- Identyfikator aplikacji usługi AAD (uzyskany w kroku 1)

- Adres URL usługi Azure App Service (uzyskany w kroku 1; na przykład https://fbconnector.azurewebsites.net)

- APISecretKey (utworzony w kroku 2)
