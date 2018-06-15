---
title: Microsoft 更新プログラム - Analytics Platform System アンインストール |Microsoft ドキュメント"
description: Microsoft Analytics Platform System (APS) での更新プログラムをアンインストールします。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 57d0eb3616cf3567f63d75029f79cea6709ed955
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31538552"
---
# <a name="uninstall-microsoft-updates-in-analytics-platform-system"></a>Analytics Platform System の Microsoft 更新プログラムをアンインストールします。
この記事では、Analytics Platform System アプライアンス上の以前にインストールされた Microsoft 更新プログラムをアンインストールする方法について説明します。  
  
## <a name="before-you-begin"></a>はじめに  
  
### <a name="prerequisites"></a>前提条件  
次の手順を実行するには、必要があります。  
  
-   アプライアンスを監視する管理コンソールにアクセスする権限を持つ分析プラットフォーム システム ログインします。  
  
-   ログインに、ファブリック管理者はドメイン アカウントのナレッジ、  *<Fabric Domain>* * *-HST01** ノード。  
  
## <a name="HowToUninstallMSFT"></a>Microsoft 更新プログラムをアンインストールするには  
  
1.  ログインに、  *<Fabric Domain>* * *-HST01** ファブリック ドメイン管理者としてのノードです。  
  
2.  WSUS をアンインストールするが承認されているすべての更新プログラムをアンインストールするには、コマンド プロンプト ウィンドウを開きし、次のコマンドを入力します。 プレース ホルダー アイテムを置き換える *< >* 適切な情報を使用します。  
  
    ```  
    C:\pdwinst\media\setup.exe /action="RemoveMicrosoftUpdate" /DomainAdminPasswords="<password>"  
    ```  
  
## <a name="next-steps"></a>次の手順
詳細については、以下をご覧ください。
- [ダウンロードして Microsoft 更新プログラムを適用して&#40;分析プラットフォーム システム&#41;](download-and-apply-microsoft-updates.md) 
- [分析プラットフォーム システムの修正プログラム適用&#40;分析プラットフォーム システム&#41;](apply-analytics-platform-system-hotfixes.md)  
- [分析プラットフォーム システムの修正プログラムをアンインストール&#40;分析プラットフォーム システム&#41;](uninstall-analytics-platform-system-hotfixes.md)  
- [ソフトウェア サービス&#40;分析プラットフォーム システム&#41;](software-servicing.md)  
  
