---
title: "結合フィルター | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "フィルター [SQL Server レプリケーション]、結合"
  - "パブリケーション [SQL Server レプリケーション]、結合フィルター"
  - "マージ レプリケーションの結合フィルター [SQL Server レプリケーション]"
  - "結合フィルター"
ms.assetid: dd78fd8f-56e3-4582-9abd-6bc25c91e075
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# 結合フィルター
  結合フィルターを使用すると、パブリケーションにおける関連するテーブルのフィルター方法に基づいて、テーブルにフィルターを適用できます。 通常、親テーブルにはパラメーター化されたフィルターが使用されます。そのため、テーブル間の結合を定義する場合とほぼ同じ方法で 1 つ以上の結合フィルターを定義できます。 結合フィルターは、結合フィルター句に一致した場合のみ関連テーブルのデータがレプリケートされるように、パラメーター化されたフィルターを拡張します。  
  
 通常、結合フィルターは適用先のテーブルに定義されている主キー/外部キーのリレーションシップに従いますが、これに厳密に限定されてはいません。 結合フィルターには、2 つのテーブルの関連データを比較するためのあらゆるロジックを使用できます。  
  
 [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] サンプル データベースの次のテーブルを検討してみましょう。これらのテーブルは主キーと外部キーのリレーションシップによって関連付けられています。  
  
-   **HumanResources.Employee**  
  
-   **Sales.SalesOrderHeader**  
  
-   **Sales.SalesOrderDetail**  
  
 移動営業部門をサポートするために、アプリケーションでこれらのテーブルを使用する可能性がありますが、各ようにフィルター選択する必要があります内の販売員、 **HumanResources.Employee** テーブルは、顧客の注文に関連するデータのみを受信します。  
  
 最初の手順があり、この例では、親テーブルにパラメーター化されたフィルターを定義するには、 **HumanResources.Employee** テーブルです。 このテーブルには、列が含まれています。 **LoginID**, 、フォーム内の各従業員のログインが含まれています *domain \login*します。 このテーブルにフィルターを適用して各従業員が関連データのみを受け取れるようにするには、パラメーター化されたフィルター句を次のように指定します。  
  
```  
LoginID = SUSER_SNAME()  
```  
  
 このフィルターにより、各従業員のサブスクリプションにはのみからのデータが含まれている、 **HumanResources.Employee** (ここでは、1 つの行) をその従業員に関連するテーブル。 詳しくは、「 [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md)」をご覧ください。  
  
 次の手順で、このフィルターを各関連テーブルに拡張します。フィルターの拡張に使用する構文は、2 つのテーブルの結合の指定に使用する構文とほぼ同じです。 最初の結合フィルター句を次のように指定します。  
  
```  
Employee.EmployeeID = SalesOrderHeader.SalesPersonID  
```  
  
 この指定により、各営業担当者に関連する注文データのみがサブスクリプションに格納されます。 2 つ目の結合フィルター句を次のように指定します。  
  
```  
SalesOrderHeader.SalesOrderID = SalesOrderDetail.SalesOrderID  
```  
  
 この指定により、各営業担当者の注文データに関連する詳細データのみがサブスクリプションに格納されます。 この例では、各ポイントで単一のテーブルが結合されていますが、複数のテーブルを結合することもできます。  
  
 パブリケーションの新規作成ウィザードで一度に 1 つの結合フィルターを追加できる、 **パブリケーションのプロパティ** ] ダイアログ ボックスで、またはこれらをプログラムで追加することができます。 パブリケーションの新規作成ウィザードを使用して結合フィルターを自動的に生成することもできます。このウィザードでテーブルの行フィルターを指定すると、すべての関連テーブルに対して結合フィルターが適用されます。 詳細については、次を参照してください。 [を定義し、結合フィルターの間でマージ アーティクルの変更](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md), 、[自動的に生成、設定の結合フィルターの間でマージ アーティクルと #40 です。SQL Server Management Studio と #41;](../../../relational-databases/replication/publish/automatically generate join filters between merge articles.md), 、および [アーティクルを定義](../../../relational-databases/replication/publish/define-an-article.md)します。  
  
## 結合フィルターのパフォーマンスの最適化  
 次のガイドラインに従うことにより、結合フィルターのパフォーマンスを最適化できます。  
  
-   結合フィルター階層のテーブル数を制限します。  
  
     結合フィルターを適用できるテーブル数に制限はありませんが、多数のテーブルにフィルターを適用すると、マージ処理中のパフォーマンスに大きく影響します。 テーブルが 5 つ以上の結合フィルターを生成する場合は、小さなテーブル、変更されないテーブル、プライマリ参照テーブルはフィルター選択しないという別の解決策を検討してください。 結合フィルターは、サブスクリプション間でパーティション分割する必要のあるテーブル間でのみ使用します。  
  
-   設定、 **結合一意キー** オプションを **True** の適切な場所です。  
  
     親テーブルの結合列が一意の場合、特別なパフォーマンスの最適化機能をマージ処理で利用できます。 結合条件は一意の列に基づいて、設定、 **結合一意キー** 結合フィルターのオプションです。 このオプション設定の詳細については、前のセクションに示されている操作方法のトピックを参照してください。  
  
-   結合フィルターで参照される列にインデックスが作成されていることを確認します。  
  
     結合フィルターで参照される列にインデックスを作成すると、レプリケーションのフィルター処理がより効率的に実行されます。  
  
-   結合フィルターと同様の処理をする行フィルターは作成しないでください。  
  
     WHERE 句にサブクエリを使用すると、結合フィルターと同様の処理の行フィルターを次のように作成できます。  
  
    ```  
    WHERE Customer.SalesPersonID IN (SELECT EmployeeID FROM Employee WHERE LoginID = SUSER_SNAME())   
    ```  
  
     上記のようなロジックを使用する場合、サブクエリではなく結合フィルターを使用することを強くお勧めします。 アプリケーションでサブクエリを使用する行フィルターが必要な場合は、サブクエリが参照するデータが変更されない読み取り専用データであることを確認してください。  
  
## 参照  
 [マージ レプリケーション用にパブリッシュされたデータのフィルター選択](../../../relational-databases/replication/merge/filter-published-data-for-merge-replication.md)   
 [パラメーター化された行フィルター](../../../relational-databases/replication/merge/parameterized-row-filters.md)  
  
  