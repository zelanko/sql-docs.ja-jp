---
title: Analytics Platform System の修正プログラムのアンインストール |Microsoft Docs
description: Analytics Platform System の修正プログラムをアンインストールします。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 5507eae7bb2f8a5ce138223a031ac4946d9f0030
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2019
ms.locfileid: "54255068"
---
# <a name="uninstall-analytics-platform-system-hotfixes"></a>Analytics Platform System の修正プログラムをアンインストールします。 
次の手順では、以前にインストールされた Analytics Platform System の修正プログラムをアンインストールする方法について説明します。  
  
## <a name="before-you-begin"></a>はじめに  
  
### <a name="prerequisites"></a>前提条件  
次の手順を実行するには、必要があります。  
  
-   アプライアンスの監視を管理コンソールにアクセスする権限を持つ、Analytics Platform System ログインします。  
  
-   ドメイン管理者アカウントにログインを<em>< appliance_domain ></em>**-HST01**ノード。  
  
-   アンインストールする修正プログラムのサポート技術情報記事番号。  
  
## <a name="HowToUninstallPDW"></a>SQL Server PDW の修正プログラムをアンインストールするには  
  
1.  ログオン、 <em>< appliance_domain ></em>**-HST01** Fabric ドメイン管理者としてのノード。  
  
2.  管理者として実行を使用して、コマンド プロンプトを開きます。  
  
3.  ディレクトリに移動`C:\PDWINST\Patches\<kbarticle>\media`場所*<kbarticle>* をアンインストールする修正プログラムのサポート技術情報記事番号です。  
  
    ```  
    cd /d c:\PDWINST\Patches\<kbarticle>\media  
    ```  
  
4.  修正プログラムを削除するには、次のコマンドを実行します。  
  
    ```  
    setup.exe /action="removepatch" /DomainAdminPassword="<password>"  
    ```  
  
## <a name="see-also"></a>参照  
[ダウンロードして Microsoft 更新プログラムを適用して&#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md)  
[Microsoft 更新プログラムのアンインストール&#40;Analytics Platform System&#41;](uninstall-microsoft-updates.md)  
[Analytics Platform System の修正プログラムを適用&#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
[ソフトウェアのサービス&#40;Analytics Platform System&#41;](software-servicing.md)  
  
