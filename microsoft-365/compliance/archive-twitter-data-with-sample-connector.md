---
title: Konfigurowanie łącznika do archiwizowania danych usługi Twitter
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 04/08/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Dowiedz się, jak administratorzy mogą skonfigurować łącznik natywny i używać go do importowania danych usługi Twitter do Microsoft 365.
ms.openlocfilehash: ba151d1ffae18a5df033fbb8696fcd3bf759f285
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094553"
---
# <a name="set-up-a-microsoft-connector-to-archive-twitter-data-preview"></a>Konfigurowanie łącznika firmy Microsoft do archiwizowania danych usługi Twitter (wersja zapoznawcza)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj łącznika w portalu zgodności usługi Microsoft Purview, aby zaimportować i zarchiwizować dane z usługi Twitter do Microsoft 365. Po skonfigurowaniu i skonfigurowaniu łącznika nawiązuje on połączenie z kontem twitterowym organizacji (zgodnie z harmonogramem), konwertuje zawartość elementu na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej w Microsoft 365.

Po zaimportowaniu danych usługi Twitter do danych usługi Twitter można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, wyszukiwanie zawartości, archiwizowanie In-Place, inspekcja i zasady przechowywania Microsoft 365. Na przykład po umieszczeniu skrzynki pocztowej w blokadzie postępowania sądowego lub przypisaniu do zasad przechowywania dane usługi Twitter są zachowywane. Dane innych firm można przeszukiwać przy użyciu wyszukiwania zawartości lub kojarzyć skrzynkę pocztową, w której dane usługi Twitter są przechowywane z opiekunem w przypadku zbierania elektronicznych materiałów dowodowych (Premium) w usłudze Microsoft Purview. Użycie łącznika do importowania i archiwizowania danych usługi Twitter w Microsoft 365 może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

Po zaimportowaniu danych usługi Twitter można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, wyszukiwanie zawartości, archiwizowanie In-Place, inspekcja, zgodność z komunikacją i zasady przechowywania Microsoft 365 do danych przechowywanych w skrzynce pocztowej. Możesz na przykład przeszukać dane usługi Twitter przy użyciu funkcji wyszukiwania zawartości lub skojarzyć skrzynkę pocztową, w której dane są przechowywane u opiekuna w przypadku zbierania elektronicznych materiałów dowodowych (Premium). Użycie łącznika do importowania i archiwizowania danych usługi Twitter w Microsoft 365 może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

Przed skonfigurowaniem i skonfigurowaniem łącznika w portalu zgodności w celu zaimportowania i zarchiwizowania danych z konta twitterowego organizacji wykonaj następujące wymagania wstępne.

- Potrzebujesz konta w serwisie Twitter dla swojej organizacji; musisz zalogować się do tego konta podczas konfigurowania łącznika.

