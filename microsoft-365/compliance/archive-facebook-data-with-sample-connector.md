---
title: Konfigurowanie łącznika do archiwizowania danych z serwisu Facebook
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
description: Dowiedz się, jak skonfigurować & łącznika w aplikacji Centrum zgodności platformy Microsoft 365 w celu & zarchiwizować dane ze stron biznesowych w serwisie Facebook w celu Microsoft 365.
ms.openlocfilehash: b78a2ae168c896d525ad57bc986105e891f7dde9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988055"
---
# <a name="set-up-a-connector-to-archive-facebook-data-preview"></a>Konfigurowanie łącznika do archiwizowania danych serwisu Facebook (wersja zapoznawcza)

Za pomocą łącznika w Centrum zgodności platformy Microsoft 365 można importować i archiwizować dane ze stron biznesowych serwisu Facebook w celu Microsoft 365. Po skonfigurowaniu i skonfigurowaniu łącznika zostanie on połączony ze stroną biznesową w serwisie Facebook (według harmonogramu), konwertuje zawartość elementów serwisu Facebook na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej w programie Microsoft 365.

Po zaimportowaniu danych z serwisu Facebook możesz zastosować funkcje zgodności usługi Microsoft 365, takie jak archiwizacja w związku z postępowaniem sądowym In-Place, wyszukiwanie zawartości, archiwizowanie, inspekcja, zgodność z komunikacją i zasady przechowywania Microsoft 365 do danych serwisu Facebook. Na przykład w przypadku umieszczenia skrzynki pocztowej w związku z postępowaniem sądowym lub przypisania jej do zasad przechowywania dane z serwisu Facebook zostaną zachowane. Przy użyciu funkcji przeszukiwania zawartości można przeszukiwać dane innych firm lub skojarzyć skrzynkę pocztową, w której dane z serwisu Facebook są przechowywane ze współpracownikiem w Advanced eDiscovery przypadku. Importowanie i archiwizowanie danych serwisu Facebook w programie Microsoft 365 za pomocą łącznika może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulacyjną.

## <a name="prerequisites-for-setting-up-a-connector-for-facebook-business-pages"></a>Wymagania wstępne dotyczące konfigurowania łącznika dla stron biznesowych w serwisie Facebook

Wykonaj poniższe wymagania wstępne, zanim będzie można skonfigurować łącznik w Centrum zgodności platformy Microsoft 365 do importowania i archiwizowania danych ze stron biznesowych organizacji w serwisie Facebook. 

- Do korzystania ze stron biznesowych organizacji jest potrzebne konto serwisu Facebook (podczas konfigurowania łącznika należy zalogować się na tym koncie). Obecnie zarchiwizować można tylko dane ze stron firmowych serwisu Facebook. nie można archiwizować danych z poszczególnych profilów w serwisie Facebook.

