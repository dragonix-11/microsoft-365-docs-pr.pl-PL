---
title: Zalecenia dotyczące zasad dotyczących haseł
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9fa2539a-2211-41fd-85a0-bc37b9619ca4
description: Zwiększaj bezpieczeństwo organizacji przed atakami haseł, a także zakaż popularne hasła i włącz oparte na ryzyko uwierzytelnianie wieloskładnikowe.
ms.openlocfilehash: a77d6a157c3691739ee7f5a024796f1f203241e8
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019257"
---
# <a name="password-policy-recommendations"></a>Zalecenia dotyczące zasad dotyczących haseł

Jako administrator organizacji, odpowiadasz za konfigurowanie zasad haseł dla użytkowników w organizacji. Ustawienie zasad dotyczących haseł może być skomplikowane i skomplikowane, a w tym artykule przedstawiono zalecenia dotyczące zabezpieczania organizacji przed atakami hasła.
  
Aby określić, jak często Microsoft 365 wygasają hasła w organizacji, zobacz Ustawianie zasad wygasania [haseł dla konta Microsoft 365](../manage/set-password-expiration-policy.md).

Aby uzyskać więcej informacji na Microsoft 365 haseł, zobacz:

[Resetowanie haseł](../add-users/reset-passwords.md) (artykuł)

[Konfigurowanie hasła pojedynczego użytkownika tak, aby nigdy nie wygasło](../add-users/set-password-to-never-expire.md) (artykuł)

[Umożliwianie użytkownikom resetowania swoich haseł](../add-users/let-users-reset-passwords.md) (artykuł)

[Ponowne wysyłanie hasła użytkownika — Pomoc dla administratorów](../add-users/resend-user-password.md) (artykuł)
  
## <a name="understanding-password-recommendations"></a>Zrozumienie zaleceń dotyczących haseł

Dobre praktyki dotyczące haseł można podzielić na kilka ogólnych kategorii:
  
- **Zadbanie o odporność na typowe ataki** Obejmuje to wybór miejsc, w których użytkownicy wprowadzają hasła (znane i zaufane urządzenia wyposażone w skuteczne mechanizmy wykrywania złośliwego oprogramowania, zweryfikowane strony) oraz dobór odpowiedniego hasła (długość i niepowtarzalność).

- **Ograniczanie strat w przypadku skutecznych ataków** Ograniczanie strat w przypadku skutecznych ataków hakerów polega na ograniczaniu narażenia do konkretnej usługi lub całkowite uniknięcie strat, jeżeli hasło użytkownika zostanie skradzione. Na przykład warto się upewnić, czy przechwycenie Twoich danych uwierzytelniających do sieci społecznościowej nie wpłynie na bezpieczeństwo Twojego konta bankowego, lub zapobiegać akceptowaniu przez słabo zabezpieczone konta łączy do resetowania hasła na ważnym koncie.

- **Zrozum naturę ludzką** Wiele dobrych praktyk w zakresie haseł zawodzi w starciu z naturalnymi ludzkimi zachowaniami. Zrozumienie ludzkiej natury ma kluczowe znaczenie, ponieważ z badań wynika, że niemal każda zasada, którą narzucisz użytkownikom, spowoduje pogorszenie jakości haseł. Wymagania dotyczące długości, stosowania znaków specjalnych i zmian haseł powodują ujednolicenie haseł, co sprawia, że intruzom łatwiej jest je odgadnąć lub złamać.

## <a name="password-guidelines-for-administrators"></a>Wskazówki dla administratorów dotyczące haseł

Aby system był bezpieczniejszy, hasła powinny być przede wszystkim bardziej zróżnicowane. Warto dążyć do tego, aby Twoje zasady dotyczące haseł zawierały wiele różnych i trudnych do odgadnięcia haseł. Oto kilka zaleceń dotyczących utrzymania jak najwyższego poziomu zabezpieczeń w organizacji.
  
- Zachowywanie wymagania minimalnej długości 8 znaków

