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
description: Dowiedz się więcej o szyfrowaniu dostępnym na platformie Azure, takim jak szyfrowanie dysków platformy Azure
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f3672800b6f90277195a63b640911ea1ed24cac9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983167"
---
# <a name="encryption-in-azure"></a>Szyfrowanie na platformie Azure

Zabezpieczanie danych na platformie Azure, takie jak zaszyfrowane procesy komunikacyjne i operacyjne, pomagają zabezpieczyć dane. Masz również możliwość wdrożenia dodatkowych funkcji szyfrowania i zarządzania własnymi kluczami kryptograficznymi. Niezależnie od konfiguracji klienta firma Microsoft stosuje szyfrowanie w celu ochrony danych klienta na platformie Azure. Firma Microsoft umożliwia również kontrolowanie danych hostowanych na platformie Azure za pośrednictwem szeregu zaawansowanych technologii do szyfrowania, kontrolowania kluczy kryptograficznych i zarządzania nimi, a także kontrolowania dostępu do danych i audytu do nich. Ponadto usługa Azure Storage udostępnia kompleksowy zestaw funkcji zabezpieczeń, które razem umożliwiają deweloperom tworzenie bezpiecznych aplikacji.

Platforma Azure udostępnia wiele mechanizmów ochrony danych podczas ich przesuwania w inne miejsce. Firma Microsoft używa usługi TLS do ochrony danych podczas podróży między usługami w chmurze a klientami. Centra danych firmy Microsoft wynegocjowają negocjacje w sprawie połączenia TLS z systemami klienckimi, które łączą się z usługami platformy Azure. Perfect Forward Secrecy (PFS) chroni połączenia między systemami klienckimi klientów i usługami firmy Microsoft w chmurze za pomocą unikatowych kluczy. Połączenia mają również 2048-bitowe długości kluczy szyfrowania oparte na RSA. Takie połączenie utrudnia przechwycenie i uzyskanie dostępu do danych podczas przesyłania.

