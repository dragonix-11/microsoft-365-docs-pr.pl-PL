---
title: Co nowego w Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux
description: Lista najważniejszych zmian dotyczących Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, linux, whatsnew, release
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: reference
ms.technology: mde
ms.openlocfilehash: ea99a46d468e6c3d5e7346006da0eb24116067d0
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66489952"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-linux"></a>Co nowego w Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 


Ten artykuł jest często aktualizowany w celu poinformowania o nowościach w najnowszych wersjach Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux. 

- [Co nowego w usłudze Defender for Endpoint w systemie macOS](mac-whatsnew.md)
- [Co nowego w usłudze Defender for Endpoint w systemie iOS](ios-whatsnew.md)

<details>
  <summary>Czerwiec 2022 r. (kompilacja: 101.71.18 | Wersja wydania: 30.122052.17118.0)</summary>

&ensp;Data wydania: **24 czerwca 2022 r**.<br/>
&ensp;Opublikowano: **24 czerwca 2022 r**.<br/>
&ensp;Kompilacja: **101.71.18**<br/>
&ensp;Wersja wydania: **30.122042.16880.0**<br/>


**Co nowego**

- Rozwiązano problem z czujnikiem produktu używanym w systemie RHEL 6, który mógł prowadzić do zawieszenia systemu operacyjnego
- `mdatp connectivity test` został rozszerzony o dodatkowy adres URL, który produkt wymaga poprawnego działania. Nowy adres URL to [https://go.microsoft.com/fwlink/?linkid=2144709](https://go.microsoft.com/fwlink/?linkid=2144709).
- Do tej pory poziom dziennika produktu nie był utrwalany między ponownym uruchomieniem produktu. Począwszy od tej wersji, istnieje nowy przełącznik narzędzia wiersza polecenia, który utrwala poziom dziennika. Nowe polecenie to `mdatp log level persist --level <level>`.
- Usunięto zależność `python` od pakietu instalacyjnego produktu
- Ulepszenia wydajności operacji kopiowania plików i przetwarzania zdarzeń sieciowych pochodzących z `auditd`
- Poprawki błędów
</br>

<br/><br/>
</details>


<details>
  <summary>Maj-2022 r. (kompilacja: 101.68.80 | Wersja wydania: 30.122042.16880.0)</summary>

&ensp;Data wydania: **23 maja 2022 r**.<br/>
&ensp;Opublikowano: **23 maja 2022 r**.<br/>
&ensp;Kompilacja: **101.68.80**<br/>
&ensp;Wersja wydania: **30.122042.16880.0**<br/>

**Co nowego** 

- Dodano obsługę wersji `2.6.32-754.47.1.el6.x86_64` jądra podczas uruchamiania w systemie RHEL 6
- W systemie RHEL 6 produkt można teraz zainstalować na urządzeniach z uruchomionym nierozerwalnym jądrem przedsiębiorstwa (UEK)
- Rozwiązano problem polegający na tym, że nazwa procesu była czasami niepoprawnie wyświetlana, jak `unknown` podczas uruchamiania `mdatp diagnostic real-time-protection-statistics`
- Usunięto usterkę polegającą na tym, że produkt czasami niepoprawnie wykrywał pliki w folderze kwarantanny
- Rozwiązano problem polegający na tym `mdatp` , że narzędzie wiersza polecenia nie działało, gdy `/opt` było zainstalowane jako łącze nietrwałe
- Ulepszenia wydajności & poprawek błędów
</br>

<br/><br/>
</details>

<details>
<summary>Maj 2022 r. (kompilacja: 101.65.77 | Wersja wydania: 30.122032.16577.0)</summary>

&ensp;Data wydania: **2 maja 2022 r**.<br/>
&ensp;Opublikowano: **2 maja 2022 r**.<br/>
&ensp;Kompilacja: **101.65.77**<br/>
&ensp;Wersja wydania: **30.122032.16577.0**<br/>


**Co nowego**

- Ulepszono pole w programie `conflicting_applications` , `mdatp health` aby wyświetlić tylko najnowsze 10 procesów, a także uwzględnić nazwy procesów. Ułatwia to określenie, które procesy mogą być w konflikcie z Ochrona punktu końcowego w usłudze Microsoft Defender dla systemu Linux.
- Poprawki błędów


<br/><br/>
</details><details>
<summary>Mar-2022 (kompilacja: 101.62.74 | Wersja wydania: 30.122022.16274.0)</summary>

&ensp;Data wydania: **24 marca 2022 r**.<br/>
&ensp;Opublikowano: **24 marca 2022 r**.<br/>
&ensp;Kompilacja: **101.62.74**<br/>
&ensp;Wersja wydania: **30.122022.16274.0**<br/>


**Co nowego**

- Rozwiązano problem polegający na tym, że produkt niepoprawnie blokował dostęp do plików o rozmiarze większym niż 2 GB podczas uruchamiania w starszych wersjach jądra
- Poprawki błędów


<br/><br/>
</details><details>
<summary>Mar-2022 (kompilacja: 101.60.93 | Wersja wydania: 30.122012.16093.0)</summary>

&ensp;Data wydania: **9 marca 2022 r**.<br/>
&ensp;Opublikowano: **9 marca 2022 r**.<br/>
&ensp;Kompilacja: **101.60.93**<br/>
&ensp;Wersja wydania: **30.122012.16093.0**<br/>

**Co nowego**

- Ta wersja zawiera aktualizację zabezpieczeń dla [CVE-2022-23278](https://msrc-blog.microsoft.com/2022/03/08/guidance-for-cve-2022-23278-spoofing-in-microsoft-defender-for-endpoint/)


<br/><br/>
</details><details>
<summary>Mar-2022 (kompilacja: 101.60.05 | Wersja wydania: 30.122012.16005.0)</summary>

&ensp;Data wydania: **3 marca 2022 r**.<br/>
&ensp;Opublikowano: **3 marca 2022 r**.<br/>
&ensp;Kompilacja: **101.60.05**<br/>
&ensp;Wersja wydania: **30.122012.16005.0**<br/>

**Co nowego**

- Dodano obsługę jądra w wersji 2.6.32-754.43.1.el6.x86_64 dla RHEL 6.10
- Poprawki błędów


<br/><br/>
</details><details>
<summary>Luty 2022 (kompilacja: 101.58.80 | Wersja wydania: 30.122012.15880.0)</summary>

&ensp;Data wydania: **20 lutego 2022 r**.<br/>
&ensp;Opublikowano: **20 lutego 2022 r**.<br/>
&ensp;Kompilacja: **101.58.80**<br/>
&ensp;Wersja wydania: **30.122012.15880.0**<br/>

**Co nowego**

- Narzędzie wiersza polecenia obsługuje teraz przywracanie plików poddanych kwarantannie do lokalizacji innej niż ta, w której plik został pierwotnie wykryty. Można to zrobić za pośrednictwem programu `mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`.
- Począwszy od tej wersji, ochronę sieci dla systemu Linux można ocenić na żądanie
- Poprawki błędów



<br/><br/>
</details><details>
<summary>Jan-2022 (kompilacja: 101.56.62 | Wersja wydania: 30.121122.15662.0)</summary>

&ensp;Data wydania: **26 stycznia 2022 r**.<br/>
&ensp;Opublikowano: **26 stycznia 2022 r**.<br/>
&ensp;Kompilacja: **101.56.62**<br/>
&ensp;Wersja wydania: **30.121122.15662.0**<br/>

**Co nowego**

- Naprawiono awarię produktu wprowadzona w wersji 101.53.02, która wpłynęła na wielu klientów


<br/><br/>
</details><details>
<summary>Jan-2022 (kompilacja: 101.53.02 | Wersja wydania: (30.121112.15302.0)</summary>

&ensp;Data wydania: **8 stycznia 2022 r**.<br/>
&ensp;Opublikowano: **8 stycznia 2022 r**.<br/>
&ensp;Kompilacja: **101.53.02**<br/>
&ensp;Wersja wydania: **30.1211112.15302.0**<br/>

**Co nowego**

- Ulepszenia wydajności & poprawek błędów



</details>

<details><summary> Wersje 2021</summary><blockquote>
  <details><summary>(Kompilacja: 101.52.57 | Wersja wydania: 30.121092.15257.0)</summary>
   
  <p><b> Kompilacja: 101.52.57 <br>
Wersja wydania: 30.121092.15257.0</b></p>
   
  <p><b> Co nowego </b></p>

   - Dodano możliwość wykrywania zagrożonych plików jar log4j używanych przez aplikacje Java. Maszyna jest okresowo sprawdzana pod kątem uruchamiania procesów Javaprocesses z załadowanymi plikami jar log4j. Informacje są zgłaszane do zaplecza Ochrona punktu końcowego w usłudze Microsoft Defender i są widoczne w obszarze Zarządzanie dostępnością w portalu.
   
   </details>

  <details><summary>(Kompilacja: 101.47.76 | Wersja wydania: 30.121092.14776.0)</summary>
   
  <p><b> Kompilacja: 101.47.76 <br>
Wersja wydania: 30.121092.14776.0</b></p>
   
  <p><b>Co nowego</b></p>

   - Dodano nowy przełącznik do narzędzia wiersza polecenia, aby kontrolować, czy archiwa są skanowane podczas skanowania na żądanie. Można to skonfigurować za pomocą konfiguracji mdatp scan-archives --value [enabled/disabled]. Domyślnie jest to ustawienie włączone.

   - Poprawki błędów

   </details>

   <details><summary>(Kompilacja: 101.45.13 | Wersja wydania: 30.121082.14513.0)</summary>
   
  <p> 
  Kompilacja: <b>101.45.13 </b>  <br>
Wersja wydania:<b> 30.121082.14513.0 </b></p>
   
  <p><b>Co nowego</b></p>

  - Począwszy od tej wersji, oferujemy obsługę Ochrona punktu końcowego w usłudze Microsoft Defender do następujących dystrybucji:

    - Wersje RHEL6.7-6.10 i CentOS6.7-6.10.
    - Amazon Linux 2
    - Fedora 33 lub nowsza

  - Poprawki błędów

   </details>


   <details><summary>(Kompilacja: 101.45.00 | Wersja wydania: 30.121072.14500.0)</summary>
   
   <p> 
   Kompilacja:<b> 101.45.00</b> <br>
Wersja wydania: <b>30.121072.14500.0</b></p>
   
   <p><b>Co nowego</b></p>
      

  - Dodano nowe przełączniki do narzędzia wiersza polecenia:
    - Kontrolowanie stopnia równoległości skanowania na żądanie. Można to skonfigurować za pomocą programu `mdatp config maximum-on-demand-scan-threads --value [number-between-1-and-64]`. Domyślnie używany jest stopień równoległości `2` .
    - Określ, czy skanowanie po włączeniu lub wyłączeniu aktualizacji analizy zabezpieczeń. Można to skonfigurować za pomocą programu `mdatp config scan-after-definition-update --value [enabled/disabled]`. Domyślnie jest to ustawienie na wartość `enabled`.
  - Zmiana poziomu dziennika produktu wymaga teraz podniesienia uprawnień
  - Poprawki błędów

   </details>

   <details><summary>(Kompilacja: 101.39.98 | Wersja wydania: 30.121062.13998.0)</summary>
   
   <p> 
   Kompilacja: <b>101.39.98 </b><br>
Wersja wydania: <b>30.121062.13998.0</b></p>
   
   <p><b>Co nowego</b></p>

  - Ulepszenia wydajności & poprawek błędów
  
   </details>

   <details><summary>(Kompilacja: 101.34.27 | Wersja wydania: 30.121052.13427.0)</summary>
   
   <p> 
   Kompilacja:<b> 101.34.27</b> <br>
Wersja wydania: <b>30.121052.13427.0</b></p>
   
   <p><b>Co nowego</b></p>

   - Ulepszenia wydajności & poprawek błędów
  
   </details>

   <details><summary>(Kompilacja: 101.29.64 | Wersja wydania: 30.121042.12964.0)</summary>
   
   <p> 
   Kompilacja:<b> 101.29.64 </b><br>
Wersja wydania:<b> 30.121042.12964.0</b></p>
   
   <p><b>Co nowego</b></p>

   - Począwszy od tej wersji, zagrożenia wykryte podczas skanowania antywirusowego na żądanie wyzwalane za pośrednictwem klienta wiersza polecenia są automatycznie korygowane. Zagrożenia wykryte podczas skanowania wyzwalane za pośrednictwem interfejsu użytkownika nadal wymagają akcji ręcznej.
   - `mdatp diagnostic real-time-protection-statistics` Teraz obsługuje dwa dodatkowe przełączniki:
     - `--sort`: sortuje dane wyjściowe malejąco według całkowitej liczby skanowanych plików
     - `--top N`: wyświetla pierwsze wyniki N (działa tylko wtedy, gdy `--sort` jest również określona)
   - Ulepszenia wydajności & poprawek błędów
  
   </details>

   <details><summary>(Kompilacja: 101.25.72 | Wersja wydania: 30.121022.12563.0)</summary>
   
   <p> 
   Kompilacja:<b> 101.25.72</b> <br>
Wersja wydania: <b>30.121022.12563.0</b></p>
   
   <p><b>Co nowego</b></p>

   - Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux jest teraz dostępna w wersji zapoznawczej dla klientów rządowych USA. Aby uzyskać więcej informacji, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender dla klientów rządowych USA](gov.md).
   - Rozwiązano problem polegający na tym, że użycie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux w systemach z systemami plików FUSE doprowadziło do zawieszenia systemu operacyjnego
   - Ulepszenia wydajności & innych poprawek błędów
  
   </details>

   
   <details><summary>(Kompilacja: 101.25.63 | Wersja wydania: 30.121022.12563.0)</summary>
   
   <p> 
   Kompilacja:<b> 101.25.63</b> <br>
Wersja wydania: <b>30.121022.12563.0</b></p>
   
   <p><b>Co nowego</b></p>

   - Ulepszenia wydajności & poprawek błędów
  
   </details>

   <details><summary>(Kompilacja: 101.23.64 | Wersja wydania: 30.121021.12364.0)</summary>
   
   <p>
Kompilacja:<b> 101.23.64 </b><br>
Wersja wydania: 30.121021.12364.0</b></p>
   
   <p><b>Co nowego</b></p>

   - Poprawa wydajności w sytuacji, gdy cały punkt instalacji jest dodawany do listy wykluczeń programu antywirusowego. Przed tą wersją działanie pliku pochodzące z punktu instalacji było nadal przetwarzane przez produkt. Począwszy od tej wersji, działanie pliku dla wykluczonych punktów instalacji jest pomijane, co prowadzi do lepszej wydajności produktu
   - Dodano nową opcję do narzędzia wiersza polecenia, aby wyświetlić informacje o ostatnim skanowaniu na żądanie. Aby wyświetlić informacje o ostatnim skanowaniu na żądanie, uruchom polecenie `mdatp health --details antivirus`
   - Inne ulepszenia wydajności & poprawki błędów
  
   </details>

   <details><summary>(Kompilacja: 101.18.53)</summary>
   
    <p> 
    Kompilacja:<b> 101.18.53 </b><br>
        
    <p>Co nowego</b></p>

   - EDR dla systemu Linux jest teraz [ogólnie dostępny](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/edr-for-linux-is-now-is-generally-available/ba-p/2048539)
   - Dodano nowy przełącznik wiersza polecenia (`--ignore-exclusions`) w celu ignorowania wykluczeń av podczas skanowania niestandardowego (`mdatp scan custom`)
   - Rozszerzono `mdatp diagnostic create` o nowy parametr (`--path [directory]`), który umożliwia zapisywanie dzienników diagnostycznych w innym katalogu
    - Ulepszenia wydajności & poprawek błędów
    
   </details>





</blockquote></details>

