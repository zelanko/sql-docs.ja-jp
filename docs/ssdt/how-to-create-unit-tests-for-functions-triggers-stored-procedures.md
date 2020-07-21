---
title: 関数、トリガー、およびストアド プロシージャに対する SQL Server の単体テストを作成する
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: bda57c10-a1ab-4a1a-8a71-42085a3cb793
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: c7218f035ca907bf9052865408b3a7311e8f75b4
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "75241471"
---
# <a name="how-to-create-sql-server-unit-tests-for-functions-triggers-and-stored-procedures"></a>関数、トリガー、およびストアド プロシージャに対する SQL Server の単体テストを作成する方法

任意のデータベース オブジェクトに対する変更を評価する単体テストを作成できます。 ただし、SQL Server Data Tools には、SQL Server オブジェクト エクスプローラーのデータベース プロジェクト ノードから、データベースの関数、トリガー、およびストアド プロシージャのテストを作成するための追加サポートが含まれています。 Transact\-SQL コード スタブを自動的に生成して、カスタマイズすることができます。  
  
### <a name="to-create-a-sql-server-unit-test-from-a-function-trigger-or-stored-procedure"></a>関数、トリガー、またはストアド プロシージャから SQL Server の単体テストを作成するには  
  
1.  ストアド プロシージャの単体テストを追加する例については、「[チュートリアル: SQL Server の単体テストの作成と実行](../ssdt/walkthrough-creating-and-running-a-sql-server-unit-test.md)」の「ストアド プロシージャに対して SQL Server の単体テストを作成するには」セクションを参照してください。  
  
    結果不確定のテスト条件は、すべてのテストに追加される既定の条件です。 このテスト条件は、テストの検証が実装されていないことを示すために含まれています。 このテスト条件は、他のテスト条件を追加した後に、テストから削除します。 詳しくは、「[SQL Server の単体テストにテスト条件を追加する方法](../ssdt/how-to-add-test-conditions-to-sql-server-unit-tests.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
[SQL Server の単体テストの作成と定義](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
[空の SQL Server の単体テストを作成する方法](../ssdt/how-to-create-an-empty-sql-server-unit-test.md)  
  
