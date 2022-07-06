---
title: Szyfrowanie na platformie Azure
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-security-compliance
- Strat_O365_Enterprise
description: Dowiedz się więcej o szyfrowaniu dostępnym na platformie Azure, takim jak usługa Azure Disk Encryption
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 66fb4e54c0837534d6943372d84cf3a4864e4739
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632184"
---
# <a name="encryption-in-azure"></a>Szyfrowanie na platformie Azure

Zabezpieczenia technologiczne na platformie Azure, takie jak szyfrowana komunikacja i procesy operacyjne, pomagają zapewnić bezpieczeństwo danych. Możesz również elastycznie implementować dodatkowe funkcje szyfrowania i zarządzać własnymi kluczami kryptograficznymi. Niezależnie od konfiguracji klienta firma Microsoft stosuje szyfrowanie w celu ochrony danych klientów na platformie Azure. Firma Microsoft umożliwia również kontrolowanie danych hostowanych na platformie Azure za pomocą szeregu zaawansowanych technologii do szyfrowania, kontrolowania i zarządzania kluczami kryptograficznymi oraz kontrolowania i inspekcji dostępu do danych. Ponadto usługa Azure Storage oferuje kompleksowy zestaw funkcji zabezpieczeń, które razem umożliwiają deweloperom tworzenie bezpiecznych aplikacji.

Platforma Azure oferuje wiele mechanizmów ochrony danych w miarę ich przenoszenia z jednej lokalizacji do innej. Firma Microsoft używa protokołu TLS do ochrony danych podczas podróży między usługami w chmurze a klientami. Centra danych firmy Microsoft negocjują połączenie TLS z systemami klienckimi łączącymi się z usługami platformy Azure. Usługa Perfect Forward Secrecy (PFS) chroni połączenia między systemami klienckimi klientów i usługami firmy Microsoft w chmurze za pomocą unikatowych kluczy. Połączenia używają również 2048-bitowych długości kluczy szyfrowania opartych na RSA. Ta kombinacja utrudnia komuś przechwycenie przesyłanych danych i uzyskanie do nich dostępu.

