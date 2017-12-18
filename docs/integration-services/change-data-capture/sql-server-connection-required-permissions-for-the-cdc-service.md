---
title: "CDC Service で使用する SQL Server 接続に必要な権限 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: change-data-capture
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9e968f9-180c-4fa0-a849-98f2b1942330
caps.latest.revision: "8"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f9f9031088ec304f5a26496355a43ba6b1a3ac3b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sql-server-connection-required-permissions-for-the-cdc-service"></a>CDC Service で使用する SQL Server 接続に必要な権限
  CDC Service 構成コンソールのタスクを実行するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続情報が必要です。 このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]との接続を設定するために [SQL Server への接続] ダイアログ ボックスで指定できる情報について説明します。  
  
 ‭[SQL Server への接続] ダイアログ ボックスは必要なときに開きます。たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続情報がない場合や、情報は存在しても接続に必要な権限がない場合などです。  
  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続が必要となる各種のタスクと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン/ユーザーに必要な権限について説明します。  
  
|タスク|最低限の権限|  
|----------|-------------------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを準備する。|`dbcreator` 固定サーバー ロール|  
|Oracle CDC サービスが使用する Oracle CDC Service-SQLServer ログインを作成する。|`public` 固定サーバー ロール|  
|MSXDBCDC に新しいサービスを登録するために使用する Oracle CDC Service ログインを作成する。|`db_datareader` ロールと `db_datawriter` ロール|  
|MSXDBCDC のサービスの登録を更新するために使用する Oracle CDC Service ログインを編集する。|`db_datareader` ロールと `db_datawriter` ロール|  
|MSXDBCDC のサービスの登録を更新するために使用する Oracle CDC Service ログインを削除する。|`db_datareader` ロールと `db_datawriter` ロール|  
  
## <a name="see-also"></a>参照  
 [SQL Server への接続](../../integration-services/change-data-capture/connection-to-sql-server.md)   
 [削除用の SQLServer への接続](../../integration-services/change-data-capture/connection-to-sql-server-for-delete.md)  
  
  
