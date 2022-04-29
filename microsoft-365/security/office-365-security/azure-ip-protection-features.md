---
title: Funkcje ochrony na platformie Azure Information Protection wdrażane w istniejących dzierżawach
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 7ad6f58e-65d7-4c82-8e65-0b773666634d
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: W tym artykule wyjaśniono zmiany wprowadzane w funkcjach ochrony w usłudze Azure Information Protection
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: dbfc21b879745567c9273c79356ff60e498d95ff
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130829"
---
# <a name="protection-features-in-azure-information-protection-rolling-out-to-existing-tenants"></a>Funkcje ochrony na platformie Azure Information Protection wdrażane w istniejących dzierżawach

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Aby ułatwić początkowy krok ochrony informacji, od lipca 2018 r. wszystkie kwalifikujące się dzierżawy Information Protection platformy Azure będą mieć domyślnie włączone funkcje ochrony na platformie Azure Information Protection. Funkcje ochrony w usłudze Azure Information Protection były wcześniej znane w Office 365 jako usługa Rights Management lub Azure RMS. Jeśli Twoja organizacja ma Office plan usługi E3 lub wyższy plan usługi, uzyskasz teraz początek ochrony informacji za pośrednictwem usługi Azure Information Protection podczas wdrażania tych funkcji.

## <a name="changes-beginning-july-1-2018"></a>Zmiany rozpoczynające się 1 lipca 2018 r.

Od 1 lipca 2018 r. firma Microsoft włączy możliwość ochrony w usłudze Azure Information Protection dla wszystkich organizacji z jednym z następujących planów subskrypcji:

- Office 365 szyfrowanie komunikatów jest oferowane w ramach Office 365 E3 i E5, Microsoft E3 i E5, Office 365 A1, A3 i A5 oraz Office 365 G3 i G5. Nie potrzebujesz dodatkowych licencji, aby otrzymywać nowe możliwości ochrony obsługiwane przez usługę Azure Information Protection.

- Możesz również dodać usługę Azure Information Protection Plan 1 do następujących planów, aby otrzymać nowe funkcje szyfrowania komunikatów Office 365: Exchange Online plan 1, Exchange Online plan 2, Office 365 F1, Microsoft 365 Business Basic, Microsoft 365 Business Standard lub Office 365 Enterprise E1.

- Każdy użytkownik korzystający z Office 365 szyfrowania komunikatów musi mieć licencję, aby był objęty funkcją.

- Aby uzyskać pełną listę, zobacz [opisy usługi Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description) dotyczące szyfrowania komunikatów Office 365.

Administratorzy dzierżawy mogą sprawdzić stan ochrony w portalu administratora Office 365.

:::image type="content" source="../../media/303453c8-e4a5-4875-b49f-e80c3eb7b91e.png" alt-text="Zarządzanie prawami w Office 365, które jest aktywowane" lightbox="../../media/303453c8-e4a5-4875-b49f-e80c3eb7b91e.png":::

## <a name="why-are-we-making-this-change"></a>Dlaczego wprowadzamy tę zmianę?

Office 365 szyfrowanie komunikatów korzysta z możliwości ochrony w usłudze Azure Information Protection. Sednem ostatnich ulepszeń Office 365 szyfrowania komunikatów i naszych szerszych inwestycji w ochronę informacji w Microsoft 365 jest ułatwienie organizacjom włączania i korzystania z naszych możliwości ochrony, ponieważ historycznie trudno było skonfigurować technologie szyfrowania. Domyślnie włączając funkcje ochrony na platformie Azure Information Protection, możesz szybko rozpocząć ochronę poufnych danych.

## <a name="does-this-impact-me"></a>Czy to ma na mnie wpływ?

Jeśli Twoja organizacja zakupiła kwalifikującą się licencję Office 365, ta zmiana będzie mieć wpływ na dzierżawę.

> [!IMPORTANT]
> Jeśli używasz Usługi Active Directory Rights Management (AD RMS) w środowisku lokalnym, musisz natychmiast zrezygnować z tej zmiany lub przeprowadzić migrację do usługi Azure Information Protection, zanim wdrożymy tę zmianę w ciągu najbliższych 30 dni. Aby uzyskać informacje na temat sposobu rezygnacji, zobacz "Jak mogę zrezygnować z korzystania z usług AD RMS?" w dalszej części tego artykułu. Jeśli wolisz migrować, zobacz [Migrowanie z usług AD RMS do usługi Azure Information Protection.](/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms).

