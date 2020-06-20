---
title: ユーティリティ コントロール ポイントの削除 (SQL Server ユーティリティ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c048a416-900e-4c77-8243-e0f0d8b94068
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b4325be141d93a684a0cbb31a6f2c91197704ba4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85023299"
---
# <a name="remove-a-utility-control-point-sql-server-utility"></a>ユーティリティ コントロール ポイントの削除 (SQL Server ユーティリティ)
  このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインスタンスから [!INCLUDE[tsql](../../includes/tsql-md.md)]ユーティリティ コントロール ポイント (UCP) を削除する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   **ユーティリティ コントロール ポイントを削除する方法:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 制限事項と制約事項  
 この手順を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティから UCP を削除する前に、次の要件を確認してください。 ストアド プロシージャでは、操作の一部として前提条件がチェックされます。  
  
-   この手順を実行する前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージド インスタンスをすべて UCP から削除する必要があります。 UCP は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のマネージド インスタンスの 1 つです。 詳細については、「 [SQL Server ユーティリティからの SQL Server のインスタンスの削除](remove-an-instance-of-sql-server-from-the-sql-server-utility.md)」を参照してください。  
  
-   このプロシージャは、UCP として構成されたコンピューターで実行する必要があります。  
  
-   UCP を削除した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにユーティリティ以外のデータ コレクション セットがある場合、このプロシージャでは UMDW データベース (sysutility_mdw) が削除されません。 この場合、再度 UCP を作成するには、あらかじめ手動で UMDW データベース (sysutility_mdw) を削除しておく必要があります。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 このプロシージャは、`sysadmin` 権限を持つユーザーが実行する必要があります。この権限は、UCP の作成に必要な権限と同じです。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-remove-a-utility-control-point"></a>ユーティリティ コントロール ポイントを削除するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
```  
EXEC msdb.dbo.sp_sysutility_ucp_remove;  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server ユーティリティの機能とタスク](sql-server-utility-features-and-tasks.md)   
 [ユーティリティ エクスプローラーを使用した SQL Server ユーティリティの管理](use-utility-explorer-to-manage-the-sql-server-utility.md)   
 [SQL Server ユーティリティのトラブルシューティング](../../database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
