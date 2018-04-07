---
title: 分析プラットフォーム システムの修正プログラム (Analytics Platform System) のアンインストールします。
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c9ab596d-3f5a-48e2-bce7-c9be99b8c23b
caps.latest.revision: 21
ms.openlocfilehash: 56c6731d5a39741574999d94532b9505adaf6380
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="uninstall-analytics-platform-system-hotfixes"></a>分析プラットフォーム システムの修正プログラムをアンインストールします。
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
  