- Nie wprowadzaj wymogów dotyczących wymaganych znaków. Na przykład \*&amp;(^%$.

- Nie wymagaj okresowego obowiązkowego resetowania haseł do kont użytkowników.

- Zabroń korzystania z typowych haseł w celu wyeliminowania najłatwiejszych do złamania haseł.

- Informacje dla użytkowników, aby nie ponownie używać haseł organizacji do celów niezwiązywnych z pracą

- Wymuś korzystanie z [uwierzytelniania wieloskładnikowego](../security-and-compliance/set-up-multi-factor-authentication.md).

- Włącz weryfikacje przeprowadzane w oparciu o ocenę ryzyka w uwierzytelnianiu wieloskładnikowym.

### <a name="password-guidance-for-your-users"></a>Wskazówki dotyczące haseł dla Twoich użytkowników

Oto kilka wskazówek dotyczących haseł dla użytkowników w Twojej organizacji. Zadbaj o to, aby użytkownicy znali te zalecenia i egzekwuj stosowanie się do zalecanych zasad dotyczących haseł na poziomie organizacji.
  
- Nie używaj hasła podobnego do używanego w innych witrynach internetowych lub takiego samego.

- Nie używaj pojedynczego wyrazu, na przykład **hasła ani często** używanej frazy, takiej jak **Iloveyou**

- Postaraj się, aby hasło było trudne do odgadnięcia, nawet dla osób, które dobrze Cię znają. Nie używaj imion i dat urodzin swoich przyjaciół i rodziny, nazw ulubionych zespołów lub swoich typowych zwrotów.

## <a name="some-common-approaches-and-their-negative-impacts"></a>Przykłady typowego podejścia i jego negatywne skutki

Poniżej opisujemy jedne z najczęściej stosowanych praktyk w zakresie zarządzania hasłami, które według badań mogą mieć negatywne skutki.
  
### <a name="password-expiration-requirements-for-users"></a>Obowiązkowe wygasanie haseł

Wymagania dotyczące wygasania haseł są bardziej szkodliwe, ponieważ te wymagania sprawiają, że użytkownicy będą wybierać przewidywalne hasła składające się z sekwencyjnych wyrazów i liczb, które są ze sobą ściśle powiązane. W takich przypadkach kolejne hasło można przewidzieć na podstawie poprzedniego hasła. Wymagania dotyczące wygasania haseł nie oferują korzyści związanych z zawieraniem hasła, ponieważ cyberprzestępcy prawie zawsze używają poświadczeń w momencie ich naruszenia. Aby uzyskać [więcej informacji, zobacz Czas na sprawdzenie obowiązkowych zmian](https://go.microsoft.com/fwlink/p/?linkid=861018) hasła.
  
### <a name="requiring-long-passwords"></a>Wymóg stosowania długich haseł

Wymóg stosowania długich haseł (dłuższych niż 10 znaków) może spowodować, że użytkownicy będą zachowywać się w przewidywalny i niepożądany sposób. Na przykład użytkownicy, od których oczekuje się stosowania hasła złożonego z 16 znaków, mogą zdecydować się na użycie powtarzających się słów, np. **trzytrzytrzytrzy** lub **czwartekczwartek**, aby spełnić wymóg długości. Takie hasła nie są jednak trudne do odgadnięcia. Ponadto wymagania dotyczące długości zwiększają szanse na przyjęcie przez użytkowników innych niezabezpieczonych rozwiązań, takich jak zapisywanie haseł, ponowne ich użycie lub przechowywanie w dokumentach niezaszyfrowane. W celu zachęcenia użytkowników do wymyślenia niepowtarzalnego hasła zalecamy zachowanie rozsądnego wymogu minimalnej długości wynoszącej 8 znaków.
  
### <a name="requiring-the-use-of-multiple-character-sets"></a>Wymóg stosowania różnych rodzajów znaków

Wymogi dotyczące złożoności ograniczają dostępne miejsce i powodują, że użytkownicy postępują w przewidywalny sposób, co przynosi więcej szkody niż pożytku. W większości systemów obowiązują pewne wymogi dotyczące złożoności haseł. Na przykład hasło musi składać się ze znaków ze wszystkich trzech poniższych kategorii:
  
- wielkie litery;

- małe litery;

- znaki niealfanumeryczne.

Większość osób używa podobnych wzorców, na przykład wielka litera na pierwszej pozycji, symbol na ostatniej i numer w jednej z dwóch ostatnich pozycji. Cyberprzestępcy wiedzą o tym, więc uruchamiają swoje ataki słowników, używając najpopularniejszych podstawiania "$" dla "s", "@" dla "a", "1" dla "l". Nakładanie na użytkowników obowiązku używania kombinacji wielkich i małych liter, cyfr i znaków specjalnych ma negatywny efekt. Zastosowanie niektórych wymogów dotyczących złożoności uniemożliwia nawet użytkownikom korzystanie z bezpiecznych i łatwych do zapamiętania haseł, a także zmusza ich do wymyślania takich, które będą mniej bezpieczne i trudniejsze do zapamiętania.
  
## <a name="successful-patterns"></a>Skuteczne wzorce

Teraz omówimy zalecenia, które sprzyjają stosowaniu zróżnicowanych haseł.
  
### <a name="ban-common-passwords"></a>Wyklucz korzystanie z typowych haseł

Najistotniejszym wymogiem, który użytkownicy powinni spełnić, tworząc swoje hasła, jest zakaz stosowania typowych haseł, aby ograniczyć podatność organizacji na brutalne ataki polegające na łamaniu haseł. Typowe hasła użytkowników to: **abcdefg**, **hasło**, **małpa**.
  
### <a name="educate-users-to-not-reuse-organization-passwords-anywhere-else"></a>Ułagodnianie użytkownikom ponownego używania haseł organizacji w innych miejscach

Jednym z najważniejszych komunikatów, które należy należy uzyskać od użytkowników w organizacji, jest to, aby nie używać ich ponownie w innych miejscach. Korzystanie z haseł organizacji w witrynach zewnętrznych znacznie zwiększa prawdopodobieństwo naruszenia tych haseł przez cyberprzestępców.
  
### <a name="enforce-multi-factor-authentication-registration"></a>Egzekwuj korzystanie z uwierzytelnienia wieloskładnikowego

Zadbaj o to, aby użytkownicy aktualizowali informacje kontaktowe i dotyczące bezpieczeństwa, takie jak alternatywny adres e-mail, numer telefonu lub urządzenie zarejestrowane na potrzeby powiadomień push. Dzięki temu będą mogli odpowiadać na komunikaty zabezpieczające i otrzymywać powiadomienia o zdarzeniach związanych z zabezpieczeniami. Aktualne dane kontaktowe i informacje dotyczące bezpieczeństwa ułatwiają użytkownikom zweryfikowanie ich tożsamości, jeżeli zdarzy im się zapomnieć hasło lub ktoś inny spróbuje przejąć ich konto. Dzięki nim użytkownicy dysponują również zapasowym kanałem wysyłania powiadomień, z którego można skorzystać w razie wystąpienia zdarzeń związanych z zabezpieczeniami np. prób logowania lub zmiany hasła. 
  
Aby dowiedzieć się więcej, przeczytaj artykuł [Konfigurowanie uwierzytelniania wieloskładnikowego](../security-and-compliance/set-up-multi-factor-authentication.md).
  
### <a name="enable-risk-based-multi-factor-authentication"></a>Włączanie uwierzytelniania wieloskładnikowego opartego o ocenę ryzyka

Dzięki uwierzytelnianiu wieloskładnikowemu opartemu o ocenę ryzyka możemy mieć pewność, że gdy system wykryje podejrzaną aktywność, zweryfikuje tożsamość użytkownika, aby upewnić się, że jest prawowitym właścicielem konta. 
  
## <a name="next-steps"></a>Następne kroki

Chcesz dowiedzieć się więcej o zarządzaniu hasłami? Oto kilka polecanych opisów:

- [Zapomnij hasła, nie hasło](https://www.microsoft.com/security/business/identity-access-management/passwordless-authentication)

- [Wskazówki dotyczące haseł firmy Microsoft](https://www.microsoft.com/research/wp-content/uploads/2016/06/Microsoft_Password_Guidance-1.pdf)

- [Do Strong Web Passwords Accomplish Anything? (Czy silne hasła w sieci są skuteczne?)](https://go.microsoft.com/fwlink/p/?linkid=861008)

- [Password Portfolios and the Finite-Effort User (Portfolio haseł i użytkownik, który nie chce się przesadnie wysilać)](https://go.microsoft.com/fwlink/p/?linkid=861014)

- [Preventing Weak Passwords by Reading Users' Minds (Zapobieganie stosowaniu słabych haseł poprzez czytanie w myślach użytkowników)](https://go.microsoft.com/fwlink/p/?linkid=861015)

- [Choosing Secure Passwords (Wybór bezpiecznych haseł)](https://go.microsoft.com/fwlink/p/?linkid=861016)

- [Time to rethink mandatory password changes (Czas przemyśleć obowiązkowe zmiany haseł)](https://go.microsoft.com/fwlink/p/?linkid=861018)

- [Worst Passwords of 2015 (Najgorsze hasła 2015 r.)](https://go.microsoft.com/fwlink/p/?linkid=861020)

## <a name="related-content"></a>Zawartość pokrewna

[Resetowanie haseł](../add-users/reset-passwords.md) (artykuł)\
[Ustawianie hasła pojedynczego użytkownika tak, aby nigdy nie wygasło](../add-users/set-password-to-never-expire.md) (artykuł)\
[Umożliwianie użytkownikom resetowania swoich haseł](../add-users/let-users-reset-passwords.md) (artykuł)\
[Ponowne wysyłanie hasła użytkownika — Pomoc dla administratorów](../add-users/resend-user-password.md) (artykuł)
