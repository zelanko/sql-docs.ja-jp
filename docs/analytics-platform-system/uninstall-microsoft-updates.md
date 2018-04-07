---
title: Microsoft 更新プログラム (Analytics Platform System) のアンインストールします。
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
ms.assetid: df61570a-210d-4154-822f-98acd721f075
caps.latest.revision: 19
ms.openlocfilehash: b428cdacefefa96cdd5c500d34225c6963f5cb1f
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="uninstall-microsoft-updates"></a>Microsoft 更新プログラムをアンインストールします。
このトピックでは、Analytics Platform System アプライアンス上の以前にインストールされた Microsoft 更新プログラムをアンインストールする方法について説明します。  
  
## <a name="before-you-begin"></a>はじめに  
  
### <a name="prerequisites"></a>前提条件  
次の手順を実行するには、必要があります。  
  
-   アプライアンスを監視する管理コンソールにアクセスする権限を持つ分析プラットフォーム システム ログインします。  
  
-   ファブリック管理者はドメイン アカウントにログインするためのナレッジ、  *<Fabric Domain>* * *-HST01** ノード。  
  
## <a name="HowToUninstallMSFT"></a>Microsoft 更新プログラムをアンインストールするには  
  
1.  ログイン、  *<Fabric Domain>* * *-HST01** ファブリック ドメイン管理者としてのノードです。  
  
2.  WSUS をアンインストールするが承認されているすべての更新プログラムをアンインストールするには、コマンド プロンプト ウィンドウを開きし、次のコマンドを入力します。 プレース ホルダー アイテムを置き換える*< >*適切な情報を使用します。  
  
    ```  
    C:\pdwinst\media\setup.exe /action="RemoveMicrosoftUpdate" /DomainAdminPasswords="<password>"  
    ```  
  
## <a name="see-also"></a>参照  
[ダウンロードして Microsoft 更新プログラムを適用して&#40;分析プラットフォーム システム&#41;](download-and-apply-microsoft-updates.md)  
[分析プラットフォーム システムの修正プログラム適用&#40;分析プラットフォーム システム&#41;](apply-analytics-platform-system-hotfixes.md)  
[分析プラットフォーム システムの修正プログラムをアンインストール&#40;分析プラットフォーム システム&#41;](uninstall-analytics-platform-system-hotfixes.md)  
[ソフトウェア サービス&#40;分析プラットフォーム システム&#41;](software-servicing.md)  
  