## <a name="can-i-use-azure-information-protection-with-active-directory-rights-management-services-ad-rms"></a>Czy mogę używać usługi Azure Information Protection z usługą Usługi Active Directory Rights Management (AD RMS)?

Nie. Nie jest to obsługiwany scenariusz wdrażania. Bez wykonywania dodatkowych kroków rezygnacji niektóre komputery mogą automatycznie zacząć korzystać z usługi Azure Rights Management, a także łączyć się z klastrem usług AD RMS. Ten scenariusz nie jest obsługiwany i ma niewiarygodne wyniki, dlatego ważne jest, aby zrezygnować z tej zmiany w ciągu najbliższych 30 dni przed wdrożeniem tych nowych funkcji. Aby uzyskać informacje na temat sposobu rezygnacji, zobacz "Jak mogę zrezygnować z korzystania z usług AD RMS?" w dalszej części tego artykułu. Jeśli wolisz migrować, zobacz [Migrowanie z usług AD RMS do usługi Azure Information Protection.](/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms)

## <a name="how-do-i-know-if-im-using-ad-rms"></a>Jak mogę wiem, czy używam usług AD RMS?

Skorzystaj z tych instrukcji z [artykułu Przygotowywanie środowiska dla usługi Azure Rights Management, gdy masz również Usługi Active Directory Rights Management (AD RMS),](/azure/information-protection/deploy-use/prepare-environment-adrms) aby sprawdzić, czy wdrożono usługę AD RMS:

1. Chociaż jest to opcjonalne, większość wdrożeń usług AD RMS publikuje punkt połączenia usługi (SCP) w usłudze Active Directory, aby komputery domeny mogły odnajdywać klaster usług AD RMS.

   Użyj narzędzia ADSI Edit, aby sprawdzić, czy w usłudze Active Directory opublikowano protokół SCP: CN=Configuration [nazwa serwera], CN=Services, CN=RightsManagementServices, CN=SCP

2. Jeśli nie używasz protokołu SCP, Windows komputery łączące się z klastrem usług AD RMS muszą być skonfigurowane do odnajdywania usług po stronie klienta lub przekierowywania licencjonowania przy użyciu rejestru Windows: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC\ServiceLocation`.

Aby uzyskać więcej informacji na temat tych konfiguracji rejestru, zobacz [Włączanie odnajdywania usługi po stronie klienta przy użyciu rejestru Windows](/azure/information-protection/rms-client/client-deployment-notes#enabling-client-side-service-discovery-by-using-the-windows-registry) i [przekierowywania ruchu serwera licencjonowania](/azure/information-protection/rms-client/client-deployment-notes#redirecting-licensing-server-traffic).

## <a name="i-use-ad-rms-how-do-i-opt-out"></a>Jak mogę zrezygnować z korzystania z usług AD RMS?

Aby zrezygnować z nadchodzącej zmiany, wykonaj następujące kroki:

1. Korzystając z konta służbowego z uprawnieniami administratora globalnego w organizacji, rozpocznij sesję Windows PowerShell i połącz się z Exchange Online. Aby uzyskać instrukcje, zobacz [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Uruchom polecenie cmdlet Set-IRMConfiguration przy użyciu następującej składni:

  ```powershell
  Set-IRMConfiguration -AutomaticServiceUpdateEnabled $false
  ```

## <a name="what-can-i-expect-after-this-change-has-been-made"></a>Czego mogę oczekiwać po wprowadzeniu tej zmiany?

Po włączeniu tej opcji, pod warunkiem, że nie zrezygnujesz, możesz zacząć korzystać z nowej wersji szyfrowania komunikatów Office 365, która została ogłoszona na [konferencji Microsoft Ignite 2017](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801), i korzystać z funkcji szyfrowania i ochrony usługi Azure Information Protection.

:::image type="content" source="../../media/599ca9e7-c05a-429e-ae8d-359f1291a3d8.png" alt-text="Chroniony komunikat OME w Outlook w sieci Web" lightbox="../../media/599ca9e7-c05a-429e-ae8d-359f1291a3d8.png":::

Aby uzyskać więcej informacji na temat nowych ulepszeń, zobacz [Office 365 Szyfrowanie komunikatów](../../compliance/ome.md).
