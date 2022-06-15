---
title: Omówienie profilów rozliczeniowych
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: amberb, vikdesai
audience: Admin
ms.topic: article
f1.keywords:
- MACBillingBillsPaymentsBillingProfiles
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_billing
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid: MET150
description: Dowiedz się, jak profile rozliczeniowe obsługują faktury.
ms.date: 04/02/2021
ms.openlocfilehash: 92c8bd302d65bc9f7c9376ac148fd49a0ac18e04
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102553"
---
# <a name="understand-billing-profiles"></a>Omówienie profilów rozliczeniowych

Profil rozliczeniowy zawiera formę płatności, informacje o rozliczeniu i inne ustawienia faktury, takie jak numer zamówienia zakupu i preferencje dotyczące faktury e-mail. Profil rozliczeniowy służy do płacenia za produkty kupowane od firmy Microsoft. Profil rozliczeniowy jest tworzony automatycznie, gdy użytkownik dokonuje zakupu samoobsługowego. Każdy profil rozliczeniowy jest fakturowane oddzielnie.

> [!NOTE]
>
> Profile rozliczeniowe nie są dostępne dla klientów, którzy kupują produkty i usługi od Microsoft.com lub na stronie **Zakup usług** Centrum administracyjne platformy Microsoft 365.

## <a name="what-are-billing-profile-roles"></a>Co to są role profilu rozliczeniowego?

Role w profilach rozliczeniowych mają uprawnienia do kontrolowania zakupów oraz wyświetlania faktur i zarządzania nimi. Przypisz te role użytkownikom, którzy śledzą, organizują i płacą faktury. Na przykład członkowie zespołu ds. zamówień w organizacji.

| Rola                         | Opis                                                                      |
|----------------------------- |--------------------------------------------------------------------------------- |
| Właściciel profilu rozliczeniowego        | Zarządzanie wszystkimi elementami profilu rozliczeniowego                                          |
| Współautor profilu rozliczeniowego  | Zarządzanie wszystkim z wyjątkiem uprawnień w profilu rozliczeniowym                        |
| Czytelnik profilu rozliczeniowego       | Widok tylko do odczytu wszystkich elementów w profilu rozliczeniowym                                |
| Menedżer faktur              | Wyświetlanie i płacenie rachunków oraz widok tylko do odczytu wszystkich elementów w profilu rozliczeniowym  |

## <a name="view-my-billing-profiles"></a>Wyświetlanie profilów rozliczeniowych

> [!NOTE]
>
> Jeśli wykonajesz te kroki, a lista profilów rozliczeniowych jest pusta, oznacza to, że nie masz profilu rozliczeniowego i nie możesz korzystać z tej funkcji.

1. W centrum administracyjnym przejdź do strony **Rachunki** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">Rachunki i płatności</a>.
2. Wybierz kartę **Profil rozliczeniowy** , a następnie wybierz z listy profil rozliczeniowy.

Każdy profil rozliczeniowy zawiera następujące informacje:

- **Nazwa i stan** &ndash; profilu rozliczeniowego Unikatowa nazwa profilu rozliczeniowego oraz to, czy profil rozliczeniowy jest aktywny, czy wyłączony w przypadku zakupu.
- **Ustawienia faktury** &ndash; Waluta na podstawie kraju konta rozliczeniowego, informacji o częstotliwości i dacie faktury, opcji otrzymywania faktur jako załączników wiadomości e-mail oraz opcjonalnego pola numeru zamówienia zakupu
- **Formy** &ndash; płatności Pokazuje podstawową i zapasową formę płatności dla profilu, jeśli istnieje
- **Konto** &ndash; rozliczeniowe Nazwa konta rozliczeniowego, z którego jest powiązany profil. Aby uzyskać więcej informacji na temat kont rozliczeniowych, zobacz [Omówienie kont rozliczeniowych](../manage-billing-accounts.md).
- **Informacje** &ndash; kontaktowe Adres rozliczeniowy oraz nazwa kontaktu i adres e-mail
- Role &ndash; **profilu rozliczeniowego** Lista osób, do których przypisano jedną z ról profilu rozliczeniowego, aby wykonywać zadania dla tego profilu. Na przykład zapłać rachunki, dodaj numer zamówienia zakupu lub zastąp formę płatności używaną do dokonywania zakupów.

> [!NOTE]
>
> Role profilu rozliczeniowego można przypisywać tylko do użytkowników w organizacji.

## <a name="need-help-contact-support"></a>Potrzebujesz pomocy? Kontakt z pomocą techniczną

Jeśli masz pytania lub potrzebujesz pomocy dotyczącej opłat za korzystanie z platformy Azure, <a href="https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest" target="_blank">utwórz wniosek o pomoc techniczną z pomoc techniczna platformy Azure</a>.

Jeśli masz pytania lub potrzebujesz pomocy dotyczącej profilu rozliczeniowego w Centrum administracyjne platformy Microsoft 365, [skontaktuj się z pomocą techniczną](../../admin/get-help-support.md).

## <a name="related-content"></a>Zawartość pokrewna

[Jak płacić za subskrypcję za pomocą profilu rozliczeniowego](pay-for-subscription-billing-profile.md) (artykuł)\
[Omówienie kont rozliczeniowych](../manage-billing-accounts.md) (artykuł)\
[Zarządzanie formami płatności](manage-payment-methods.md) (artykuł)
