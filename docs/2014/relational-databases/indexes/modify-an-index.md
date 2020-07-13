---
title: インデックスの変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexes [SQL Server], modifying
- modifying indexes
- index changes [SQL Server]
ms.assetid: 97e3110d-fde7-4f5d-9309-dc1697960aeb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2af9293966afce8372f5b83a579418c546c82816
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85049860"
---
# <a name="modify-an-index"></a>インデックスの変更
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]のインデックスを変更する方法について説明します。  
  
> [!IMPORTANT]  
>  PRIMARY KEY 制約または UNIQUE 制約の結果として作成されたインデックスは、この方法を使用して変更することはできません。 このような場合には、制約を変更する必要があります。  
  
 **このトピックの内容**  
  
-   **インデックスを変更するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-modify-an-index"></a>インデックスを変更するには  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[データベース]** を展開し、テーブルが属するデータベースを展開して、 **[テーブル]** を展開します。  
  
3.  インデックスが属するテーブルを展開し、 **[インデックス]** を展開します。  
  
4.  変更するインデックスを右クリックし、 **[プロパティ]** をクリックします。  
  
5.  **[インデックスのプロパティ]** ダイアログ ボックスで、目的の変更を行います。 たとえば、インデックス キーの列の追加や削除を行うことができます。また、インデックス オプションの設定も変更できます。  
  
#### <a name="to-modify-index-columns"></a>インデックス列を変更するには  
  
1.  インデックス列の位置を追加、削除、または変更するには、 **[インデックスのプロパティ]** ダイアログ ボックスの **[全般]** ページをクリックします。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-modify-an-index"></a>インデックスを変更するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。 次の例では、 `ProductID` オプションを使って、 `Production.WorkOrder` テーブルの `DROP_EXISTING` 列にある既存のインデックスを削除して再作成します。 ここではオプション `FILLFACTOR` および `PAD_INDEX` も設定されています。  
  
     [!code-sql[IndexDDL#CreateIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/createindex.sql#createindex4)]  
  
     次の例では、ALTER INDEX を使用して、 `AK_SalesOrderHeader_SalesOrderNumber`インデックスのいくつかのオプションを設定します。  
  
     [!code-sql[IndexDDL#AlterIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex4)]  
  
#### <a name="to-modify-index-columns"></a>インデックス列を変更するには  
  
1.  インデックス列の位置を追加、削除、または変更するには、インデックスを削除してから再作成する必要があります。  
  
## <a name="see-also"></a>参照  
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)   
 [INDEXPROPERTY &#40;Transact-sql&#41;](/sql/t-sql/functions/indexproperty-transact-sql)   
 [SQL&#41;&#40;Transact-sql のインデックス](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)   
 [index_columns &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-index-columns-transact-sql)   
 [インデックスオプションの設定](set-index-options.md)   
 [インデックスの名前変更](indexes.md)  
  
  
