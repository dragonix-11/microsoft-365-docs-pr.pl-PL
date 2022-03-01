---
title: Zarządzanie programem Microsoft Defender dla punktu końcowego przy użyciu zasady grupy obiektów
description: Dowiedz się, jak zarządzać usługą Microsoft Defender dla punktu końcowego za zasady grupy obiektów
keywords: po migracji, zarządzanie, operacje, konserwacja, wykorzystanie, PowerShell, Microsoft Defender for Endpoint, edr
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
- m365solution-scenario
ms.topic: article
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: 2155c72d7008bf3669a1908b3fd866877eb36a7c
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2022
ms.locfileid: "63016592"
---
# <a name="manage-microsoft-defender-for-endpoint-with-group-policy-objects"></a>Zarządzanie programem Microsoft Defender for Endpoint za pomocą zasady grupy obiektów

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Zalecamy używanie programu [Microsoft Endpoint Manager](/mem) do zarządzania funkcjami ochrony przed zagrożeniami organizacji dla urządzeń (nazywanymi również punktami końcowymi). Endpoint Manager obejmuje [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) i [Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction). **[Dowiedz się więcej o Endpoint Manager](/mem/endpoint-manager-overview)**.

Za pomocą obiektów zasady grupy w Azure Active Directory domenowych możesz zarządzać niektórymi ustawieniami w programie Microsoft Defender for Endpoint.

## <a name="configure-microsoft-defender-for-endpoint-with-group-policy-objects"></a>Konfigurowanie programu Microsoft Defender dla punktu końcowego zasady grupy obiektów

> [!NOTE]
> Jeśli używasz nowego, ujednoliconego rozwiązania [Microsoft Defender for Endpoint dla wersji Windows Server 2012 R2 i 2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview), upewnij się, że używasz najnowszych plików ADMX w Twoim centralnym magazynie, aby uzyskać dostęp do właściwych opcji zasad programu Microsoft Defender dla punktu końcowego. Informacje na [temat tworzenia i](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) zarządzania centralną magazynem witryn zasady grupy administracyjnego w programie Windows oraz pobierania najnowszych plików do używania z **Windows 10.** 

W poniższej tabeli wymieniono różne zadania, które można wykonać w celu skonfigurowania programu Microsoft Defender dla punktu końcowego zasady grupy obiektów.

<br/><br/>

