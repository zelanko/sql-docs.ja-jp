---
title: "複数行のデータを処理するための DML トリガーの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-dml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "複数行の DML トリガー"
  - "UPDATE ステートメント [SQL Server], DML トリガー"
  - "DELETE ステートメント [SQL Server], DML トリガー"
  - "複数行の DML トリガー [SQL Server]"
  - "INSERT ステートメント [SQL Server], DML トリガー"
  - "DML トリガー, 複数行"
ms.assetid: d476c124-596b-4b27-a883-812b6b50a735
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# 複数行のデータを処理するための DML トリガーの作成
  DML トリガーのコードを記述するときは、トリガーを起動するステートメントが、1 行だけではなく複数行のデータに影響する場合があることを考慮してください。 この動作は UPDATE トリガーや DELETE トリガーの場合によく見られます。UPDATE ステートメントや DELETE ステートメントが複数行に影響を与えることが多いためです。 INSERT トリガーの場合は、INSERT ステートメントが 1 行単位で追加を行うため、この動作はあまり見られません。 ただし、INSERT トリガーは INSERT INTO (*table_name*) SELECT ステートメントにより起動されることもあります。その場合は、1 回のトリガーの呼び出しで複数行が挿入される可能性があります。  
  
 複数行への影響について考慮することは、DML トリガーの機能によって 1 つのテーブルから自動的に集計値が再計算され、その結果を他のテーブルに保存して集計を続行するような場合は、特に重要です。  
  
> [!NOTE]  
>  パフォーマンスが低下する可能性があるので、トリガーにカーソルを使用することはお勧めしません。 複数行に影響を与えるトリガーを設計する場合は、カーソルではなく行セットをベースにしたロジックを使用してください。  
  
## 使用例  
 次の例の DML トリガーはどれも、ある列の集計の途中経過を [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースの別のテーブル内に保存するように設計されています。  
  
### A. 単一の行を挿入する場合の集計途中経過の格納  
 最初の例の DML トリガーは、`PurchaseOrderDetail` テーブルに 1 行のデータが追加される場合、つまり 1 行単位の挿入は問題なく実行できます。 INSERT ステートメントにより DML トリガーが起動され、トリガーの実行中に **inserted** テーブルに新しい行が追加されます。 `UPDATE` ステートメントでは行の `LineTotal` 列の値が読み取られ、その値が `SubTotal` テーブルの `PurchaseOrderHeader` 列の既存の値に加算されます。 `WHERE` 句により、`PurchaseOrderDetail` テーブルで更新された行が **inserted** テーブルの行の `PurchaseOrderID` に一致することが保証されます。  
  
```  
-- Trigger is valid for single-row inserts.  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER NewPODetail  
ON Purchasing.PurchaseOrderDetail  
AFTER INSERT AS  
   UPDATE PurchaseOrderHeader  
   SET SubTotal = SubTotal + LineTotal  
   FROM inserted  
   WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID ;  
```  
  
### B. 複数または単一の行を挿入する場合の集計途中経過の格納  
 複数行を挿入する場合は、例 A で示した DML トリガーは正しく実行されない可能性があります。UPDATE ステートメントの代入式の右側の式 (`SubTotal` + `LineTotal`) は必ず単一の値になり、値のリストを指定することはできません。 したがって、このトリガーの結果は、**inserted** テーブル内の 1 行から値を取得して、その値を、特定の `PurchaseOrderID` 値に対する `PurchaseOrderHeader` テーブルの既存の `SubTotal` 値に追加することになります。 この操作では、1 つの `PurchaseOrderID` が **inserted** テーブルに複数登録されている場合には、予想どおりの結果が得られないことがあります。  
  
 `PurchaseOrderHeader` テーブルを正しく更新するには、**inserted** テーブルに複数の行がある場合を考慮してトリガーを作成する必要があります。 これを行うには、`PurchaseOrderID` ごとに **inserted** テーブル内の行グループで `LineTotal` の合計を計算する `SUM` 関数を使用します。 `SUM` 関数は、相関サブクエリ (かっこ内の `SELECT` ステートメント) に指定します。 このサブクエリは、`PurchaseOrderHeader` テーブルの `PurchaseOrderID` に一致するか、これと相関関係にある **inserted** テーブルの `PurchaseOrderID` の各値を返します。  
  
```  
-- Trigger is valid for multirow and single-row inserts.  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER NewPODetail2  
ON Purchasing.PurchaseOrderDetail  
AFTER INSERT AS  
   UPDATE Purchasing.PurchaseOrderHeader  
   SET SubTotal = SubTotal +   
      (SELECT SUM(LineTotal)  
      FROM inserted  
      WHERE PurchaseOrderHeader.PurchaseOrderID  
       = inserted.PurchaseOrderID)  
   WHERE PurchaseOrderHeader.PurchaseOrderID IN  
      (SELECT PurchaseOrderID FROM inserted);  
```  
  
 このトリガーは 1 行だけの挿入でも正しく実行されます。この場合、`LineTotal` 値の列の合計は、1 つの行だけの値になります。 ただし、このトリガーでは、相関サブクエリと `IN` 句で使用されている `WHERE` 演算子のために、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] による追加の処理を必要とします。 これは、1 行単位の挿入操作の場合は必要ありません。  
  
### C. 挿入の種類に基づいた集計の途中経過の格納  
 処理対象の行数に応じて最適の方法を使用するようにトリガーを変更できます。 たとえば、1 行だけの挿入と複数行の挿入を区別するには、トリガーのロジックで `@@ROWCOUNT` 関数を使用します。  
  
```  
-- Trigger valid for multirow and single row inserts  
-- and optimal for single row inserts.  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER NewPODetail3  
ON Purchasing.PurchaseOrderDetail  
FOR INSERT AS  
IF @@ROWCOUNT = 1  
BEGIN  
   UPDATE Purchasing.PurchaseOrderHeader  
   SET SubTotal = SubTotal + LineTotal  
   FROM inserted  
   WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID  
END  
ELSE  
BEGIN  
      UPDATE Purchasing.PurchaseOrderHeader  
   SET SubTotal = SubTotal +   
      (SELECT SUM(LineTotal)  
      FROM inserted  
      WHERE PurchaseOrderHeader.PurchaseOrderID  
       = inserted.PurchaseOrderID)  
   WHERE PurchaseOrderHeader.PurchaseOrderID IN  
      (SELECT PurchaseOrderID FROM inserted)  
END;  
```  
  
## 参照  
 [DML トリガー](../../relational-databases/triggers/dml-triggers.md)  
  
  