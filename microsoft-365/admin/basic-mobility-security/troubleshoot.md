---
title: Rozwiązywanie problemów z podstawową mobilnością i zabezpieczeniami
f1.keywords: NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
description: Spróbuj wykonać poniższe czynności, aby śledzić problemy z podstawową mobilnością i zabezpieczeniami
ms.openlocfilehash: f625fbc642392ee575b35f225f5e65b942362c4a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983928"
---
# <a name="troubleshoot-basic-mobility-and-security"></a>Rozwiązywanie problemów z podstawową mobilnością i zabezpieczeniami

Jeśli masz problemy podczas próby zarejestrowania urządzenia w pakietach Basic Mobility and Security, wypróbuj opisane tu czynności w celu śledzenia problemu. Jeśli ogólne czynności nie rozwiązały problemu, zobacz jedną z sekcji poniżej z konkretną czynnością dla danego typu urządzenia.

## <a name="steps-to-try-first"></a>Czynności do wypróbowania

Aby rozpocząć, sprawdź następujące elementy:

- Upewnij się, że urządzenie nie zostało jeszcze zarejestrowane u innego dostawcy zarządzania urządzeniami przenośnymi, na przykład Intune.

- Upewnij się, że urządzenie ma ustawioną prawidłową datę i czas.

- Przełącz się do innej sieci WIFI lub komórkowej na urządzeniu.

- W przypadku urządzeń z systemem Android lub iOS odinstaluj i ponownie Intune — Portal firmy aplikację na urządzeniu. 

## <a name="ios-phone-or-tablet"></a>Telefon lub tablet z systemem iOS

- Upewnij się, że został ustawiony certyfikat usługi APN. Aby uzyskać więcej informacji, [zobacz Tworzenie certyfikatu usługi APN dla urządzeń z systemem iOS](create-an-apns-certificate-for-ios-devices.md).

- W  **Ustawienia** >  **GeneralProfile** >  **(lub Zarządzanie urządzeniami)** upewnij się, że profil zarządzania nie jest jeszcze zainstalowany. Jeśli jest, usuń go.

- Jeśli zostanie wyświetlony komunikat o błędzie "Urządzenie nie zostało zarejestrować", zaloguj się do usługi Microsoft 365 i upewnij się, że licencja na program Exchange Online została przypisana do użytkownika, który jest zalogowany na urządzeniu.

- Jeśli zostanie wyświetlony komunikat o błędzie "Nie można zainstalować profilu", spróbuj wykonać jedną z następujących czynności:

    - Upewnij się, że domyślną przeglądarką na urządzeniu jest Safari, a pliki cookie nie są wyłączone.

    - Uruchom ponownie urządzenie, a następnie przejdź do portal.manage.microsoft.com. Zaloguj się za pomocą Microsoft 365 identyfikatora użytkownika i hasła, a następnie spróbuj ręcznie zainstalować profil.

## <a name="windows-rt"></a>Windows RT

- Upewnij się, że Twoja domena jest Microsoft 365 na urządzeniach z pakietem Basic Mobility and Security. Aby uzyskać więcej informacji, zobacz [Konfigurowanie mobilności podstawowej i zabezpieczeń](set-up.md).
    
- Upewnij się, że użytkownik wybiera  **opcjęTurn Onrather** (Przywróć)  zamiast  **opcjiJoin (Dołącz**).

## <a name="windows-10-pc"></a>Windows 10 PC

- Upewnij się, że Twoja domena jest Microsoft 365 na urządzeniach z pakietem Basic Mobility and Security. Aby uzyskać więcej informacji, zobacz [Konfigurowanie mobilności podstawowej i zabezpieczeń](set-up.md).
    
- Jeśli nie masz Azure Active Directory — wersja Premium, upewnij się, że użytkownik wybiera  **opcjęEnroll in Device Management onlyrather**  than choosing  **Połączenie**.

## <a name="android-phone-or-tablet"></a>Telefon lub tablet z systemem Android

- Upewnij się, że na urządzeniu działa system Android 4.4 lub nowszy.

- Upewnij się, że przeglądarka Chrome jest aktualne i jest ustawiona jako domyślna przeglądarka.

- Jeśli zostanie wyświetlony komunikat o błędzie "Nie można zarejestrować tego urządzenia", zaloguj się do usługi Microsoft 365 i upewnij się, że licencja na program Exchange Online została przypisana do użytkownika, który jest zalogowany na urządzeniu.

- Sprawdź w obszarze powiadomień na urządzeniu, czy są oczekujące wymagane akcje użytkownika końcowego, a jeśli tak, wykonaj je.