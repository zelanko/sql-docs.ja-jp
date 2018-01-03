---
title: "Configuration Manager (Analytics Platform System) の起動します。"
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
ms.assetid: b914ba9a-e4ec-4750-934a-c447fc8909e3
caps.latest.revision: "22"
ms.openlocfilehash: 2ead82cd226a585d261eac2779cacb72cd5edbb6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="launch-the-configuration-manager"></a>構成マネージャーを起動します。
このトピックでは起動するための説明、 **Configuration Manager** Analytics Platform System アプライアンスです。  
  
## <a name="before-you-begin"></a>はじめに  
  
### <a name="prerequisites"></a>Prerequisites  
Analytics Platform System**Configuration Manager**アプライアンス ドメイン管理者によってのみ実行できます。 このツールを実行するには、アプライアンスのドメイン管理者のパスワードが必要です。 APS の追加の管理者を作成するを参照してください[APS ドメイン管理者 &#40; を作成します。APS&#41;](create-an-aps-domain-administrator-aps.md).  
  
## <a name="Accessing"></a>Configuration Manager ツールを起動します。  
Configuration Manager を実行するには、PDW 管理ノードに接続するリモート デスクトップを使用 (***PDW_region*-CTL01**) ノード、およびログインとして*appliance_domain* **\Administrator**です。 開始するときに、 **Configuration Manager**プログラムを使用して、**管理者として実行**管理者の資格情報を使用することを確認するにはオプションです。  
  
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
[管理コンソール &#40; を使用してアプライアンスを監視します。Analytics Platform System &#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
