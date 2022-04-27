---
title: Testowanie podstawowego interfejsu API & SDK
description: Testowanie podstawowego interfejsu API & SDK
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 6ae0fdf9cc49faaaff84eb3f96e076d1efba8a4c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077432"
---
# <a name="manage-your-resource-with-sdk--apis"></a>Zarządzanie zasobem przy użyciu zestawu SDK & interfejsów API

Automatyzacja jest kluczowym aspektem DevOps i zwinnego programowania. Chcesz zarządzać bazą testów dla zasobów Microsoft 365, programowo uzyskiwać wyniki testów i integrować je z naszymi narzędziami ciągłej integracji? Testowe podstawowe interfejsy API/zestaw SDK mogą pomóc w osiągnięciu tych wszystkich i nie tylko!

Te interfejsy API/zestaw SDK umożliwiają specjalistom IT i deweloperom aplikacji:

- Zarządzaj kontami bazy testów, w tym tworzeniem, aktualizowaniem i odłączakiem.
- Zarządzaj pakietami aplikacji, w tym tworzeniem, aktualizowaniem, usuwaniem i pobieraniem pakietu.
- Pobierz podsumowanie testu, szczegółowe wyniki testu i wyniki analizy. Wynik analizy obejmuje analizę regresji procesora CPU, analizę wykorzystania procesora CPU, analizę regresji pamięci i analizę wykorzystania pamięci.
- Pobieranie wyników testów i nagrywanie wideo wykonywania testu.

Zapoznaj się z poniższym konspektem krok po kroku, aby dowiedzieć się, jak uzyskać dostęp do tej nowej funkcji w bazie testowej dla usługi Microsoft 365.

## <a name="a-step-by-step-example-of-test-base-account-creation-by-using-python-sdk"></a>Przykład krok po kroku tworzenia konta bazy testowej przy użyciu zestawu Python SDK

1. Wymagania wstępne:

   - Zainstaluj poniższe wymagane składniki:

     - [Konto platformy Azure z aktywną subskrypcją](https://azure.microsoft.com/free/?utm_source=campaign&utm_campaign=python-dev-center&mktingSource=environment-setup) , jeśli nie masz subskrypcji
     - [Python 2.7 lub 3.6+](https://www.python.org/downloads)
     - [Interfejs interfejsu wiersza polecenia platformy Azure Command-Line](/cli/azure/install-azure-cli)

   - Instalowanie pakietów biblioteki przy użyciu instalacji pip z konsoli

     ```console
     pip install azure-identity
     pip install azure-mgmt-testbase
     ```

   - Uwierzytelnianie w środowisku deweloperskim

     Podczas debugowania i wykonywania kodu lokalnie deweloperzy często używają własnych kont do uwierzytelniania wywołań w usługach platformy Azure. Pakiet azure-identity obsługuje uwierzytelnianie za pośrednictwem interfejsu wiersza polecenia platformy Azure, aby uprościć programowanie lokalne. Aby zalogować się do interfejsu wiersza polecenia platformy Azure, uruchom polecenie `az login`. W systemie z domyślną przeglądarką internetową interfejs wiersza polecenia platformy Azure uruchomi przeglądarkę w celu uwierzytelnienia użytkownika.

     Sprawdź[, jak uwierzytelniać aplikacje języka Python za pomocą usług platformy Azure| Microsoft Docs](/azure/developer/python/azure-sdk-authenticate) i <https://pypi.org/project/azure-identity/> innych obsługiwanych metod uwierzytelniania.

   - Utwórz grupę zasobów o żądanej nazwie, która będzie używana w poniższych krokach.

2. Poniższy fragment kodu obejmuje przepływ w celu utworzenia testowego konta podstawowego, w tym

   - Żądanie poświadczenia za pośrednictwem interfejsu wiersza polecenia platformy Azure w celu interakcji z platformą Azure
   - Inicjowanie klienta zestawu Test Base SDK przy użyciu poświadczeń i identyfikatora subskrypcji dla późniejszych operacji
   - Wywoływanie begin_create z modelu test_base_accounts w celu utworzenia konta bazy testowej

   Skopiuj kod do środowiska deweloperskiego języka Python i zastąp ciąg "subscription-id" identyfikatorem subskrypcji platformy Azure i "nazwą grupy zasobów" utworzoną powyżej grupą zasobów.

   ```python
   from azure.identity import AzureCliCredential
   from azure.mgmt.testbase import TestBase
   from azure.mgmt.testbase.models import TestBaseAccountResource
   from azure.mgmt.testbase.models import TestBaseAccountSKU

   # requesting token from Azure CLI for request
   # For other authentication approaches, please see: https://pypi.org/project/azure-identity/
   credential = AzureCliCredential()
   subscription_id = "<subscription-id>"
   resource_group = "<resource-group-name>"
   testBaseAccount_name = "contoso-testbaseAccount"
   testBaseAccount_location = "global"
   sku_name = "S0"
   sku_tier = "Standard"
   sku_locations = {"global"}
  
   # Create client
   testBase_client = TestBase(credential, subscription_id)
  
   # Create sku for test base account
   sku = TestBaseAccountSKU(name=sku_name, tier=sku_tier, locations=sku_locations)
  
   # Create test base account
   parameters = TestBaseAccountResource(location=testBaseAccount_location, sku=sku)
   testBaseAccount = testBase_client.test_base_accounts.begin_create(resource_group, testBaseAccount_name, parameters).result()
   print("Create test base account:\n{}".format(testBaseAccount))
   ```

## <a name="learn-more"></a>Dowiedz się więcej

Skorzystaj z poniższych linków, aby dowiedzieć się więcej o interfejsie API & zestawu SDK.

**Subskrypcja platformy Azure**:

- [Konto platformy Azure z aktywną subskrypcją](https://azure.microsoft.com/free/?utm_source=campaign&utm_campaign=python-dev-center&mktingSource=environment-setup)

**Zestaw SDK języka Python**:

- [Dokumentacja zestawu Test Base Python SDK](/python/api/overview/azure/mgmt-testbase-readme)
- [Przykład testu podstawowego zestawu SDK języka Python](https://aka.ms/testbase-sample-py)
- [Wzorzec ogólnego użycia zestawu Python SDK na platformie Azure](/azure/developer/python/sdk/azure-sdk-library-usage-patterns)

**Interfejs API REST**:

- [Dokumentacja interfejsu API REST](https://aka.ms/testbase-api)