|Zadanie|Zasoby, aby dowiedzieć się więcej|
|---|---|
|**Zarządzanie ustawieniami obiektów użytkownika i komputera** <br/><br/> *Dostosowywanie wbudowanych obiektów zasady grupy lub tworzenie niestandardowych obiektów zasady grupy i jednostek organizacyjnych do potrzeb organizacji.*|[Administrowanie zasady grupy domeną zarządzaną Azure Active Directory domenowych](/azure/active-directory-domain-services/manage-group-policy)|
|**Konfigurowanie Program antywirusowy Microsoft Defender** <br/><br/> *Skonfiguruj funkcje oprogramowania antywirusowego & funkcje, takie jak ustawienia zasad, wykluczenia, działania naprawcze i zaplanowane skany na urządzeniach organizacji (nazywane także punktami końcowymi).*|[Konfigurowanie zasady grupy zarządzanie plikami Program antywirusowy Microsoft Defender i zarządzanie nimi zasady grupy](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus) <br/><br/> [Włączanie zasady grupy w chmurze za pomocą funkcji ochrony](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-group-policy-to-enable-cloud-delivered-protection)|
|**Zarządzanie regułami zmniejszania powierzchni ataków Twojej organizacji** <br/><br/> *Dostosuj reguły ograniczania powierzchni ataków, wykluczając pliki & lub dodając niestandardowy tekst do alertów powiadomień wyświetlanych na urządzeniach użytkowników.*|[Dostosowywanie reguł zmniejszania powierzchni ataków za pomocą zasady grupy obiektów](/microsoft-365/security/defender-endpoint/customize-attack-surface-reduction#use-group-policy-to-exclude-files-and-folders)|
|**Zarządzanie ustawieniami ochrony przed wykorzystywaniem luk w zabezpieczeniach** <br/><br/> *Możesz dostosować ustawienia ochrony przed wykorzystywaniem luk, zaimportować plik konfiguracji, a następnie użyć zasady grupy w celu wdrożenia tego pliku konfiguracji.*|[Dostosowywanie ustawień ochrony przed lukami w zabezpieczeniach](/microsoft-365/security/defender-endpoint/customize-exploit-protection) <br/><br/> [Importowanie, eksportowanie i wdrażanie konfiguracji ochrony przed wykorzystywaniem luk](/microsoft-365/security/defender-endpoint/import-export-exploit-protection-emet-xml) <br/><br/> [Używanie zasady grupy do rozpowszechniania konfiguracji](/microsoft-365/security/defender-endpoint/import-export-exploit-protection-emet-xml#use-group-policy-to-distribute-the-configuration)|
|**Włączanie ochrony sieci w** celu uniemożliwinia pracownikom korzystania z aplikacji zawierających złośliwą zawartość w Internecie <br/><br/> *Zalecamy używanie [najpierw trybu inspekcji](/microsoft-365/security/defender-endpoint/evaluate-network-protection) w celu ochrony sieci w środowisku testowym, aby sprawdzić, które aplikacje mogą być blokowane przed ich rozpoczęciem.*|[Włączanie ochrony sieci przy użyciu zasady grupy](/microsoft-365/security/defender-endpoint/enable-network-protection#group-policy)|
|**Konfigurowanie kontrolowanego dostępu do folderu w** celu ochrony przed oprogramowaniem wymuszającym okup <br/><br/> *[Kontrolowany dostęp do folderu](/microsoft-365/security/defender-endpoint/controlled-folders) jest również określany jako ochrona antyransomware.*|[Włączanie kontrolowanego dostępu do folderu przy użyciu zasady grupy](/microsoft-365/security/defender-endpoint/enable-controlled-folders#group-policy)|
|**Skonfiguruj Microsoft Defender SmartScreen**, aby chronić przed złośliwymi witrynami i plikami w Internecie.|[Konfigurowanie Microsoft Defender SmartScreen zasady grupy zarządzania urządzeniami przenośnymi przy użyciu funkcji zasady grupy](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings#group-policy-settings)|
|**Skonfiguruj szyfrowanie i funkcję BitLocker**, aby chronić informacje na urządzeniach w Twojej organizacji, na których działa Windows|[Ustawienia funkcji BitLocker zasady grupy funkcji BitLocker](/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings)|
|**Konfigurowanie usługi Microsoft Defender Credential Guard w** celu ochrony przed atakami kradzieży poświadczeń|[Włącz Windows Defender Credential Guard przy użyciu funkcji zasady grupy](/windows/security/identity-protection/credential-guard/credential-guard-manage#enable-windows-defender-credential-guard-by-using-group-policy)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Konfigurowanie portalu Microsoft 365 Defender sieciOwego

Jeśli jeszcze tego nie zrobiono, skonfiguruj w portalu usługi Microsoft 365 Defender wyświetlanie alertów, konfigurowanie funkcji ochrony przed zagrożeniami i wyświetlanie szczegółowych informacji o ogólnym stanie zabezpieczeń Twojej organizacji. Zobacz [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Możesz także skonfigurować funkcje, które użytkownicy końcowi będą widzieć w portalu Microsoft 365 Defender sieci.

- [Omówienie Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [Ochrona punktu końcowego: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Następne kroki

- [Omówienie funkcji Zarządzanie zagrożeniami i lukami](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Odwiedź pulpit nawigacyjny Microsoft 365 Defender zabezpieczeń portalu](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [Zarządzanie programem Microsoft Defender dla punktu końcowego za pomocą usługi Intune](manage-mde-post-migration-intune.md)
