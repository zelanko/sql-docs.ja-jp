---
title: INSERT ステートメントまたは UPDATE ステートメントに対して外部キー制約を無効にする方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- constraints [SQL Server], foreign keys
- foreign keys [SQL Server], disabling constraints
- disabling constraints
- UPDATE statement [SQL Server], foreign key constraints
- INSERT statement [SQL Server], foreign key constraints
ms.assetid: 029168d7-085e-4b13-9b86-5644b67c6e24
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f37ba3c296e74a2c095f5ac9af5deb581491fa5a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179073"
---
# <a name="disable-foreign-key-constraints-with-insert-and-update-statements"></a>INSERT ステートメントまたは UPDATE ステートメントに対して外部キー制約を無効にする方法
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、INSERT トランザクションまたは UPDATE トランザクションの実行中に外部キー制約を無効にできます。 新しいデータが既存の制約に違反することがわかっている場合、またはデータベース内の既存のデータのみに制約を適用する場合に、このオプションを使用します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   **以下を使用して INSERT ステートメントまたは UPDATE ステートメントに対して外部キー制約を無効にするには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
 これらの制約を無効にすると、今後列に行われる挿入または更新は、制約条件に対して検証されません。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 テーブルに対する ALTER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-disable-a-foreign-key-constraint-for-insert-and-update-statements"></a>INSERT ステートメントまたは UPDATE ステートメントに対して外部キー制約を無効にするには  
  
1.  **オブジェクト エクスプローラー**で、制約が含まれているテーブルを展開し、 **[キー]** フォルダーを展開します。  
  
2.  制約を右クリックし、 **[変更]** をクリックします。  
  
3.  **[テーブル デザイナー]** の下のグリッドで、 **[外部キーの制約を適用]** をクリックし、ドロップダウン ボックスの一覧の **[いいえ]** をクリックします。  
  
4.  **[閉じる]** をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-disable-a-foreign-key-constraint-for-insert-and-update-statements"></a>INSERT ステートメントまたは UPDATE ステートメントに対して外部キー制約を無効にするには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Purchasing.PurchaseOrderHeader  
    NOCHECK CONSTRAINT FK_PurchaseOrderHeader_Employee_EmployeeID;  
    GO  
    ```  
  
 詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」を参照してください。  
  
###  <a name="TsqlExample"></a>  
