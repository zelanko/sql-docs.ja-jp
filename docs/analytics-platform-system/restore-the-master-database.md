---
title: Master データベースの分析プラットフォーム システムの復元 |Microsoft Docs
description: Analytics Platform System で master データベースを復元します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 7c9931ab6fb0946de83c3113a36de723a7a05cd0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960136"
---
# <a name="restore-the-master-database-in-analytics-platform-system"></a>Analytics Platform System で master データベースを復元します。
**Master の復元**の SQL Server PDW 構成マネージャー ページでは、master データベースのバックアップから復元することができます。  
  
## <a name="before-you-begin"></a>はじめに  
  
> [!IMPORTANT]  
> 復元を実行するには、SQL Server PDW は、ユーザーのセキュリティ情報と、データベース カタログを含む現在のマスター データベースを削除する必要があります。 復元を実行する前に、現在のマスター データベースのバックアップを作成することをお勧めします。  
  
## <a name="to-restore-the-master-database"></a>master データベースを復元するには  
  
1.  Configuration Manager を起動します。 詳細については、次を参照してください。 [Configuration Manager の起動&#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)します。  
  
2.  Configuration Manager の左側のウィンドウで次のようにクリックします。 **Master の復元**します。  
  
3.  復元するバックアップを選択します。  
  
4.  **[適用]** をクリックします。  
  
5.  復元を実行するのには、SQL Server PDW はアプライアンスのすべてのサービスをシャット ダウンし、すべてのユーザーを切断します。 復元が完了したら、SQL Server PDW アプライアンスのサービスは再起動します。  
  
![DWConfig アプライアンス PDW の復元のマスター](./media/restore-the-master-database/SQL_Server_PDW_DWConfig_ApplPDWRestore.png "SQL_Server_PDW_DWConfig_ApplPDWRestore")  
  
