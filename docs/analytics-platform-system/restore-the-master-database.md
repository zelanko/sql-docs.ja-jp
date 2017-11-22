---
title: "Master データベース (Analytics Platform System) の復元します。"
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
ms.assetid: 7870021a-0d89-422e-b8ea-1cc95b45c139
caps.latest.revision: "11"
ms.openlocfilehash: ff00e17d05b13317e009357e8c2089a46cbce4a4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="restore-the-master-database"></a>Master データベースを復元します。
**Master の復元**ページの SQL Server PDW 構成マネージャーでは、バックアップから master データベースを復元することができます。  
  
## <a name="before-you-begin"></a>はじめに  
  
> [!IMPORTANT]  
> 復元を実行するには、SQL Server PDW は現在のマスター データベースで、ユーザーのセキュリティ情報と、データベース カタログが含まれていますを削除する必要があります。 復元を実行する前に、現在のマスター データベースのバックアップを作成することをお勧めします。  
  
## <a name="to-restore-the-master-database"></a>master データベースを復元するには  
  
1.  構成マネージャーを起動します。 詳細については、次を参照してください[構成マネージャー &#40; を起動。Analytics Platform System &#41;](launch-the-configuration-manager.md).  
  
2.  構成マネージャーの左側のウィンドウでをクリックして**Master の復元**です。  
  
3.  復元するマスターのバックアップを選択します。  
  
4.  **[適用]**をクリックします。  
  
5.  復元を実行するのには、SQL Server PDW はアプライアンスのすべてのサービスをシャット ダウンし、すべてのユーザーを切断します。 復元が完了すると、SQL Server PDW アプライアンスのサービスは再起動します。  
  
![DWConfig アプライアンス PDW の復元のマスター](./media/restore-the-master-database/SQL_Server_PDW_DWConfig_ApplPDWRestore.png "SQL_Server_PDW_DWConfig_ApplPDWRestore")  
  
