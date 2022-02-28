---
title: Funkcje ochrony w usłudze Azure Information Protection są obecnie dostępne w istniejących dzierżawach
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
description: W tym artykule wyjaśniono zmiany wprowadzone w funkcjach ochrony w usłudze Azure Information Protection
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a11821e6c2165c79e286612b89d42f7e19b1593d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988355"
---
# <a name="protection-features-in-azure-information-protection-rolling-out-to-existing-tenants"></a>Funkcje ochrony w usłudze Azure Information Protection są obecnie dostępne w istniejących dzierżawach

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Aby ułatwić początkowy krok w zakresie ochrony informacji, od lipca 2018 r. wszystkie dzierżawy kwalifikujące się do usługi Azure Information Protection będą domyślnie włączone funkcje ochrony w usłudze Azure Information Protection. Funkcje ochrony w usłudze Azure Information Protection były wcześniej znane w programie Office 365 jako zarządzanie prawami dostępu lub usługa Azure RMS. Jeśli Twoja organizacja ma plan usługi Office E3 lub wyższy plan usługi, po wdowy tych funkcjach zacznij chronić informacje za pośrednictwem usługi Azure Information Protection.

## <a name="changes-beginning-july-1-2018"></a>Zmiany od 1 lipca 2018 r.

Począwszy od 1 lipca 2018 r., firma Microsoft włączy funkcję ochrony w usłudze Azure Information Protection dla wszystkich organizacji, które mają jeden z następujących planów subskrypcji:

- Szyfrowanie wiadomości usługi Office 365 jest oferowana w ramach usług Office 365 E3 i E5, Microsoft E3 i E5, Office 365 A1, A3 i A5 oraz Office 365 G3 i G5. Nie potrzebujesz dodatkowych licencji, aby uzyskać nowe funkcje ochrony obsługiwane przez usługę Azure Information Protection.

- Możesz również dodać plan 1 usługi Azure Information Protection do następujących planów, aby uzyskać nowe funkcje usługi Szyfrowanie wiadomości usługi Office 365: Exchange Online Plan 1, Exchange Online Plan 2, Office 365 F1, Microsoft 365 Business Basic, Microsoft 365 Business Standard lub Office 365 Enterprise E1.

- Każdy użytkownik, który korzysta Szyfrowanie wiadomości usługi Office 365 musi posiadać licencję, aby ta funkcja została objęta funkcją.

- Aby uzyskać pełną listę, zobacz [opisy Exchange Online usługi w](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description) Szyfrowanie wiadomości usługi Office 365.

Administratorzy dzierżawy mogą sprawdzać stan ochrony w portalu Office 365 administratorów.

![Zrzut ekranu przedstawiający aktywowanie zarządzania prawami w Office 365 sieci.](../../media/303453c8-e4a5-4875-b49f-e80c3eb7b91e.png)

## <a name="why-are-we-making-this-change"></a>Dlaczego taka zmiana jest w tej zmianie?

Szyfrowanie wiadomości usługi Office 365 wykorzystuje funkcje ochrony w usłudze Azure Information Protection. W związku z ostatnimi ulepszeniami programu Szyfrowanie wiadomości usługi Office 365 i naszymi szerszymi inwestycjami w ochronę informacji w programie Microsoft 365 ułatwiamy organizacjom włączanie i używanie naszych możliwości ochrony, ponieważ historyczne technologie szyfrowania były trudne do skonfigurowania. Włączając domyślnie funkcje ochrony w usłudze Azure Information Protection, możesz szybko zacząć chronić poufne dane.

## <a name="does-this-impact-me"></a>Czy to na mnie wpływa?

Jeśli Twoja organizacja zakupiła uprawniawą licencję usługi Office 365, ta zmiana wpłynie na Twoją dzierżawę.

> [!IMPORTANT]
> Jeśli korzystasz z usługi Usługi Active Directory Rights Management (AD RMS) w środowisku lokalnym, musisz natychmiast zrezygnować z tej zmiany lub zmigrować do usługi Azure Information Protection, zanim będziemy wdać tę zmianę w ciągu następnych 30 dni. Aby uzyskać informacje na temat sposobu rezygnacji, zobacz "Korzystam z usług AD RMS, jak zrezygnować?". w dalszej części tego artykułu. Jeśli wolisz przeprowadzić migrację, zobacz [Migrowanie z usług AD RMS do usługi Azure Information Protection](/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms).

