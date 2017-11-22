---
title: "FROM またはサブクエリを使用した UPDATE を実装する | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 138f5b0e-f8a4-400f-b581-8062aebc62b6
caps.latest.revision: "4"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5de86bfa68d281e79f77b9578eff2385f20c0958
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="implementing-update-with-from-or-subqueries"></a>FROM またはサブクエリを使用した UPDATE を実装する
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

ネイティブにコンパイルされた T-SQL モジュールは FROM 句をサポートせず、UPDATE ステートメントのサブクエリをサポートしません (SELECT ではサポートされます)。 FROM 句を含む UPDATE ステートメントは、通常、テーブル値パラメーター (TVP) に基づいてテーブルの情報を更新するため、または AFTER トリガーでテーブルの列を更新するために使用されます。 

TVP に基づく更新のシナリオについては、「 [ネイティブ コンパイル ストアド プロシージャに MERGE 機能を実装する](../../relational-databases/in-memory-oltp/implementing-merge-functionality-in-a-natively-compiled-stored-procedure.md)」をご覧ください。 

次の例は、トリガーで実行される更新を示します。テーブルの LastUpdated 列が更新の後で現在の日時に更新されます。 回避策では、ID 列を含むテーブル変数、およびテーブル変数の行を反復処理して個々の更新を実行する WHILE ループを使用します。
  
元の T-SQL UPDATE ステートメントを次に示します。  
  
  
  
  
    UPDATE dbo.Table1  
        SET LastUpdated = SysDateTime()  
        FROM  
            dbo.Table1 t  
            JOIN Inserted i ON t.Id = i.Id;  
  
  
  

このセクションの T-SQL コード例は、良好なパフォーマンスを提供する回避策を示します。 回避策は、ネイティブ コンパイル トリガーで実装されます。 コードで注目すべき重要な点は次のとおりです。  
  
- dbo.Type1 という名前の型。これはメモリ最適化テーブル型です。  
- トリガーの WHILE ループ。  
  - ループは、Inserted から一度に 1 行ずつ取得します。  
  
  
  

    DROP TABLE IF EXISTS dbo.Table1;  
    go  
    DROP TYPE IF EXISTS dbo.Type1;  
    go  
    -----------------------------  
    <a name="---table-and-table-type"></a>-- テーブルとテーブル型
    -----------------------------
  
    CREATE TABLE dbo.Table1  
    (  
        Id           INT        NOT NULL  PRIMARY KEY NONCLUSTERED,  
        Column2      INT        NOT NULL,  
        LastUpdated  DATETIME2  NOT NULL  DEFAULT (SYSDATETIME())  
    )  
        WITH (MEMORY_OPTIMIZED = ON);  
    go  
  
  
    CREATE TYPE dbo.Type1 AS TABLE  
    (  
        Id       INT NOT  NULL,  
        
        RowID    INT NOT  NULL  IDENTITY,  
        INDEX ix_RowID HASH (RowID) WITH (BUCKET_COUNT=1024)
    )   
        WITH (MEMORY_OPTIMIZED = ON);  
    go  
    ----------------------------- 
    <a name="---trigger-that-contains-the-workaround-for-update-with-from"></a>-- FROM を使用する UPDATE に対する回避策を含むトリガー 
    -----------------------------  
  
    CREATE TRIGGER dbo.tr_a_u_Table1  
        ON dbo.Table1  
        WITH NATIVE_COMPILATION, SCHEMABINDING  
        更新後に  
    AS BEGIN ATOMIC WITH  
        (  
        TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
        LANGUAGE = N'us_english'  
        )  
        
      DECLARE @tabvar1 dbo.Type1;  
    
      INSERT @tabvar1 (Id)   
          SELECT Id FROM Inserted;  
    
      DECLARE  
          @i INT = 1,  @Id INT,  
          @max INT = SCOPE_IDENTITY();  
    
      ---- カーソルをシミュレートするための回避策としてループする。
    ---- メモリ最適化テーブル変数内の行を反復処理し、  
      ---- 各行の更新を実行する。  
    
      WHILE @i <= @max  
      BEGIN  
          SELECT @Id = Id  
              FROM @tabvar1  
              WHERE RowID = @i;  
    
          UPDATE dbo.Table1  
              SET LastUpdated = SysDateTime()  
              WHERE Id = @Id;  
    
          SET @i += 1;  
      END  
    END  
    go  
    -----------------------------  
    <a name="---test-to-verify-functionality"></a>-- 機能をテストして検証する
    -----------------------------  
  
    SET NOCOUNT ON;  
  
    INSERT dbo.Table1 (Id, Column2)  
        VALUES (1,9), (2,9), (3,600);  
    
    SELECT N'BEFORE-Update' AS [BEFORE-Update], *  
        FROM dbo.Table1  
        ORDER BY Id;  
  
    WAITFOR DELAY '00:00:01';  

    UPDATE dbo.Table1  
        SET   Column2 += 1  
        WHERE Column2 <= 99;  
  
    SELECT N'AFTER--Update' AS [AFTER--Update], *  
        FROM dbo.Table1  
        ORDER BY Id;  
    go  
    -----------------------------  
  
    /**** Actual output:  
  
    BEFORE-Update   Id   Column2   LastUpdated  
    BEFORE-Update   1       9      2016-04-20 21:18:42.8394659  
    BEFORE-Update   2       9      2016-04-20 21:18:42.8394659  
    BEFORE-Update   3     600      2016-04-20 21:18:42.8394659  
  
    AFTER--Update   Id   Column2   LastUpdated  
    AFTER--Update   1      10      2016-04-20 21:18:43.8529692  
    AFTER--Update   2      10      2016-04-20 21:18:43.8529692  
    AFTER--Update   3     600      2016-04-20 21:18:42.8394659  
    ****/  
  
  
  
