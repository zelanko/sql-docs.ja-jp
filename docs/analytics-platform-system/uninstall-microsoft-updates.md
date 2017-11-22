---
title: "Microsoft 更新プログラム (Analytics Platform System) のアンインストールします。"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: df61570a-210d-4154-822f-98acd721f075
caps.latest.revision: "19"
ms.openlocfilehash: c801918cbac5d0762384a0cd3adcca9ddf8f346a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="uninstall-microsoft-updates"></a>Microsoft 更新プログラムをアンインストールします。
このトピックでは、Analytics Platform System アプライアンス上の以前にインストールされた Microsoft 更新プログラムをアンインストールする方法について説明します。  
  
## <a name="before-you-begin"></a>はじめに  
  
### <a name="prerequisites"></a>前提条件  
次の手順を実行するには、必要があります。  
  
-   アプライアンスを監視する管理コンソールにアクセスする権限を持つ分析プラットフォーム システム ログインします。  
  
-   ファブリック管理者はドメイン アカウントにログインするためのナレッジ、  *<Fabric Domain>*  **-HST01**ノード。  
  
## <a name="HowToUninstallMSFT"></a>Microsoft 更新プログラムをアンインストールするには  
  
1.  ログイン、  *<Fabric Domain>*  **-HST01**ファブリック ドメイン管理者としてのノードです。  
  
2.  WSUS をアンインストールするが承認されているすべての更新プログラムをアンインストールするには、コマンド プロンプト ウィンドウを開きし、次のコマンドを入力します。 プレース ホルダー アイテムを置き換える*< >*適切な情報を使用します。  
  
    ```  
    C:\pdwinst\media\setup.exe /action="RemoveMicrosoftUpdate" /DomainAdminPasswords="<password>"  
    ```  
  
## <a name="see-also"></a>参照  
[ダウンロードして適用 Microsoft 更新プログラムと #40 です。Analytics Platform System &#41;](download-and-apply-microsoft-updates.md)  
[分析プラットフォーム システムの修正プログラム &#40; を適用します。Analytics Platform System &#41;](apply-analytics-platform-system-hotfixes.md)  
[分析プラットフォーム システムの修正プログラム &#40; をアンインストールします。Analytics Platform System &#41;](uninstall-analytics-platform-system-hotfixes.md)  
[ソフトウェアのサービス (&) #40 です。Analytics Platform System &#41;](software-servicing.md)  
  