## <a name="can-i-use-azure-information-protection-with-active-directory-rights-management-services-ad-rms"></a>Czy mogę używać usługi Azure Information Protection z usługą Usługi Active Directory Rights Management (AD RMS)?

L.p. Nie jest to obsługiwany scenariusz wdrażania. Bez dodatkowych kroków rezygnacji niektóre komputery mogą automatycznie zacząć korzystać z usługi Azure Rights Management i nawiązać połączenie z klasterem usług AD RMS. Ten scenariusz nie jest obsługiwany i jego wyniki są zawodne, dlatego należy zrezygnować z tej zmiany w ciągu 30 dni przed rozpoczęciem działania tych nowych funkcji. Aby uzyskać informacje na temat sposobu rezygnacji, zobacz "Korzystam z usług AD RMS, jak zrezygnować?". w dalszej części tego artykułu. Jeśli wolisz przeprowadzić migrację, zobacz [Migrowanie z usług AD RMS do usługi Azure Information Protection.](/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms)

## <a name="how-do-i-know-if-im-using-ad-rms"></a>Jak sprawdzić, czy korzystam z usług AD RMS?

Skorzystaj z poniższych instrukcji z przygotowywanie środowiska do korzystania z usługi [Azure Rights Management](/azure/information-protection/deploy-use/prepare-environment-adrms), gdy masz również usługę ad rms w celu sprawdzenia, czy usługi AD RMS Usługi Active Directory Rights Management wdrożono:

1. Mimo że jest to opcjonalne, większość wdrożeń usług AD RMS publikuje punkt połączenia usługi (SCP) w usłudze Active Directory, aby komputery domeny wykrywały klaster usług AD RMS.

   Użyj edycji ADSI, aby sprawdzić, czy w usłudze Active Directory opublikowano SCP: CN=Configuration [nazwa serwera], CN=Services, CN=RightsManagementServices, CN=SCP

2. Jeśli nie używasz oznaczania SCP, komputery Windows, które łączą się z klastrem USŁUG AD RMS, muszą być skonfigurowane do odnajdowania usług po stronie klienta lub przekierowywania licencjonowania przy użyciu rejestru usługi Windows: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC\ServiceLocation`.

Aby uzyskać więcej informacji o tych konfiguracjach rejestru, zobacz Włączanie odnajdowania usługi po stronie klienta przy Windows [rejestru](/azure/information-protection/rms-client/client-deployment-notes#enabling-client-side-service-discovery-by-using-the-windows-registry) i [Przekierowywanie ruchu serwera licencji](/azure/information-protection/rms-client/client-deployment-notes#redirecting-licensing-server-traffic).

## <a name="i-use-ad-rms-how-do-i-opt-out"></a>Jak zrezygnować z usług AD RMS?

Aby zrezygnować z nadchodzącej zmiany, wykonaj następujące czynności:

1. Korzystając z konta służbowego z uprawnieniami administratora globalnego w Twojej organizacji, rozpocznij sesję Windows PowerShell i połącz się z Exchange Online. Aby uzyskać instrukcje, [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Uruchom Set-IRMConfiguration cmdlet programu Set-IRMConfiguration przy użyciu następującej składni:

  ```powershell
  Set-IRMConfiguration -AutomaticServiceUpdateEnabled $false
  ```

## <a name="what-can-i-expect-after-this-change-has-been-made"></a>Czego mogę się spodziewać po w związku z tą zmianą?

Jeśli ta funkcja zostanie włączona, o ile nie zrezygnuje się z tej funkcji, możesz zacząć korzystać z nowej wersji programu Szyfrowanie wiadomości usługi Office 365, która została ogłoszona na konferencji [Microsoft Ignite 2017](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801) i korzysta z funkcji szyfrowania i ochrony usługi Azure Information Protection.

![Zrzut ekranu przedstawiający wiadomość chronioną za pomocą OME w aplikacji Outlook w sieci Web.](../../media/599ca9e7-c05a-429e-ae8d-359f1291a3d8.png)

Aby uzyskać więcej informacji na temat nowych ulepszeń, zobacz [Szyfrowanie wiadomości usługi Office 365](../../compliance/ome.md).