- Twoja organizacja musi mieć ważną subskrypcję platformy Azure. Jeśli nie masz jeszcze subskrypcji platformy Azure, możesz utworzyć konto w jednej z tych opcji:

    - [Zarejestruj się, aby uzyskać bezpłatną, jednoroczną subskrypcję platformy Azure](https://azure.microsoft.com/free)

    - [Zarejestruj się w celu wykupinia subskrypcji usługi Azure w usłudze Pay-As-You-Go](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > [Bezpłatna Azure Active Directory](use-your-free-azure-ad-subscription-in-office-365.md), która jest zawarta w Twojej subskrypcji usługi Microsoft 365, nie obsługuje łączników w Centrum zgodności platformy Microsoft 365.

- Łącznik dla stron biznesowych serwisu Facebook może zaimportować łącznie 200 000 elementów w jednym dniu. Jeśli dziennie istnieje więcej niż 200 000 elementów biznesowych serwisu Facebook, żaden z tych elementów nie zostanie zaimportowany do Microsoft 365.

- Użytkownik, który konfiguruje łącznik niestandardowy w Centrum zgodności platformy Microsoft 365 (w kroku 5), musi mieć przypisaną rolę importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Krok 1. Tworzenie aplikacji w aplikacji Azure Active Directory

Pierwszym krokiem jest zarejestrowanie nowej aplikacji w aplikacji Azure Active Directory (AAD). Ta aplikacja odpowiada zasobowi aplikacji sieci Web zaimplementowanemu w krokach 4 i 5 łącznika serwisu Facebook. 

Aby uzyskać instrukcje krok po kroku, [zobacz Tworzenie aplikacji w aplikacji Azure Active Directory](deploy-facebook-connector.md#step-1-create-an-app-in-azure-active-directory).

Podczas wykonania tego kroku (korzystając z poprzednich instrukcji krok po kroku), zapisujesz poniższe informacje w pliku tekstowym. Te wartości są używane w dalszych krokach procesu wdrażania.

- AAD identyfikatora aplikacji

- AAD tajny aplikacji

- Identyfikator dzierżawy

## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>Krok 2. Wdrażanie usługi sieci Web łącznika z programu GitHub do konta Azure

Następnym krokiem jest wdrożenie kodu źródłowego dla aplikacji łącznika stron biznesowych serwisu Facebook, która będzie używać interfejsu API serwisu Facebook do łączenia się z kontem w serwisie Facebook i wyodrębniania danych, aby można było je zaimportować do usługi Microsoft 365. Łącznik serwisu Facebook wdrożony w organizacji przekaże elementy ze stron biznesowych serwisu Facebook do lokalizacji usługi Azure Storage utworzonej w tym kroku. Po utworzeniu łącznika stron biznesowych serwisu Facebook w usłudze Centrum zgodności platformy Microsoft 365 (w kroku 5) usługa importowania skopiuje dane stron biznesowych serwisu Facebook z lokalizacji usługi Azure Storage do skrzynki pocztowej w Microsoft 365 organizacji. Jak wyjaśniono [wcześniej w sekcji](#prerequisites-for-setting-up-a-connector-for-facebook-business-pages) Wymagania wstępne, aby utworzyć konto azure dla usługi Azure Storage, musisz mieć ważną subskrypcję Storage Azure.

Aby uzyskać instrukcje krok po kroku, zobacz Wdrażanie usługi sieci Web łącznika z GitHub [na koncie platformy Azure](deploy-facebook-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).

W instrukcjach krok po kroku dotyczących wykonania tego kroku podano następujące informacje:

- APISecretKey: Ten klucz tajny należy utworzyć podczas wykonania tego kroku. Jest on używany w kroku 5.

- TenantId: Identyfikator dzierżawy organizacji Microsoft 365, która została skopiowana po utworzeniu aplikacji łącznika serwisu Facebook w programie Azure Active Directory kroku 1.

Po wykonaniu tego kroku pamiętaj o skopiowaniu adresu URL usługi aplikacji Azure (na przykład https://fbconnector.azurewebsites.net). Musisz użyć tego adresu URL do wykonania kroków 3, 4 i 5).

## <a name="step-3-register-the-web-app-on-facebook"></a>Krok 3. Rejestrowanie aplikacji sieci Web w serwisie Facebook

Następnym krokiem jest utworzenie i skonfigurowanie nowej aplikacji w serwisie Facebook. Łącznik stron biznesowych serwisu Facebook, który tworzysz w kroku 5, współdziała z interfejsem API serwisu Facebook w celu uzyskiwania danych ze stron biznesowych organizacji w serwisie Facebook.

Aby uzyskać instrukcje krok po kroku, zobacz [Rejestrowanie aplikacji Facebook](deploy-facebook-connector.md#step-3-register-the-facebook-app).

Po wykonaniu tego kroku (zgodnie z instrukcjami krok po kroku) poniższe informacje są zapisywane w pliku tekstowym. Te wartości służą do konfigurowania aplikacji Łącznik serwisu Facebook w kroku 4.

- Identyfikator aplikacji serwisu Facebook

- Tajny program serwisu Facebook

- Token weryfikacji w sieci Web serwisu Facebook

## <a name="step-4-configure-the-facebook-connector-app"></a>Krok 4. Konfigurowanie aplikacji Łącznik serwisu Facebook

Następnym krokiem jest dodanie ustawień konfiguracji do aplikacji łącznika serwisu Facebook, która została przesłana podczas tworzenia zasobu aplikacji Azure Web App w kroku 1. Możesz to zrobić, przechodząc do strony głównej aplikacji łącznika i konfigurując ją.

Aby uzyskać instrukcje krok po kroku, [zobacz Konfigurowanie aplikacji łącznika serwisu Facebook](archive-facebook-data-with-sample-connector.md#step-4-configure-the-facebook-connector-app).

Po wykonaniu tego kroku (wykonując instrukcje krok po kroku) podaj następujące informacje (skopiowane do pliku tekstowego po wykonaniu poprzednich kroków):

- Identyfikator aplikacji serwisu Facebook (uzyskany w kroku 3)

- Tajny program serwisu Facebook (uzyskany w kroku 3)

- Token weryfikacji w sieci Web serwisu Facebook (uzyskany w kroku 3)

- Azure Active Directory aplikacji (identyfikator AAD aplikacji uzyskany w kroku 1)

- Azure Active Directory tajny aplikacji (AAD tajna aplikacji uzyskana w kroku 1)

## <a name="step-5-set-up-a-facebook-business-pages-connector-in-the-microsoft-365-compliance-center"></a>Krok 5. Konfigurowanie łącznika stron biznesowych serwisu Facebook w Centrum zgodności platformy Microsoft 365

Ostatnim krokiem jest skonfigurowanie łącznika w Centrum zgodności platformy Microsoft 365, który zaimportuje dane ze stron biznesowych serwisu Facebook do określonej skrzynki pocztowej w Microsoft 365. Po zakończeniu tego kroku usługa importowania Microsoft 365 rozpocznie importowanie danych ze stron biznesowych serwisu Facebook w celu Microsoft 365.

Aby uzyskać instrukcje krok po kroku, zobacz [Krok 5. Konfigurowanie](deploy-facebook-connector.md#step-5-set-up-a-facebook-connector-in-the-microsoft-365-compliance-center) łącznika serwisu Facebook w aplikacji Centrum zgodności platformy Microsoft 365. 

Po wykonaniu tego kroku (zgodnie z instrukcjami krok po kroku) należy podać następujące informacje (skopiowane do pliku tekstowego po wykonaniu tych czynności).

- AAD aplikacji (uzyskany w kroku 1)

- Adres URL usługi aplikacji Azure (uzyskany w kroku 1, na przykład https://fbconnector.azurewebsites.net)

- APISecretKey (utworzony w kroku 2)