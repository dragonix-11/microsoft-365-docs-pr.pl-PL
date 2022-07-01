---
title: Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu obiektów zasady grupy
description: Dowiedz się, jak zarządzać Ochrona punktu końcowego w usłudze Microsoft Defender za pomocą obiektów zasady grupy
keywords: po migracji, zarządzaniu, operacjach, konserwacji, wykorzystaniu, programie PowerShell, Ochrona punktu końcowego w usłudze Microsoft Defender, edr
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: article
ms.reviewer: chventou
ms.openlocfilehash: 3c7c72597416bda80894f8d44fbf5dbba3d58808
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603907"
---
# <a name="manage-microsoft-defender-for-endpoint-with-group-policy-objects"></a>Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender za pomocą obiektów zasady grupy

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Zalecamy używanie usługi [Microsoft Endpoint Manager](/mem) do zarządzania funkcjami ochrony przed zagrożeniami w organizacji dla urządzeń (nazywanych również punktami końcowymi). Endpoint Manager obejmuje [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) i [Configuration Manager punktu końcowego firmy Microsoft](/mem/configmgr/core/understand/introduction). **[Dowiedz się więcej o Endpoint Manager](/mem/endpoint-manager-overview)**.

Za pomocą zasady grupy Objects na platformie Azure Active Directory Domain Services można zarządzać niektórymi ustawieniami w Ochrona punktu końcowego w usłudze Microsoft Defender.

## <a name="configure-microsoft-defender-for-endpoint-with-group-policy-objects"></a>Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu obiektów zasady grupy

> [!NOTE]
> Jeśli używasz [nowego, ujednoliconego rozwiązania Ochrona punktu końcowego w usłudze Microsoft Defender dla Windows Server 2012 R2 i 2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview), upewnij się, że używasz najnowszych plików ADMX w magazynie centralnym, aby uzyskać dostęp do poprawnego Ochrona punktu końcowego w usłudze Microsoft Defender opcje zasad. Zapoznaj się z artykułem [How to create the Central Store for zasady grupy Administrative Templates in Windows and download the latest files for use with Windows 10 (Jak utworzyć sklep centralny dla szablonów administracyjnych zasady grupy w systemie Windows i zarządzać](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) nimi oraz pobierać najnowsze pliki **do użycia z Windows 10**. 

W poniższej tabeli wymieniono różne zadania, które można wykonać w celu skonfigurowania Ochrona punktu końcowego w usłudze Microsoft Defender za pomocą zasady grupy Objects.

|Zadanie|Zasoby, aby dowiedzieć się więcej|
|---|---|
|**Zarządzanie ustawieniami obiektów użytkowników i komputerów** <br/><br/> *Dostosuj wbudowane obiekty zasady grupy lub utwórz niestandardowe obiekty zasady grupy i jednostki organizacyjne zgodnie z potrzebami organizacji.*|[Administrowanie zasady grupy w domenie zarządzanej Active Directory Domain Services platformy Azure](/azure/active-directory-domain-services/manage-group-policy)|
|**Konfigurowanie programu antywirusowego Microsoft Defender** <br/><br/> *Konfigurowanie funkcji antywirusowych & możliwości, w tym ustawień zasad, wykluczeń, korygowania i zaplanowanych skanów na urządzeniach organizacji (nazywanych również punktami końcowymi).*|[Konfigurowanie programu antywirusowego Microsoft Defender i zarządzanie nimi przy użyciu ustawień zasady grupy](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus) <br/><br/> [Używanie zasady grupy do włączania ochrony dostarczanej w chmurze](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-group-policy-to-enable-cloud-delivered-protection)|
|**Zarządzanie regułami zmniejszania obszaru ataków w organizacji** <br/><br/> *Dostosuj reguły zmniejszania obszaru ataków, wykluczając pliki & foldery lub dodając niestandardowy tekst do alertów powiadomień wyświetlanych na urządzeniach użytkowników.*|[Dostosowywanie reguł zmniejszania obszaru ataków za pomocą obiektów zasady grupy](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-deployment-implement)|
|**Zarządzanie ustawieniami ochrony przed lukami w zabezpieczeniach** <br/><br/> *Możesz dostosować ustawienia ochrony przed lukami w zabezpieczeniach, zaimportować plik konfiguracji, a następnie użyć zasady grupy do wdrożenia tego pliku konfiguracji.*|[Dostosowywanie ustawień ochrony przed lukami w zabezpieczeniach](/microsoft-365/security/defender-endpoint/customize-exploit-protection) <br/><br/> [Importuj, eksportuj i wdrażaj konfigurację ochrony przed wykorzystaniem](/microsoft-365/security/defender-endpoint/import-export-exploit-protection-emet-xml) <br/><br/> [Dystrybucja konfiguracji przy użyciu zasady grupy](/microsoft-365/security/defender-endpoint/import-export-exploit-protection-emet-xml#use-group-policy-to-distribute-the-configuration)|
|**Włącz ochronę sieci,** aby uniemożliwić pracownikom korzystanie z aplikacji, które mają złośliwą zawartość w Internecie <br/><br/> *Zalecamy używanie [najpierw trybu inspekcji](/microsoft-365/security/defender-endpoint/evaluate-network-protection) do ochrony sieci w środowisku testowym, aby sprawdzić, które aplikacje zostaną zablokowane przed wdrożeniem.*|[Włączanie ochrony sieci przy użyciu zasady grupy](/microsoft-365/security/defender-endpoint/enable-network-protection#group-policy)|
|**Konfigurowanie kontrolowanego dostępu do folderów** w celu ochrony przed oprogramowaniem wymuszającym okup <br/><br/> *[Kontrolowany dostęp do folderów](/microsoft-365/security/defender-endpoint/controlled-folders) jest również określany jako ochrona przed złośliwym oprogramowaniem.*|[Włączanie kontrolowanego dostępu do folderów przy użyciu zasady grupy](/microsoft-365/security/defender-endpoint/enable-controlled-folders#group-policy)|
|**Skonfiguruj filtr Microsoft Defender SmartScreen** w celu ochrony przed złośliwymi witrynami i plikami w Internecie.|[Konfigurowanie ustawień usługi Microsoft Defender SmartScreen zasady grupy i zarządzania urządzeniami przenośnymi (MDM) przy użyciu zasady grupy](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings#group-policy-settings)|
|**Konfigurowanie szyfrowania i BitLocker** w celu ochrony informacji na urządzeniach organizacji z systemem Windows|[ustawienia BitLocker zasady grupy](/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings)|
|**Konfigurowanie funkcji Microsoft Defender Credential Guard** w celu ochrony przed atakami kradzieży poświadczeń|[Włączanie Windows Defender Credential Guard przy użyciu zasady grupy](/windows/security/identity-protection/credential-guard/credential-guard-manage#enable-windows-defender-credential-guard-by-using-group-policy)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Konfigurowanie portalu Microsoft 365 Defender

Jeśli jeszcze tego nie zrobiono, skonfiguruj portal Microsoft 365 Defender w celu wyświetlania alertów, konfigurowania funkcji ochrony przed zagrożeniami i wyświetlania szczegółowych informacji o ogólnej kondycji zabezpieczeń organizacji. Zobacz [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Możesz również skonfigurować, czy i jakie funkcje użytkownicy końcowi mogą wyświetlać w portalu Microsoft 365 Defender.

- [Omówienie Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [Ochrona punktu końcowego: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Następne kroki

- [Omówienie Zarządzanie zagrożeniami i lukami](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Odwiedź pulpit nawigacyjny operacji zabezpieczeń portalu Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender za pomocą Intune](manage-mde-post-migration-intune.md)
