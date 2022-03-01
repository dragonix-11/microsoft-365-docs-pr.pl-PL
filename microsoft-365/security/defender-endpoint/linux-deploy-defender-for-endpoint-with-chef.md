---
title: Jak wdrożyć usługę Defender dla punktu końcowego w systemie Linux za pomocą systemu Linux
description: Dowiedz się, jak wdrożyć program Defender dla punktu końcowego w systemie Linux z Rzeszą
keywords: microsoft, defender, atp, linux, skanuje, antivirus, microsoft defender for endpoint (linux)
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 799fc4d163b120b4197b6cd044efe4740e4a3cc7
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033738"
---
# <a name="deploy-defender-for-endpoint-on-linux-with-chef"></a>Wdrażanie programu Defender dla punktu końcowego w systemie Linux z usługą Linux

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Przed rozpoczęciem: Zainstaluj rozpakuj program, jeśli nie został jeszcze zainstalowany.

Składniki Steam są już zainstalowane, a istnieje repozytorium Kucharska Generate Repo \<reponame\>, aby przechować książka kucharska, która będzie używana do wdrażania programu Defender dla punktu końcowego na zarządzanych serwerach Linux.

W istniejącym repozytorium możesz utworzyć nową bazę kucharską, uruchamiając następujące polecenie z folderu kuchaczki, który znajduje się w repozytorium kucharską:

```bash
chef generate cookbook mdatp
```

To polecenie utworzy nową strukturę folderów dla nowej książki kucharskiej o nazwie mdatp. Możesz także użyć istniejącej książki kucharskiej, jeśli masz już takie, do których chcesz dodać wdrożenie MDE.
Po utworzeniu książki kucharskiej utwórz folder plików wewnątrz właśnie utworzonego folderu kucharskiej:

```bash
mkdir mdatp/files
```

Przenieś plik zip dołączania do serwera Linux, który można pobrać z portalu Microsoft 365 Defender do tego nowego folderu plików.

Na stacji roboczej Dla klienta przejdź do folderu mdatp/recipes. Ten folder jest tworzony po wygenerowaniu książki kucharskiej. Użyj preferowanego edytora tekstów (np. vi lub nano), aby dodać następujące instrukcje na końcu pliku default.rb:

- include_recipe ':onboard_mdatp'
- include_recipe '::install_mdatp'

Następnie zapisz i zamknij plik default.rb.

Następnie utwórz nowy plik z przepisami o install_mdatp.rb w folderze przepisy i dodaj ten tekst do pliku:

```powershell
#Add Microsoft Defender
Repo
case node['platform_family']
when 'debian'
 apt_repository 'MDAPRepo' do
   arch               'amd64'
   cache_rebuild      true
   cookbook           false
   deb_src            false
   key                'BC528686B50D79E339D3721CEB3E94ADBE1229CF'
   keyserver          "keyserver.ubuntu.com"
   distribution       'focal'
   repo_name          'microsoft-prod'
   components         ['main']
   trusted            true
   uri                "https://packages.microsoft.com/config/ubuntu/20.04/prod"
 end
 apt_package "mdatp"
when 'rhel'
 yum_repository 'microsoft-prod' do
   baseurl            "https://packages.microsoft.com/config/rhel/7/prod/"
   description        "Microsoft Defender for Endpoint"
   enabled            true
   gpgcheck           true
   gpgkey             "https://packages.microsoft.com/keys/microsoft.asc"
 end
 if node['platform_version'] <= 8 then
    yum_package "mdatp"
 else
    dnf_package "mdatp"
 end
end
```

Musisz zmodyfikować numer wersji, rozpowszechnianie i nazwę ponownego wdrożenia, aby dopasować ją do wersji, w których wdrażasz, i kanału, w którym chcesz wdrożyć.
Następnie należy utworzyć plik onboard_mdatp.rb w folderze mdatp/recipies. Dodaj do tego pliku następujący tekst:

```powershell
#Create MDATP Directory
mdatp = "/etc/opt/microsoft/mdatp"
zip_path = "/path/to/chef-repo/cookbooks/mdatp/files/WindowsDefenderATPOnboardingPackage.zip"

directory "#{mdatp}" do
  owner 'root'
  group 'root'
  mode 0755
  recursive true
end

#Extract WindowsDefenderATPOnbaordingPackage.zip into /etc/opt/microsoft/mdatp

bash 'Extract Onbaording Json MDATP' do
  code <<-EOS
  unzip #{zip_path} -d #{mdatp}
  EOS
  not_if { ::File.exist?('/etc/opt/microsoft/mdatp/mdatp_onboard.json') }
end
```

Pamiętaj o zaktualizowaniu nazwy ścieżki do lokalizacji pliku dołączania.
Aby przetestować jej wdrożenie na stacji roboczej Wiad.``sudo chef-client -z -o mdatp``
Po wdrożeniu rozważ utworzenie i wdrożenie pliku konfiguracji na serwerach w oparciu o ustawienie preferencji programu [Microsoft Defender dla punktu końcowego w systemie Linux](/linux-preferences.md).
Po utworzeniu i przetestowaniu pliku konfiguracji możesz umieścić go w folderze książka kucharska/mdatp/pliki, gdzie również umieszczasz pakiet dołączania. Następnie możesz utworzyć plik settings_mdatp.rb w folderze mdatp/recipies i dodać ten tekst:

```powershell
#Copy the configuration file
cookbook_file '/etc/opt/microsoft/mdatp/managed/mdatp_managed.json' do
  source 'mdatp_managed.json'
  owner 'root'
  group 'root'
  mode '0755'
  action :create
end
```

Aby uwzględnić ten krok jako część przepisów, po prostu dodaj plik include_recipe :: settings_mdatp" do pliku default.rb w folderze z przepisami.
Za pomocą karty crontab możesz także zaplanować automatyczne aktualizacje Zaplanuj aktualizację programu [Microsoft Defender for Endpoint (Linux)](linux-update-MDE-Linux.md).

Odinstaluj album kucharska MDATP:

```powershell
#Uninstall the Defender package
case node['platform_family']
when 'debian'
 apt_package "mdatp" do
   action :remove
 end
when 'rhel'
 if node['platform_version'] <= 8
then
    yum_package "mdatp" do
      action :remove
    end
 else
    dnf_package "mdatp" do
      action :remove
    end
 end
end
```
