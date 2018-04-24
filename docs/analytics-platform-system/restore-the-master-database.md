---
title: Master データベースの分析プラットフォーム システムを復元 |Microsoft ドキュメント
description: 分析プラットフォーム システムでマスター データベースを復元します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 184184f332225e76e152c2d909cfff788b4fea91
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="restore-the-master-database-in-analytics-platform-system"></a>Analytics Platform System で master データベースを復元します。
**Master の復元**ページの SQL Server PDW 構成マネージャーでは、バックアップから master データベースを復元することができます。  
  
## <a name="before-you-begin"></a>はじめに  
  
> [!IMPORTANT]  
> 復元を実行するには、SQL Server PDW は現在のマスター データベースで、ユーザーのセキュリティ情報と、データベース カタログが含まれていますを削除する必要があります。 復元を実行する前に、現在のマスター データベースのバックアップを作成することをお勧めします。  
  
## <a name="to-restore-the-master-database"></a>master データベースを復元するには  
  
1.  構成マネージャーを起動します。 詳細については、次を参照してください。[構成マネージャーを起動&#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)です。  
  
2.  構成マネージャーの左側のウィンドウでをクリックして**Master の復元**です。  
  
3.  復元するマスターのバックアップを選択します。  
  
4.  **[適用]**をクリックします。  
  
5.  復元を実行するのには、SQL Server PDW はアプライアンスのすべてのサービスをシャット ダウンし、すべてのユーザーを切断します。 復元が完了すると、SQL Server PDW アプライアンスのサービスは再起動します。  
  
![DWConfig アプライアンス PDW の復元のマスター](./media/restore-the-master-database/SQL_Server_PDW_DWConfig_ApplPDWRestore.png "SQL_Server_PDW_DWConfig_ApplPDWRestore")  
  
