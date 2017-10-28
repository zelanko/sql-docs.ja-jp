---
title: "データベース マスター キーの復元 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- database master key [SQL Server], importing
ms.assetid: 16897cc5-db8f-43bb-a38e-6855c82647cf
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c2833a4b91d4465e126c0a393e756ab09106d1c8
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="restore-a-database-master-key"></a>データベース マスター キーの復元
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] を使用して [!INCLUDE[tsql](../../../includes/tsql-md.md)]でデータベース マスター キーを復元する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   [Transact-SQL を使用してデータベース マスター キーを復元するには](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   マスター キーを復元するとき、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では現在アクティブなマスター キーによって暗号化されたすべてのキーの暗号化が解除された後、復元されたマスター キーを使用してこれらのキーが暗号化されます。 この操作はリソースを大量に消費するため、リソース要求が少ないときに実行するように考慮してください。 現在のデータベースのマスター キーが開いていないか、開けない場合、またはマスター キーで暗号化されたキーを 1 つでも暗号化解除できない場合、復元操作は失敗します。  
  
-   暗号化解除が 1 つでも失敗した場合、復元は失敗します。 FORCE オプションを使用するとエラーを無視できますが、暗号化を解除できないデータが失われる可能性があります。  
  
-   マスター キーがサービス マスター キーで暗号化されている場合は、復元されたマスター キーもサービス マスター キーで暗号化されます。  
  
-   現在のデータベースにマスター キーが存在しない場合は、RESTORE MASTER KEY を実行するとマスター キーが作成されます。 この新しいマスター キーは、サービス マスター キーで自動的に暗号化されません。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 データベースに対する CONTROL 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> Transact-SQL を備えた SQL Server Management Studio の使用  
  
#### <a name="to-restore-the-database-master-key"></a>データベース マスター キーを復元するには  
  
1.  バックアップしたデータベース マスター キーのコピーを、物理バックアップ メディアまたはローカル ファイル システム上のディレクトリから取得します。  
  
2.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。  
  
3.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
4.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    -- Restores the database master key of the AdventureWorks2012 database.  
    USE AdventureWorks2012;  
    GO  
    RESTORE MASTER KEY   
        FROM FILE = 'c:\backups\keys\AdventureWorks2012_master_key'   
        DECRYPTION BY PASSWORD = '3dH85Hhk003#GHkf02597gheij04'   
        ENCRYPTION BY PASSWORD = '259087M#MyjkFkjhywiyedfgGDFD';  
    GO  
    ```  
  
    > [!NOTE]  
    >  キーのファイル パスとキーのパスワード (存在する場合) は、実際は上に示したものと異なります。 両方がサーバーとキーのセットアップで固有であることをご確認ください。  
  
 詳細については、「[RESTORE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/restore-master-key-transact-sql.md)」を参照してください。  
  
  

