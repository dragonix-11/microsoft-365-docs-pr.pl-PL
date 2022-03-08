---
title: Konfigurowanie łącznika do archiwizowania danych z konta Twitter
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
description: Dowiedz się, jak administratorzy mogą skonfigurować łącznik natywny i używać go do importowania danych serwisu Twitter do usługi Microsoft 365.
ms.openlocfilehash: 959cdd49d229334f3129eb21505c4489d23ded4f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320637"
---
# <a name="set-up-a-microsoft-connector-to-archive-twitter-data-preview"></a>Konfigurowanie łącznika firmy Microsoft do archiwizowania danych z usługi Twitter (wersja zapoznawcza)

Za pomocą łącznika w aplikacji Centrum zgodności platformy Microsoft 365 importować i archiwizować dane z konta w serwisie Twitter Microsoft 365. Po skonfigurowaniu i skonfigurowaniu łącznika połączy się on z kontem w serwisie Twitter Twojej organizacji (według harmonogramu), przekonwertuje zawartość elementu na format wiadomości e-mail, a następnie zaim importuje te elementy do skrzynki pocztowej w u Microsoft 365.

Po zaimportowaniu danych z serwisu Twitter możesz zastosować do danych serwisu Twitter funkcje zgodności usługi Microsoft 365, takie jak archiwizacja w związku z postępowaniem sądowym In-Place, przeszukiwanie zawartości, archiwizowanie, inspekcja i Microsoft 365. Na przykład w przypadku umieszczenia skrzynki pocztowej w związku z postępowaniem sądowym lub przypisania jej do zasad przechowywania dane w serwisie Twitter zostaną zachowane. Przy użyciu funkcji przeszukiwania zawartości można przeszukiwać dane osób trzecich lub skojarzyć skrzynkę pocztową, w której dane serwisu Twitter są przechowywane z pogotowiem w Advanced eDiscovery przypadku. Importowanie i archiwizowanie danych z usługi Twitter w programie Microsoft 365 za pomocą łącznika może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulacyjną.

Po zaimportowaniu danych z serwisu Twitter możesz zastosować funkcje zgodności usługi Microsoft 365, takie jak archiwizacja w związku z postępowaniem sądowym In-Place, wyszukiwanie zawartości, archiwizowanie, inspekcja, zgodność z komunikacją i zasady przechowywania Microsoft 365 do danych przechowywanych w skrzynce pocztowej. Można na przykład przeszukiwać dane serwisu Twitter przy użyciu funkcji przeszukiwania zawartości lub skojarzyć skrzynkę pocztową, w której dane są przechowywane ze współpracownikiem w Advanced eDiscovery przypadku. Importowanie i archiwizowanie danych z usługi Twitter w programie Microsoft 365 za pomocą łącznika może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulacyjną.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

Wykonaj poniższe wymagania wstępne, zanim będzie można skonfigurować łącznik w aplikacji Centrum zgodności platformy Microsoft 365 do importowania i archiwizowania danych z konta usługi Twitter Twojej organizacji.

- Potrzebujesz konta w serwisie Twitter w swojej organizacji; musisz zalogować się do tego konta podczas konfigurowania łącznika.

