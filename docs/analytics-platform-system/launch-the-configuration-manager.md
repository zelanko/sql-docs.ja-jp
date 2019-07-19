---
title: Configuration Manager - Analytics Platform System の起動 |Microsoft Docs
description: Analytics Platform System appliance 用 Configuration Manager ツールを起動するための手順です。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 7aef9ada4a93605460cf2759dbe9deeddfc9e0d9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960724"
---
# <a name="launch-the-configuration-manager-in-analytics-platform-system"></a>Analytics Platform System で Configuration Manager を起動します。
このトピックでは起動するための手順、 **Configuration Manager** Analytics Platform System appliance。  
  
## <a name="before-you-begin"></a>はじめに  
  
### <a name="prerequisites"></a>必須コンポーネント  
Analytics Platform System**Configuration Manager**アプライアンスのドメイン管理者によってのみ実行できます。 このツールを実行するには、アプライアンスのドメイン管理者のパスワードが必要です。 追加の AP 管理者を作成するを参照してください。 [APS ドメイン管理者を作成&#40;AP&#41;](create-an-aps-domain-administrator-aps.md)します。  
  
## <a name="Accessing"></a>Configuration Manager ツールを起動します。  
Configuration Manager を実行するには、PDW 管理ノードに接続するリモート デスクトップを使用 ( **_PDW_region_-CTL01**) ノード、およびログインとして_appliance_domain_ **\Administrator**します。 開始するときに、 **Configuration Manager**プログラムで、使用、**管理者として実行**管理者の資格情報を使用することを確認するにはオプションです。  
  
#### <a name="to-launch-from-a-browser-window"></a>ブラウザー ウィンドウから起動するには  
  
1.  ブラウザーを開き、ディレクトリに移動します`C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`します。  
  
2.  右クリックして`dwconfig.exe` をクリックし、**管理者として実行**します。  
  
#### <a name="to-launch-from-a-command-prompt"></a>コマンド プロンプトから起動するには  
  
1.  デスクトップで開き、**開始** メニューのをクリックして**プログラム**、 をクリックして**アクセサリ**を右クリックして**コマンド プロンプト**順にクリックします**管理者として実行**します。  
  
2.  コマンド プロンプトでディレクトリを変更するのには、次のコマンドを入力します:`cd /d "C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100"`します。  
  
3.  コマンド プロンプトで、「`dwconfig.exe`」と入力します。  
  
後に、 **Configuration Manager**が開始されると、左側のウィンドウで表示されているすべての機能が表示されます。 このセクションの残りの部分では、このツールで使用できる各操作を実行する方法について説明します。  
  
閉じて終了**Configuration Manager**、 をクリックして**終了**の任意の画面の右下隅にします。  
  
![SQL_Server_PDW_DWConfig_ApplTop](./media/launch-the-configuration-manager/SQL_Server_PDW_DWConfig_ApplTop.png "SQL_Server_PDW_DWConfig_ApplTop")  
  
## <a name="see-also"></a>関連項目  
[アプライアンスの監視、管理コンソールを使用して&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
