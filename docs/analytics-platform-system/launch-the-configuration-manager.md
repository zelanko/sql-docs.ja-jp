---
title: Configuration Manager - 分析プラットフォーム システムを起動 |Microsoft ドキュメント
description: Analytics Platform System アプライアンス用 Configuration Manager ツールを起動するための手順です。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: d2e7a726386aa64d04f87f30cd22328900b1e5cd
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="launch-the-configuration-manager-in-analytics-platform-system"></a>Analytics Platform System での Configuration Manager を起動します。
このトピックでは起動するための説明、 **Configuration Manager** Analytics Platform System アプライアンスです。  
  
## <a name="before-you-begin"></a>はじめに  
  
### <a name="prerequisites"></a>前提条件  
Analytics Platform System**Configuration Manager**アプライアンス ドメイン管理者によってのみ実行できます。 このツールを実行するには、アプライアンスのドメイン管理者のパスワードが必要です。 APS の追加の管理者を作成するを参照してください。 [APS ドメイン管理者を作成する&#40;APS&#41;](create-an-aps-domain-administrator-aps.md)です。  
  
## <a name="Accessing"></a>Configuration Manager ツールを起動します。  
Configuration Manager を実行するには、PDW 管理ノードに接続するリモート デスクトップを使用 (***PDW_region *-CTL01**) ノード、およびとしてログイン * appliance_domain ***\Administrator**です。 開始するときに、 **Configuration Manager**プログラムを使用して、**管理者として実行**管理者の資格情報を使用することを確認するにはオプションです。  
  
#### <a name="to-launch-from-a-browser-window"></a>ブラウザー ウィンドウから起動するには  
  
1.  ブラウザーを開き、ディレクトリに移動`C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`です。  
  
2.  右クリック`dwconfig.exe` をクリックし、**管理者として実行**です。  
  
#### <a name="to-launch-from-a-command-prompt"></a>コマンド プロンプトから起動するには  
  
1.  デスクトップで、開く、**開始** メニューのをクリックして**プログラム**、 をクリックして**アクセサリ**を右クリックして**コマンド プロンプト**をクリックして**管理者として実行**です。  
  
2.  コマンド プロンプトでディレクトリを変更するのには、次のコマンドを入力してください:`cd /d "C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100"`です。  
  
3.  コマンド プロンプトで次のように入力します。`dwconfig.exe`です。  
  
後に、 **Configuration Manager**が開始されると、左側のウィンドウで記載されている使用可能なすべての機能が表示されます。 このセクションの残りの部分では、このツールで使用できる各操作を実行する方法について説明します。  
  
終了し、終了**Configuration Manager**をクリックして**終了**任意の画面の右下隅にあります。  
  
![SQL_Server_PDW_DWConfig_ApplTop](./media/launch-the-configuration-manager/SQL_Server_PDW_DWConfig_ApplTop.png "SQL_Server_PDW_DWConfig_ApplTop")  
  
## <a name="see-also"></a>参照  
[管理者コンソールを使用してアプライアンスをモニター&#40;分析プラットフォーム システム&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
