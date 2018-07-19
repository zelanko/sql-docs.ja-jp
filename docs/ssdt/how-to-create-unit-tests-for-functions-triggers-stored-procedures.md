---
title: 関数、トリガー、およびストアド プロシージャに対する SQL Server の単体テストを作成する方法 | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bda57c10-a1ab-4a1a-8a71-42085a3cb793
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: adb8d905c6ed2a5b3c6c20ec5feb595981920da8
ms.sourcegitcommit: 2f07d285824a8982c279f3816b220e61a2d91b06
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37094689"
---
# <a name="how-to-create-sql-server-unit-tests-for-functions-triggers-and-stored-procedures"></a>関数、トリガー、およびストアド プロシージャに対する SQL Server の単体テストを作成する方法
任意のデータベース オブジェクトに対する変更を評価する単体テストを作成できます。 ただし、SQL Server Data Tools には、SQL Server オブジェクト エクスプローラーのデータベース プロジェクト ノードから、データベースの関数、トリガー、およびストアド プロシージャのテストを作成するための追加サポートが含まれています。 Transact\-SQL コード スタブを自動的に生成して、カスタマイズすることができます。  
  
### <a name="to-create-a-sql-server-unit-test-from-a-function-trigger-or-stored-procedure"></a>関数、トリガー、またはストアド プロシージャから SQL Server の単体テストを作成するには  
  
1.  ストアド プロシージャの単体テストを追加する例については、「[チュートリアル: SQL Server の単体テストの作成と実行](../ssdt/walkthrough-creating-and-running-a-sql-server-unit-test.md)」の「ストアド プロシージャに対して SQL Server の単体テストを作成するには」セクションを参照してください。  
  
    結果不確定のテスト条件は、すべてのテストに追加される既定の条件です。 このテスト条件は、テストの検証が実装されていないことを示すために含まれています。 このテスト条件は、他のテスト条件を追加した後に、テストから削除します。 詳細については、「[方法: データベース単体テストにテスト条件を追加する](../ssdt/how-to-add-test-conditions-to-sql-server-unit-tests.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[SQL Server の単体テストの作成と定義](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
[空の SQL Server の単体テストを作成する方法](../ssdt/how-to-create-an-empty-sql-server-unit-test.md)  
  
