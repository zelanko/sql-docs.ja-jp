---
title: クエリを使用して既存のテーブルを編集する
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: 58f4de8e-97b4-4bcb-953f-f3d428432491
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: 56411bfffbaebeb07adf23b456a20523342db21d
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "75241414"
---
# <a name="how-to-edit-an-existing-table-using-queries"></a>クエリを使用して既存のテーブルを編集する方法

Transact\-SQL クエリを記述することによって、テーブルまたはそのデータの定義を編集することができます。 テーブルの表示またはテーブルへのデータ入力を視覚的に行うには、データ エディターを使用します。データ エディターの詳細については、「[接続されているデータベース開発](../ssdt/connected-database-development.md)」を参照してください。  
  
> [!WARNING]  
> 以下に示す手順では、「[接続されているデータベース開発](../ssdt/connected-database-development.md)」に示されているこれまでの手順で作成したエンティティを使用します。  
  
### <a name="to-edit-the-definition-of-an-existing-table"></a>既存のテーブルの定義を編集するには  
  
1.  **SQL Server オブジェクト エクスプローラー**で、**Trade** データベースの **[テーブル]** ノードを展開し、**dbo.Suppliers** を右クリックします。  
  
2.  テーブル スキーマをテーブル デザイナーで表示するには、 **[デザイナーの表示]** をクリックします。  
  
3.  **Address** 列の **[Null を許容]** チェック ボックスをオンにします。 直ちに、スクリプト ペイン内の対応するコードが `NULL` に変わります。  
  
4.  「[接続されているデータベースを Power Buffer で更新する方法](../ssdt/how-to-update-a-connected-database-with-power-buffer.md)」の手順に従ってデータベースを更新します。  
  
### <a name="to-populate-data-in-new-tables-using-a-transact-sql-query"></a>Transact\-SQL クエリを使用して新しいテーブルにデータを設定するには  
  
1.  **Trade** データベース ノードを右クリックし、 **[新しいクエリ]** をクリックします。  
  
2.  スクリプト ペインに次のコードを貼り付けます。  
  
    ```  
    insert into dbo.Suppliers values  
    (1, 'NorthWind Traders', 'Seattle, WA'),  
    (2, 'Contoso', 'Tacoma, WA')  
    GO  
  
    insert dbo.Customer values  
    (1, 'Fourth Coffee')  
    GO  
  
    insert dbo.Products values  
    (1, 'Apples', 0, 1, 1),  
    (2, 'Instant Coffee', 1, 2, 1)  
    GO  
    ```  
  
3.  **[クエリの実行]** をクリックして、このクエリを実行します。 行がテーブルに正しく追加されたことを示す次のメッセージが、**メッセージ** ペインに表示されます。  
  
**(2 行処理されました)(1 行処理されました)(2 行処理されました)**  
  
4.  スクリプト ペイン内のコードを次のコードで置き換えて、クエリを実行します。 このコードでは、`Products` テーブルに新しい行を追加し、`ShelfLife` を 6 に設定するように試行されます。  
  
    ```  
    insert dbo.Products values  
    (3, 'Potato Chips', 6, 1, 1)  
    GO  
    ```  
  
5.  **メッセージ** ペインには、`INSERT` の値を 5 未満に制限する既存の CHECK 制約と、`ShelfLife` ステートメントとが競合していることを示すメッセージが表示されます。 ステートメントが既存の制約に違反しているため、Products テーブルは更新されません。  
  
6.  コードを次のように変更し、クエリを再度実行します。 今回は行が正しく更新されます。  
  
    ```  
    insert dbo.Products values  
    (3, 'Potato Chips', 2, 1, 1)  
    GO  
    ```  
  
## <a name="see-also"></a>参照  
[テーブルとリレーションシップの管理およびエラーの修正](../ssdt/manage-tables-relationships-and-fix-errors.md)  
[Transact-SQL エディターを使用したスクリプトの編集と実行](../ssdt/use-transact-sql-editor-to-edit-and-execute-scripts.md)  
  