Dane mogą być zabezpieczone podczas przesyłania między aplikacją a platformą Azure przy użyciu [szyfrowania po stronie klienta](/azure/storage/storage-client-side-encryption), protokołu HTTPS lub protokołu SMB 3.0. Możesz włączyć szyfrowanie ruchu między własnymi maszynami wirtualnymi a użytkownikami. Za pomocą [usługi Azure Virtual Networks](https://azure.microsoft.com/services/virtual-network/) można użyć standardowego w branży protokołu IPsec do szyfrowania ruchu między firmową bramą sieci VPN a platformą Azure, a także między maszynami wirtualnymi znajdującymi się na Virtual Network.

W przypadku danych magazynowanych platforma Azure oferuje wiele opcji szyfrowania, takich jak obsługa rozwiązania AES-256, co zapewnia elastyczność wyboru scenariusza przechowywania danych, który najlepiej spełnia Twoje potrzeby. Dane mogą być automatycznie szyfrowane podczas zapisywania w usłudze Azure Storage przy użyciu [szyfrowania usługi Storage](/azure/storage/storage-service-encryption), a dyski systemu operacyjnego i danych używane przez maszyny wirtualne mogą być szyfrowane. Aby uzyskać więcej informacji, zobacz [Zalecenia dotyczące zabezpieczeń maszyn wirtualnych z systemem Windows na platformie Azure](/azure/security/azure-security-disk-encryption). Ponadto delegowany dostęp do obiektów danych w usłudze Azure Storage można udzielić przy użyciu [sygnatur dostępu współdzielonego](/azure/storage/storage-dotnet-shared-access-signature-part-1). Platforma Azure zapewnia również szyfrowanie danych magazynowanych przy użyciu [funkcji Transparent Data Encryption dla Azure SQL Database i Data Warehouse](/sql/relational-databases/security/encryption/transparent-data-encryption-azure-sql).

Aby uzyskać więcej informacji na temat szyfrowania na platformie Azure, zobacz [Omówienie szyfrowania platformy Azure](/azure/security/security-azure-encryption-overview) i [Azure Data Encryption-at-Rest](/azure/security/azure-security-encryption-atrest).

## <a name="azure-disk-encryption"></a>Azure Disk Encryption

Usługa Azure Disk Encryption umożliwia szyfrowanie dysków maszyn wirtualnych infrastruktury systemu Windows i Systemu Linux jako usługi (IaaS). Usługa Azure Disk Encryption korzysta z funkcji BitLocker systemu Windows i funkcji DM-Crypt systemu Linux w celu zapewnienia szyfrowania na poziomie woluminu dla systemu operacyjnego i dysków danych. Zapewnia również, że wszystkie dane na dyskach maszyn wirtualnych są szyfrowane w magazynie platformy Azure. Usługa Azure Disk Encryption jest zintegrowana z usługą Azure Key Vault, aby ułatwić kontrolowanie i inspekcję użycia kluczy szyfrowania i wpisów tajnych oraz zarządzanie nimi.

Aby uzyskać więcej informacji, zobacz [Zalecenia dotyczące zabezpieczeń maszyn wirtualnych z systemem Windows na platformie Azure](/azure/virtual-machines/windows/security-recommendations).

## <a name="azure-storage-service-encryption"></a>Szyfrowanie usługi Azure Storage

Dzięki [szyfrowaniu usługi Azure Storage](/azure/storage/storage-service-encryption) usługa Azure Storage automatycznie szyfruje dane przed utrwaleniem ich w magazynie i odszyfrowuje dane przed pobraniem. Procesy szyfrowania, odszyfrowywania i zarządzania kluczami są całkowicie niewidoczne dla użytkowników. Szyfrowanie usługi Azure Storage może służyć do [Azure Blob Storage](https://azure.microsoft.com/services/storage/blobs/) i [Azure Files](https://azure.microsoft.com/services/storage/files/). Możesz również użyć kluczy szyfrowania zarządzanych przez firmę Microsoft z szyfrowaniem usługi Azure Storage lub użyć własnych kluczy szyfrowania. (Aby uzyskać informacje na temat korzystania z własnych kluczy, zobacz [Szyfrowanie usługi Storage przy użyciu kluczy zarządzanych przez klienta w usłudze Azure Key Vault](/azure/storage/common/storage-service-encryption-customer-managed-keys). Aby uzyskać informacje na temat korzystania z kluczy zarządzanych przez firmę Microsoft, zobacz [Szyfrowanie usługi Storage dla danych w spoczynku](/azure/storage/storage-service-encryption)). Ponadto można zautomatyzować korzystanie z szyfrowania. Możesz na przykład programowo włączyć lub wyłączyć szyfrowanie usługi Storage na koncie magazynu przy użyciu [interfejsu API REST dostawcy zasobów usługi Azure Storage](/rest/api/storagerp/), [biblioteki klienta dostawcy zasobów magazynu dla platformy .NET](/dotnet/api/overview/azure/storage), [Azure PowerShell](/powershell/azureps-cmdlets-docs) lub [interfejsu wiersza polecenia platformy Azure](/azure/storage/storage-azure-cli).

Niektóre usługi platformy Microsoft 365 używają platformy Azure do przechowywania danych. Na przykład usługi SharePoint Online i OneDrive dla Firm przechowują dane w usłudze Azure Blob Storage, a usługa Microsoft Teams przechowuje dane dla swojej usługi czatu w tabelach, obiektach blob i kolejkach. Ponadto funkcja Menedżera zgodności w portal zgodności Microsoft Purview przechowuje dane wprowadzone przez klienta, które są przechowywane w postaci [zaszyfrowanej w usłudze Azure Cosmos DB](/azure/cosmos-db/database-encryption-at-rest), platformie jako usłudze (PaaS), globalnie rozproszonej, wielomodelowej bazie danych. Usługa Azure Storage Service Encryption szyfruje dane przechowywane w usłudze Azure Blob Storage i w tabelach, a usługa Azure Disk Encryption szyfruje dane w kolejkach, a także dyski maszyn wirtualnych z systemami Windows i IaaS w celu zapewnienia szyfrowania woluminów dla systemu operacyjnego i dysku danych. Rozwiązanie zapewnia, że wszystkie dane na dyskach maszyny wirtualnej są szyfrowane w magazynie platformy Azure. [Szyfrowanie magazynowane w usłudze Azure Cosmos DB](/azure/cosmos-db/database-encryption-at-rest) jest implementowane przy użyciu kilku technologii zabezpieczeń, w tym bezpiecznych systemów magazynu kluczy, zaszyfrowanych sieci i kryptograficznych interfejsów API.

## <a name="azure-key-vault"></a>Azure Key Vault

Bezpieczne zarządzanie kluczami to nie tylko podstawowe rozwiązania dotyczące szyfrowania; Jest również niezbędna do ochrony danych w chmurze. [Usługa Azure Key Vault](/azure/key-vault/key-vault-whatis) umożliwia szyfrowanie kluczy i małych wpisów tajnych, takich jak hasła korzystające z kluczy przechowywanych w sprzętowych modułach zabezpieczeń (HSM). Usługa Azure Key Vault to zalecane rozwiązanie firmy Microsoft do zarządzania dostępem do kluczy szyfrowania używanych przez usługi w chmurze i kontrolowania go. Uprawnienia dostępu do kluczy można przypisać do usług lub użytkowników z kontami usługi Azure Active Directory. Usługa Azure Key Vault zwalnia organizacje z konieczności konfigurowania, stosowania poprawek i obsługi modułów HSM oraz oprogramowania do zarządzania kluczami. Dzięki usłudze Azure Key Vault firma Microsoft nigdy nie widzi, że Twoje klucze i aplikacje nie mają bezpośredniego dostępu do nich. Zachowujesz kontrolę. Możesz również zaimportować lub wygenerować klucze w modułach HSM. Organizacje, które mają subskrypcję obejmującą usługę Azure Information Protection, mogą skonfigurować dzierżawę usługi Azure Information Protection, aby korzystała z klucza zarządzanego przez klienta [Przynieś własny klucz](/information-protection/plan-design/byok-price-restrictions) (BYOK) i [rejestrowała jego użycie](/information-protection/deploy-use/log-analyze-usage).
