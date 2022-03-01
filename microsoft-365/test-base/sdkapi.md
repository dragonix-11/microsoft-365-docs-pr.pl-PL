---
title: Test Base API & SDK
description: Test Base API & SDK
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
ms.openlocfilehash: f7e5edeeac79b417bcb41f8607c46fc8894ea4fc
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "63005279"
---
# <a name="manage-your-resource-with-sdk--apis"></a>Zarządzanie zasobem przy użyciu interfejsów API & SDK
Automatyzacja to kluczowy aspekt rozwoju DevOps agile. Chcesz zarządzać bazą testową dla zasobów Microsoft 365, programowo uzyskać wyniki testów i zintegrować je z naszymi narzędziami ci? Test podstawowych interfejsów API/zestawu SDK może pomóc Ci osiągnąć te i nie tylko! 

Te interfejsy API/zestaw SDK umożliwiają informatykom i deweloperom aplikacji: 
- Zarządzaj kontami bazy testowej, w tym tworzenie, aktualizowanie i wyechiwki. 
- Zarządzaj pakietami aplikacji, w tym tworzenie, aktualizowanie, usuwanie i pobieranie pakietu. 
- Uzyskaj podsumowanie testu, szczegółowe wyniki testów i wyniki analizy. Wynik analizy obejmuje analizę regresji procesora, analizę użycia procesora, analizę regresji pamięci i analizę użycia pamięci. 
- Pobierz wyniki testów i przetestuj nagranie wideo wykonywania.  

Zapoznaj się z poniższym konspektem krok po kroku, aby dowiedzieć się, jak uzyskać dostęp do tej nowej funkcji w bazie testowej dla Microsoft 365 usługi.

## <a name="a-step-by-step-example-of-test-base-account-creation-by-using-python-sdk"></a>Przykład krok po kroku tworzenia konta podstawowego w języku Python przy użyciu zestawu SDK języka Python

1. Wymagania wstępne: 

- Zainstaluj poniżej wymaganych składników: 

    [Konto Azure z aktywną subskrypcją](https://azure.microsoft.com/free/?utm_source=campaign&utm_campaign=python-dev-center&mktingSource=environment-setup) , jeśli nie masz subskrypcji<br>
    [Python 2.7+ lub 3.6+](https://www.python.org/downloads)<br>
    [Azure Command-Line Interface (CLI)](/cli/azure/install-azure-cli) <br>

- Instalowanie pakietów bibliotek przy użyciu instalacji rurowej z konsoli 

```
pip install azure-identity 
pip install azure-mgmt-testbase
```

- Autentyczność w środowisku dewelopera 

Podczas debugowania i wykonywania kodu lokalnie typowe dla deweloperów jest używanie własnych kont do uwierzytelniania połączeń z usługami Azure. Pakiet azure-identity obsługuje uwierzytelnianie za pośrednictwem interfejsu azure CLI w celu uproszczenia opracowywania lokalnego. Aby zalogować się do usługi Azure CLI, uruchom narzędzie ```az login ```. W systemie z domyślną przeglądarką sieci Web identyfikator Azure CLI uruchomi przeglądarkę w celu uwierzytelnienia użytkownika. 

Sprawdź [, jak uwierzytelnić aplikacje w języku Python za pomocą usług platformy Azure| Dokumenty Microsoft i](/azure/developer/python/azure-sdk-authenticate)  inne [https://pypi.org/project/azure-identity/](https://pypi.org/project/azure-identity/) obsługiwane metody uwierzytelniania. 

 - Utwórz grupę zasobów o odpowiedniej nazwie, która zostanie użyta w poniższych krokach. 

2. Poniżej fragmentu kodu przedstawiono przepływ tworzenia podstawowego konta testowego obejmującego m.in. 

- Żądanie poświadczeń za pośrednictwem interfejsu azure cli w celu interakcji z platformą Azure 
- Initialize Test Base SDK client with the credential and subscription ID for later operations 
- Wywoływanie begin_create z test_base_accounts w celu utworzenia konta testowego 

Skopiuj kod do środowiska programistyki w języku Python i zastąp "identyfikator subskrypcji" identyfikatorem subskrypcji platformy Azure i "resource-group-name" utworzoną powyżej grupą zasobów. 

 
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

Sprawdź poniższe linki, aby dowiedzieć się więcej o interfejsie API & SDK. 

**Subskrypcja platformy Azure** 

- [Konto Azure z aktywną subskrypcją](https://azure.microsoft.com/free/?utm_source=campaign&utm_campaign=python-dev-center&mktingSource=environment-setup)

**Python SDK** 

- [Dokumentacja zestawu SDK języka Base Python](/python/api/overview/azure/mgmt-testbase-readme)
- [Test Base Python SDK Sample](https://aka.ms/testbase-sample-py)
- [Azure General Usage Pattern of Python SDK](/azure/developer/python/azure-sdk-overview#provision-and-manage-azure-resources-with-management-libraries)

**REST API**  

- [Dokumentacja interfejsu API usługi REST](https://aka.ms/testbase-api)  
