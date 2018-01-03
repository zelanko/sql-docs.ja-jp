---
title: "分析プラットフォーム システムの修正プログラム (Analytics Platform System) のアンインストールします。"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c9ab596d-3f5a-48e2-bce7-c9be99b8c23b
caps.latest.revision: "21"
ms.openlocfilehash: 32d733f2e05855eb361095d23d6c34acefd343dc
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="uninstall-analytics-platform-system-hotfixes"></a>分析プラットフォーム システムの修正プログラムをアンインストールします。
次の手順では、以前にインストールされた Analytics Platform System 修正プログラムをアンインストールする方法について説明します。  
  
## <a name="before-you-begin"></a>はじめに  
  
### <a name="prerequisites"></a>Prerequisites  
次の手順を実行するには、必要があります。  
  
-   アプライアンスを監視する管理コンソールにアクセスする権限を持つ分析プラットフォーム システム ログインします。  
  
-   ドメイン管理者アカウントにログインするため、 *< appliance_domain >***-HST01**ノード。  
  
-   アンインストールする修正プログラムのサポート技術情報の記事番号。  
  
## <a name="HowToUninstallPDW"></a>SQL Server PDW の修正プログラムをアンインストールするには  
  
1.  ログオン、 *< appliance_domain >***-HST01**ファブリック ドメイン管理者としてのノードです。  
  
2.  管理者オプションとして、実行を使用して、コマンド プロンプトを開きます。  
  
3.  ディレクトリに移動`C:\PDWINST\Patches\<kbarticle>\media`場所 *<kbarticle>* をアンインストールする修正プログラムのサポート技術情報の記事番号です。  
  
    ```  
    cd /d c:\PDWINST\Patches\<kbarticle>\media  
    ```  
  
4.  修正プログラムを削除するには、次のコマンドを実行します。  
  
    ```  
    setup.exe /action="removepatch" /DomainAdminPassword="<password>"  
    ```  
  
## <a name="see-also"></a>参照  
[ダウンロードして適用 Microsoft 更新プログラムと #40 です。Analytics Platform System &#41;](download-and-apply-microsoft-updates.md)  
[Microsoft 更新プログラム &#40; をアンインストールします。Analytics Platform System &#41;](uninstall-microsoft-updates.md)  
[分析プラットフォーム システムの修正プログラム &#40; を適用します。Analytics Platform System &#41;](apply-analytics-platform-system-hotfixes.md)  
[ソフトウェアのサービス (&) #40 です。Analytics Platform System &#41;](software-servicing.md)  
  
