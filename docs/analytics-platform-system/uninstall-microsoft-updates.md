---
title: Microsoft 更新プログラム - Analytics Platform System のアンインストール |Microsoft Docs"
description: Microsoft Analytics Platform System (APS) での更新プログラムをアンインストールします。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: f910eeb7f3b38d29f7ae7b084de981c22a6f3f4a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959830"
---
# <a name="uninstall-microsoft-updates-in-analytics-platform-system"></a>Analytics Platform System での Microsoft 更新プログラムをアンインストールします。
この記事では、Analytics Platform System appliance で以前にインストールされた Microsoft 更新プログラムをアンインストールする方法について説明します。  
  
## <a name="before-you-begin"></a>はじめに  
  
### <a name="prerequisites"></a>必須コンポーネント  
次の手順を実行するには、必要があります。  
  
-   アプライアンスの監視を管理コンソールにアクセスする権限を持つ、Analytics Platform System ログインします。  
  
-   Fabric ドメイン管理者アカウントにログインするのには、サポート技術情報、 <em> <Fabric Domain> </em> **-HST01**ノード。  
  
## <a name="HowToUninstallMSFT"></a>Microsoft 更新プログラムをアンインストールするには  
  
1.  ログイン、 <em> <Fabric Domain> </em> **-HST01** Fabric ドメイン管理者としてのノード。  
  
2.  アンインストールするには、次のように WSUS が承認されたすべての更新プログラムをアンインストールするに、コマンド プロンプト ウィンドウを開き、次のコマンドを入力します。 プレース ホルダー アイテムを置き換える *< >* 適切な情報を使用します。  
  
    ```  
    C:\pdwinst\media\setup.exe /action="RemoveMicrosoftUpdate" /DomainAdminPasswords="<password>"  
    ```  
  
## <a name="next-steps"></a>次の手順
詳細については、以下をご覧ください。
- [ダウンロードして Microsoft 更新プログラムを適用して&#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md) 
- [Analytics Platform System の修正プログラムを適用&#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
- [Analytics Platform System の修正プログラムのアンインストール&#40;Analytics Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
- [ソフトウェアのサービス&#40;Analytics Platform System&#41;](software-servicing.md)  
  
