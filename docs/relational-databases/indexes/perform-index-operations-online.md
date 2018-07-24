---
title: オンラインでのインデックス操作の実行 | Microsoft Docs
ms.custom: ''
ms.date: 02/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- index online operations [SQL Server]
- online index operations
- ONLINE option
ms.assetid: 1e43537c-bf67-4db3-9908-3cb45c6fdaa1
caps.latest.revision: 32
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.suite: sql
ms.prod_service: table-view-index, sql-database
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 3d9494e5aec89a7a5d3b68e214b9561561aa9c07
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087324"
---
# <a name="perform-index-operations-online"></a>オンラインでのインデックス操作の実行
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、インデックスをオンラインで作成、再構築、または削除する方法について説明します。 ONLINE オプションにより、このようなインデックス操作中に、基になるテーブルやクラスター化インデックス データ、および関連付けられた任意の非クラスター化インデックスへの同時ユーザー アクセスが可能になります。 たとえば、あるユーザーがクラスター化インデックスを再構築している最中に、そのユーザーと他のユーザーが基になるデータの更新やクエリを続行できます。 クラスター化インデックスの構築や再構築などのデータ定義言語 (DDL) 操作をオフラインで実行するときは、これらの操作により、基になるデータや関連付けられたインデックスに排他ロックがかけられます。 このため、インデックス操作が完了するまで、基になるデータの変更やクエリを実行できません。  
  
> [!NOTE]  
>  オンラインでのインデックス操作は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのエディションで使用できるわけではありません。 詳細については、「SQL Server 2016 の各エディションがサポートする機能」を参照してください。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   **インデックスをオンラインで再構築するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   1 日 24 時間、週 7 日間、常時稼動のビジネス環境では、オンラインでのインデックス操作を実行することをお勧めします。このような環境では、インデックスの操作中に、ユーザーが同時に操作できることが必要不可欠です。  
  
-   次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで、ONLINE オプションを使用できます。  
  
    -   [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md)  
  
    -   [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md)  
  
    -   [DROP INDEX](../../t-sql/statements/drop-index-transact-sql.md)  
  
    -   [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) (CLUSTERED インデックス オプションが指定されている UNIQUE 制約または PRIMARY KEY 制約を追加または削除するため)  
  
-   オンラインでのインデックスの作成、再構築、または削除に関する制限と制約については、「 [オンライン インデックス操作のガイドライン](../../relational-databases/indexes/guidelines-for-online-index-operations.md)」を参照してください。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 テーブルまたはビューに対する ALTER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-rebuild-an-index-online"></a>インデックスをオンラインで再構築するには  
  
1.  オブジェクト エクスプローラーで、インデックスをオンラインで再構築するテーブルが格納されているデータベースをプラス記号をクリックして展開します。  
  
2.  **[テーブル]** フォルダーを展開します。  
  
3.  プラス記号をクリックして、オンラインでインデックスを再構築するテーブルを展開します。  
  
4.  **[インデックス]** フォルダーを展開します。  
  
5.  オンラインで再構築するインデックスを右クリックし、 **[プロパティ]** を選択します。  
  
6.  **[ページの選択]** の **[オプション]** を選択します。  
  
7.  **[DML のオンライン処理を許可する]** を選択し、一覧から **[True]** を選択します。  
  
8.  **[OK]** をクリックします。  
  
9. オンラインで再構築するインデックスを右クリックし、 **[再構築]** を選択します。  
  
10. **[インデックスの再構築]** ダイアログ ボックスで、 **[再構築するインデックス]** グリッドに目的のインデックスが表示されていることを確認し、 **[OK]** をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-create-rebuild-or-drop-an-index-online"></a>インデックスをオンラインで作成、再構築、または削除するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。 この例では、既存のインデックスをオンラインで再構築します。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER INDEX AK_Employee_NationalIDNumber ON HumanResources.Employee  
    REBUILD WITH (ONLINE = ON);  
    GO  
    ```  
  
     次の例では、クラスター化インデックスをオンラインで削除し、 `NewGroup` 句を使用することで、結果のテーブル (ヒープ) をファイル グループ `MOVE TO` に移動します。 移動の前後で `sys.indexes`、 `sys.tables`、および `sys.filegroups` カタログ ビューを参照し、ファイル グループ内のインデックスとテーブルの配置を確認します。  
  
     [!code-sql[IndexDDL#DropIndex4](../../relational-databases/indexes/codesnippet/tsql/perform-index-operations_1.sql)]  
  
 詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)」を参照してください。  
  
  