Dane mogą być zabezpieczone podczas przesyłania między aplikacją a platformą Azure przy użyciu szyfrowania po stronie [klienta, https](/azure/storage/storage-client-side-encryption) lub SMB 3.0. Możesz włączyć szyfrowanie dla ruchu między własnymi maszynami wirtualnymi i użytkownikami. Za pomocą [wirtualnych sieci Azure](https://azure.microsoft.com/services/virtual-network/) możesz użyć standardowego protokołu IPsec, aby szyfrować ruch między firmową bramą VPN i platformą Azure, a także między maszynami wirtualnych zlokalizowanymi w Twojej sieci wirtualnej.

W przypadku danych w spoczynku platforma Azure oferuje wiele opcji szyfrowania, takich jak obsługa standardu AES-256, co zapewnia elastyczność w zakresie wyboru scenariusza przechowywania danych najlepiej spełniającego Twoje potrzeby. Dane mogą być automatycznie szyfrowane podczas zapisywania na platformie Azure Storage przy użyciu szyfrowania usługi [Storage, a](/azure/storage/storage-service-encryption) dyskietki systemu operacyjnego i danych używane przez maszyny wirtualne mogą być szyfrowane. Aby uzyskać więcej informacji, zobacz [Zalecenia dotyczące zabezpieczeń dla Windows maszyn wirtualnych na platformie Azure](/azure/security/azure-security-disk-encryption). Ponadto delegowany dostęp do obiektów danych w usłudze Azure Storage można przyznać przy użyciu [podpisów dostępu udostępnionego](/azure/storage/storage-dotnet-shared-access-signature-part-1). Platforma Azure udostępnia również szyfrowanie danych w miejscu przy [Transparent Data Encryption magazynach Azure SQL Database magazynach danych](/sql/relational-databases/security/encryption/transparent-data-encryption-azure-sql).

Aby uzyskać więcej informacji na temat szyfrowania na platformie Azure, zobacz [Omówienie szyfrowania platformy Azure](/azure/security/security-azure-encryption-overview) i Szyfrowanie [danych azure w spoczynku](/azure/security/azure-security-encryption-atrest).

## <a name="azure-disk-encryption"></a>Szyfrowanie dysków platformy Azure

Szyfrowanie dysków platformy Azure umożliwia szyfrowanie dysków Windows i infrastruktury systemu Linux jako usługi (IaaS) dysków maszyn wirtualnych. Szyfrowanie dysków platformy Azure korzysta z funkcji BitLocker firmy Windows oraz funkcji DM-Crypt systemu Linux w celu zapewnienia szyfrowania na poziomie głośności dla systemu operacyjnego i dyskietek z danymi. Zapewnia również szyfrowanie wszystkich danych na dyskach maszyn wirtualnych w magazynie platformy Azure. Szyfrowanie dysków platformy Azure jest zintegrowane z magazynem kluczy platformy Azure, co pomaga kontrolować korzystanie z kluczy szyfrowania i sekretów oraz zarządzać nimi i je kontrolować.

Aby uzyskać więcej informacji, zobacz [Zalecenia dotyczące zabezpieczeń dla Windows maszyn wirtualnych na platformie Azure](/azure/virtual-machines/windows/security-recommendations).

## <a name="azure-storage-service-encryption"></a>Szyfrowanie usługi Azure Storage

Dzięki [szyfrowaniu usługi Azure Storage](/azure/storage/storage-service-encryption) usługa Azure Storage automatycznie szyfruje dane przed ich przechowywaniem i odszyfrowuje dane przed pobraniem. Procesy szyfrowania, odszyfrowywania i zarządzania kluczami są całkowicie przezroczyste dla użytkowników. Szyfrowanie usługi Azure Storage może być używane dla obiektów [blob platformy Azure Storage](https://azure.microsoft.com/services/storage/blobs/) [plików obiektów blob platformy Azure](https://azure.microsoft.com/services/storage/files/). Możesz również używać kluczy szyfrowania zarządzanych przez firmę Microsoft z szyfrowaniem usługi Azure Storage lub możesz użyć własnych kluczy szyfrowania. (Aby uzyskać informacje na temat używania własnych kluczy, zobacz szyfrowanie Storage przy użyciu kluczy zarządzanych przez klienta w [magazynie kluczy platformy Azure](/azure/storage/common/storage-service-encryption-customer-managed-keys). Aby uzyskać informacje dotyczące używania kluczy zarządzanych przez firmę Microsoft, [zobacz szyfrowanie Storage danych w spoczynku](/azure/storage/storage-service-encryption)). Ponadto możesz zautomatyzować korzystanie z szyfrowania. Na przykład możesz programowo włączyć lub wyłączyć szyfrowanie usługi Storage na koncie magazynu przy użyciu interfejsu API REST dostawcy zasobów platformy [Azure Storage](/rest/api/storagerp/), biblioteki klienta dostawcy zasobów usługi Storage dla sieci [.NET](/dotnet/api/overview/azure/storage)[, Azure PowerShell](/powershell/azureps-cmdlets-docs) lub interfejsu [wideo usługi Azure](/azure/storage/storage-azure-cli).

Niektóre Microsoft 365 korzystają z platformy Azure do przechowywania danych. Na przykład usługa SharePoint Online i usługa OneDrive dla Firm przechowują dane w magazynie obiektów blob platformy Azure, a program Microsoft Teams przechowuje dane dla swojej usługi czatu w tabelach, obiektach blob i kolejkach. Ponadto funkcja Menedżera zgodności w usłudze Centrum zgodności platformy Microsoft 365 przechowuje dane wprowadzone przez klienta, które są przechowywane w zaszyfrowanej formie w usłudze [Azure Cosmos DB](/azure/cosmos-db/database-encryption-at-rest), platformie jako usługi (PaaS), globalnej dystrybucji wielo modelowej bazy danych. Szyfrowanie usługi Azure Storage szyfruje dane przechowywane w magazynie obiektów blob platformy Azure i w tabelach, a szyfrowanie dysków platformy Azure szyfruje dane w kolejkach, a także dysków maszyn wirtualnych usług Windows i IaaS w celu zapewnienia szyfrowania woluminu dla systemu operacyjnego i dysku danych. Rozwiązanie to gwarantuje, że wszystkie dane na dyskach maszyn wirtualnych są szyfrowane w magazynie platformy Azure. [Szyfrowanie w miejscu w usłudze Azure Cosmos DB](/azure/cosmos-db/database-encryption-at-rest) jest implementowane przy użyciu kilku technologii zabezpieczeń, w tym bezpiecznych kluczowych systemów magazynu, zaszyfrowanych sieci i interfejsów API szyfrowania.

## <a name="azure-key-vault"></a>Magazyn kluczy platformy Azure

Bezpieczne zarządzanie kluczami nie jest tylko podstawowym elementem najlepszych rozwiązań szyfrowania. jest także niezbędny do ochrony danych w chmurze. [Magazyn kluczy platformy Azure](/azure/key-vault/key-vault-whatis) umożliwia szyfrowanie kluczy i małych sekretów, takich jak hasła, które korzystają z kluczy przechowywanych w modułach zabezpieczeń sprzętowych (HSM). Magazyn kluczy platformy Azure to zalecane przez firmę Microsoft rozwiązanie do zarządzania i kontrolowania dostępu do kluczy szyfrowania używanych przez usługi w chmurze. Uprawnienia do kluczy dostępu można przypisywać do usług lub do użytkowników z Azure Active Directory kontami. Magazyn kluczy platformy Azure zwalnia organizacje z konieczności konfigurowania, poprawiania i utrzymywania HSM oraz oprogramowania do zarządzania kluczami. Dzięki magazynowi kluczy platformy Azure firma Microsoft nigdy nie widzi Kluczy i aplikacji nie ma do nich bezpośredniego dostępu. zachować kontrolę. Można również importować lub generować klucze w modułach HSM. Organizacje, które mają subskrypcję, która obejmuje usługę Azure Information Protection, mogą skonfigurować swoją dzierżawę usługi Azure Information Protection do używania klucza zarządzanego przez klienta Bring [Your Own Key](/information-protection/plan-design/byok-price-restrictions) (BYOK) i rejestrować [jego użycie](/information-protection/deploy-use/log-analyze-usage).