- Twoja organizacja musi mieć prawidłową subskrypcję platformy Azure. Jeśli nie masz istniejącej subskrypcji platformy Azure, możesz utworzyć konto, aby skorzystać z jednej z następujących opcji:

    - [Utwórz konto, aby uzyskać bezpłatną roczną subskrypcję platformy Azure](https://azure.microsoft.com/free) 

    - [Tworzenie konta w celu subskrypcji platformy Azure z płatnością zgodnie z rzeczywistym użyciem](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > [Bezpłatna subskrypcja Azure Active Directory](use-your-free-azure-ad-subscription-in-office-365.md) dołączona do subskrypcji Microsoft 365 nie obsługuje łączników w portalu zgodności.

- Łącznik twitterowy może zaimportować łącznie 200 000 elementów w ciągu jednego dnia. Jeśli w ciągu dnia będzie więcej niż 200 000 elementów serwisu Twitter, żaden z tych elementów nie zostanie zaimportowany do Microsoft 365.

- Użytkownik, który konfiguruje łącznik usługi Twitter w portalu zgodności (w kroku 5), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Krok 1. Tworzenie aplikacji w Azure Active Directory

Pierwszym krokiem jest zarejestrowanie nowej aplikacji w Azure Active Directory (AAD). Ta aplikacja odpowiada zasobowi aplikacji internetowej zaimplementowanemu w kroku 2 dla łącznika usługi Twitter.

Aby uzyskać instrukcje krok po kroku, zobacz [Tworzenie aplikacji w Azure Active Directory](deploy-twitter-connector.md#step-1-create-an-app-in-azure-active-directory).

Podczas wykonywania tego kroku (postępjąc zgodnie z instrukcjami krok po kroku) zapiszesz następujące informacje w pliku tekstowym. Te wartości będą używane w kolejnych krokach procesu wdrażania.

- identyfikator aplikacji AAD

- AAD wpis tajny aplikacji

- Identyfikator dzierżawy

## <a name="step-2-deploy-connector-web-service-from-github-repository-to-your-azure-account"></a>Krok 2. Wdrażanie usługi internetowej łącznika z repozytorium GitHub na koncie platformy Azure

Następnym krokiem jest wdrożenie kodu źródłowego dla aplikacji łącznika Twitter, która będzie używać interfejsu API usługi Twitter do łączenia się z kontem usługi Twitter i wyodrębniania danych, aby można było je zaimportować do Microsoft 365. Łącznik usługi Twitter wdrażany dla organizacji przekaże elementy z konta twitterowego organizacji do lokalizacji usługi Azure Storage utworzonej w tym kroku. Po utworzeniu łącznika usługi Twitter w portalu zgodności (w kroku 5) usługa Microsoft 365 Import skopiuje dane usługi Twitter z lokalizacji usługi Azure Storage do skrzynki pocztowej w Microsoft 365. Jak wyjaśniono wcześniej w sekcji [Przed skonfigurowaniem łącznika](#before-you-set-up-a-connector), musisz mieć prawidłową subskrypcję platformy Azure, aby utworzyć konto usługi Azure Storage.

Aby wdrożyć kod źródłowy aplikacji łącznika usługi Twitter:

1. Przejdź do [tej witryny GitHub](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet).

2. Kliknij **pozycję Wdróż na platformie Azure**.

Aby uzyskać instrukcje krok po kroku, zobacz [Deploy the connector web service from GitHub to your Azure account (Wdrażanie usługi internetowej łącznika z GitHub na koncie platformy Azure](deploy-twitter-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account)).

Postępjąc zgodnie z instrukcjami krok po kroku, aby wykonać ten krok, podaj następujące informacje

- APISecretKey: ten wpis tajny jest utworzony podczas wykonywania tego kroku. Jest on używany w kroku 5.

- tenantId: identyfikator dzierżawy organizacji Microsoft 365 skopiowany po utworzeniu aplikacji Twitter w Azure Active Directory w kroku 1.

Po wykonaniu tego kroku skopiuj adres URL usługi app Service (na przykład `https://twitterconnector.azurewebsites.net`). Ten adres URL należy użyć do wykonania kroków 3, 4 i 5.

## <a name="step-3-create-developer-app-on-twitter"></a>Krok 3. Tworzenie aplikacji dewelopera w serwisie Twitter

Następnym krokiem jest utworzenie i skonfigurowanie aplikacji dewelopera w serwisie Twitter. Łącznik niestandardowy utworzony w kroku 7 używa aplikacji Twitter do interakcji z interfejsem API usługi Twitter w celu uzyskania danych z konta twitterowego organizacji.

Aby uzyskać instrukcje krok po kroku, zobacz [Tworzenie aplikacji Twitter](deploy-twitter-connector.md#step-3-create-the-twitter-app).

Podczas wykonywania tego kroku (postępjąc zgodnie z instrukcjami krok po kroku) zapisz następujące informacje w pliku tekstowym. Te wartości zostaną użyte do skonfigurowania aplikacji łącznika usługi Twitter w kroku 4.

- Klucz interfejsu API usługi Twitter

- Klucz tajny interfejsu API usługi Twitter

- Token dostępu do usługi Twitter

- Wpis tajny tokenu dostępu usługi Twitter

## <a name="step-4-configure-the-twitter-connector-app"></a>Krok 4. Konfigurowanie aplikacji łącznika usługi Twitter

Następnym krokiem jest dodanie ustawień konfiguracji do aplikacji łącznika usługi Twitter wdrożonej w kroku 2. Można to zrobić, przechodząc do strony głównej aplikacji łącznika i konfigurując ją.

Aby uzyskać instrukcje krok po kroku, zobacz [Konfigurowanie aplikacji internetowej łącznika](deploy-twitter-connector.md#step-4-configure-the-connector-web-app).

Podczas wykonywania tego kroku (postępując zgodnie z instrukcjami krok po kroku) podasz następujące informacje (skopiowane do pliku tekstowego po wykonaniu poprzednich kroków):

- Klucz interfejsu API usługi Twitter (uzyskany w kroku 3)

- Klucz tajny interfejsu API usługi Twitter (uzyskany w kroku 3)

- Token dostępu do usługi Twitter (uzyskany w kroku 3)

- Wpis tajny tokenu dostępu usługi Twitter (uzyskany w kroku 3)

- Azure Active Directory identyfikator aplikacji (identyfikator aplikacji AAD uzyskany w kroku 1)

- Azure Active Directory wpis tajny aplikacji (wpis tajny aplikacji AAD uzyskany w kroku 1)

## <a name="step-5-set-up-a-twitter-connector-in-the-compliance-portal"></a>Krok 5. Konfigurowanie łącznika usługi Twitter w portalu zgodności

Ostatnim krokiem jest skonfigurowanie łącznika usługi Twitter w portalu zgodności, który zaimportuje dane z konta twitterowego organizacji do określonej skrzynki pocztowej w Microsoft 365. Po wykonaniu tego kroku usługa Microsoft 365 Import rozpocznie importowanie danych z konta twitterowego organizacji do Microsoft 365.

Aby uzyskać instrukcje krok po kroku, zobacz [Konfigurowanie łącznika usługi Twitter w portalu zgodności usługi Microsoft Purview](deploy-twitter-connector.md#step-5-set-up-a-twitter-connector-in-the-compliance-portal).

Podczas wykonywania tego kroku (postępując zgodnie z instrukcjami krok po kroku) podasz następujące informacje (skopiowane do pliku tekstowego po wykonaniu kroków).

- Adres URL usługi Azure App Service (uzyskany w kroku 2, na przykład `https://twitterconnector.azurewebsites.net`)

- APISecretKey (utworzony w kroku 2)