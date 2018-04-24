---
title: Analytics Platform System 修正プログラムをアンインストール |Microsoft ドキュメント
description: Analytics Platform System の修正プログラムをアンインストールします。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 83e57a676ee0eff21eb3a736484d8e286cdeee01
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="uninstall-analytics-platform-system-hotfixes"></a>Analytics Platform System の修正プログラムをアンインストールします。 
次の手順では、以前にインストールされた Analytics Platform System 修正プログラムをアンインストールする方法について説明します。  
  
## <a name="before-you-begin"></a>はじめに  
  
### <a name="prerequisites"></a>前提条件  
次の手順を実行するには、必要があります。  
  
-   アプライアンスを監視する管理コンソールにアクセスする権限を持つ分析プラットフォーム システム ログインします。  
  
-   ドメイン管理者アカウントにログインするため、 *< appliance_domain > * * *-HST01** ノード。  
  
-   アンインストールする修正プログラムのサポート技術情報の記事番号。  
  
## <a name="HowToUninstallPDW"></a>SQL Server PDW の修正プログラムをアンインストールするには  
  
1.  ログオン、 *< appliance_domain > * * *-HST01** ファブリック ドメイン管理者としてのノードです。  
  
2.  管理者オプションとして、実行を使用して、コマンド プロンプトを開きます。  
  
3.  ディレクトリに移動`C:\PDWINST\Patches\<kbarticle>\media`場所*<kbarticle>*をアンインストールする修正プログラムのサポート技術情報の記事番号です。  
  
    ```  
    cd /d c:\PDWINST\Patches\<kbarticle>\media  
    ```  
  
4.  修正プログラムを削除するには、次のコマンドを実行します。  
  
    ```  
    setup.exe /action="removepatch" /DomainAdminPassword="<password>"  
    ```  
  
## <a name="see-also"></a>参照  
[ダウンロードして Microsoft 更新プログラムを適用して&#40;分析プラットフォーム システム&#41;](download-and-apply-microsoft-updates.md)  
[Microsoft 更新プログラムのアンインストール&#40;分析プラットフォーム システム&#41;](uninstall-microsoft-updates.md)  
[分析プラットフォーム システムの修正プログラム適用&#40;分析プラットフォーム システム&#41;](apply-analytics-platform-system-hotfixes.md)  
[ソフトウェア サービス&#40;分析プラットフォーム システム&#41;](software-servicing.md)  
  
