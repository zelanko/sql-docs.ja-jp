---
title: 方法:関数、トリガー、ストアド プロシージャに対する SQL Server の単体テストを作成する | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: bda57c10-a1ab-4a1a-8a71-42085a3cb793
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 5d985e2b2638d8b0047f5b4d010d87c8f631af65
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65090224"
---
# <a name="how-to-create-sql-server-unit-tests-for-functions-triggers-and-stored-procedures"></a>方法:関数、トリガー、およびストアド プロシージャに対する SQL Server の単体テストを作成する
任意のデータベース オブジェクトに対する変更を評価する単体テストを作成できます。 ただし、SQL Server Data Tools には、SQL Server オブジェクト エクスプローラーのデータベース プロジェクト ノードから、データベースの関数、トリガー、およびストアド プロシージャのテストを作成するための追加サポートが含まれています。 Transact\-SQL コード スタブを自動的に生成して、カスタマイズすることができます。  
  
### <a name="to-create-a-sql-server-unit-test-from-a-function-trigger-or-stored-procedure"></a>関数、トリガー、またはストアド プロシージャから SQL Server の単体テストを作成するには  
  
1.  ストアド プロシージャの単体テストを追加する例については、「[チュートリアル:SQL Server の単体テストの作成と実行](../ssdt/walkthrough-creating-and-running-a-sql-server-unit-test.md)」の「ストアド プロシージャに対して SQL Server の単体テストを作成するには」セクションを参照してください。  
  
    結果不確定のテスト条件は、すべてのテストに追加される既定の条件です。 このテスト条件は、テストの検証が実装されていないことを示すために含まれています。 このテスト条件は、他のテスト条件を追加した後に、テストから削除します。 詳細については、「[ソフト NUMA を使用するようにSQL Server の単体テストにテスト条件を追加する方法](../ssdt/how-to-add-test-conditions-to-sql-server-unit-tests.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[SQL Server の単体テストの作成と定義](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
[方法:空の SQL Server の単体テストを作成する方法](../ssdt/how-to-create-an-empty-sql-server-unit-test.md)  
  