- Twoja organizacja musi mieć ważną subskrypcję platformy Azure. Jeśli nie masz jeszcze subskrypcji platformy Azure, możesz utworzyć konto w jednej z tych opcji:

    - [Zarejestruj się, aby uzyskać bezpłatną, jednoroczną subskrypcję platformy Azure](https://azure.microsoft.com/free) 

    - [Zarejestruj się w celu wykupinia subskrypcji usługi Azure w usłudze Pay-As-You-Go](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > [Bezpłatna Azure Active Directory](use-your-free-azure-ad-subscription-in-office-365.md), która jest zawarta w Twojej subskrypcji usługi Microsoft 365, nie obsługuje łączników w Centrum zgodności platformy Microsoft 365.

- Łącznik serwisu Twitter może zaimportować łącznie 200 000 elementów w jednym dniu. Jeśli dziennie istnieje więcej niż 200 000 elementów w serwisie Twitter, żaden z tych elementów nie zostanie zaimportowany do Microsoft 365.

- Użytkownik, który konfiguruje łącznik usługi Twitter w Centrum zgodności platformy Microsoft 365 (w kroku 5), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Krok 1. Tworzenie aplikacji w aplikacji Azure Active Directory

Pierwszym krokiem jest zarejestrowanie nowej aplikacji w aplikacji Azure Active Directory (AAD). Ta aplikacja odpowiada zasobowi aplikacji sieci Web zaimplementowanemu w kroku 2 łącznika usługi Twitter.

Aby uzyskać instrukcje krok po kroku, [zobacz Tworzenie aplikacji w aplikacji Azure Active Directory](deploy-twitter-connector.md#step-1-create-an-app-in-azure-active-directory).

Po wykonaniu tego kroku (zgodnie z instrukcjami krok po kroku) poniższe informacje zapiszesz w pliku tekstowym. Te wartości będą używane w dalszych krokach procesu wdrażania.

- AAD identyfikatora aplikacji

- AAD tajny aplikacji

- Identyfikator dzierżawy

## <a name="step-2-deploy-connector-web-service-from-github-repository-to-your-azure-account"></a>Krok 2. Wdrażanie usługi sieci Web łącznika GitHub do konta Azure

Następnym krokiem jest wdrożenie kodu źródłowego dla aplikacji łącznika usługi Twitter, która będzie używać interfejsu API serwisu Twitter do łączenia się z twoim kontem w serwisie Twitter i wyodrębniania danych, aby można było je zaimportować do usługi Microsoft 365. Łącznik usługi Twitter wdrożony w organizacji przekaże elementy z konta organizacji w serwisie Twitter do lokalizacji usługi Azure Storage, która została utworzona w tym kroku. Po utworzeniu łącznika serwisu Twitter w usłudze Centrum zgodności platformy Microsoft 365 (w kroku 5) usługa importowania usługi Microsoft 365 skopiuje dane serwisu Twitter z lokalizacji usługi Azure Storage do skrzynki pocztowej w usłudze Microsoft 365. Jak wyjaśniono wcześniej w [](#before-you-set-up-a-connector) sekcji Przed skonfigurowaniem łącznika, aby utworzyć konto azure dla usługi Azure Storage, musisz mieć ważną subskrypcję Storage Azure.

Aby wdrożyć kod źródłowy dla aplikacji Łącznik usługi Twitter:

1. Przejdź do [tej GitHub sieci Web](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet).

2. Kliknij pozycję **Wdeksuj na platformie Azure**.

Aby uzyskać instrukcje krok po kroku, zobacz Wdrażanie usługi sieci Web łącznika z GitHub [na koncie platformy Azure](deploy-twitter-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).

W celu wykonania tego kroku należy wykonać instrukcje krok po kroku, jednak należy podać następujące informacje.

- APISecretKey: Ten klucz tajny należy utworzyć podczas wykonania tego kroku. Jest on używany w kroku 5.

- tenantId: Identyfikator dzierżawy Microsoft 365, który został skopiowany po utworzeniu aplikacji Twitter w Azure Active Directory kroku 1.

Po wykonaniu tego kroku skopiuj adres URL usługi aplikacji (na przykład `https://twitterconnector.azurewebsites.net`). Musisz użyć tego adresu URL do wykonania kroków 3, 4 i 5).

## <a name="step-3-create-developer-app-on-twitter"></a>Krok 3. Tworzenie aplikacji deweloperskiej w serwisie Twitter

Następnym krokiem jest utworzenie i skonfigurowanie aplikacji deweloperskiej w serwisie Twitter. Łącznik niestandardowy, który tworzysz w kroku 7, używa aplikacji Twitter do interakcji z interfejsem API serwisu Twitter w celu uzyskiwania danych z konta organizacji w serwisie Twitter.

Aby uzyskać instrukcje krok po kroku, zobacz [Tworzenie aplikacji Twitter](deploy-twitter-connector.md#step-3-create-the-twitter-app).

Po wykonaniu tego kroku (zgodnie z instrukcjami krok po kroku) poniższe informacje są zapisywane w pliku tekstowym. Te wartości zostaną użyte do skonfigurowania aplikacji łącznika usługi Twitter w kroku 4.

- Klucz interfejsu API serwisu Twitter

- Klucz tajny interfejsu API serwisu Twitter

- Token dostępu do Twittera

- Token dostępu do Twittera Tajna

## <a name="step-4-configure-the-twitter-connector-app"></a>Krok 4. Konfigurowanie aplikacji łącznika usługi Twitter

Następnym krokiem jest dodanie ustawień konfiguracji do aplikacji łącznika usługi Twitter wdrożonej w kroku 2. Możesz to zrobić, przechodząc do strony głównej aplikacji łącznika i konfigurując ją.

Aby uzyskać instrukcje krok po kroku, zobacz [Konfigurowanie aplikacji sieci Web łącznika](deploy-twitter-connector.md#step-4-configure-the-connector-web-app).

Po wykonaniu tego kroku (wykonując instrukcje krok po kroku) zostaną podane następujące informacje (skopiowane do pliku tekstowego po wykonaniu poprzednich kroków):

- Klucz interfejsu API usługi Twitter (uzyskany w kroku 3)

- Klucz tajny interfejsu API serwisu Twitter (uzyskany w kroku 3)

- Token dostępu do usługi Twitter (uzyskany w kroku 3)

- Token dostępu do usługi Twitter Secret (uzyskany w kroku 3)

- Azure Active Directory aplikacji (identyfikator AAD aplikacji uzyskany w kroku 1)

- Azure Active Directory tajny aplikacji (AAD tajna aplikacji uzyskana w kroku 1)

## <a name="step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center"></a>Krok 5. Konfigurowanie łącznika konta Twitter w Centrum zgodności platformy Microsoft 365

Ostatnim krokiem jest skonfigurowanie łącznika usługi Twitter w Centrum zgodności platformy Microsoft 365, który zaimportuje dane z konta w serwisie Twitter Twojej organizacji do określonej skrzynki pocztowej w Microsoft 365. Po zakończeniu tego kroku usługa importowania Microsoft 365 rozpocznie importowanie danych z konta Twitter Twojej organizacji do usługi Microsoft 365.

Aby uzyskać instrukcje krok po kroku, zobacz Konfigurowanie łącznika konta [Twitter w Centrum zgodności platformy Microsoft 365](deploy-twitter-connector.md#step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center). 

Po wykonaniu tego kroku (wykonując instrukcje krok po kroku) zostaną podane następujące informacje (skopiowane do pliku tekstowego po wykonaniu tych czynności).

- Adres URL usługi aplikacji Azure (uzyskany w kroku 2, na przykład `https://twitterconnector.azurewebsites.net`)

- APISecretKey (utworzony w kroku 2)