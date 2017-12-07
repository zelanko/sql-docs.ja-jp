---
title: "データ移行の設定 (MySQLToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-mysql
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 9c396df4-5676-4f32-9c57-70d4f15f9b7a
caps.latest.revision: "9"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d7f7d4bfad187224a73aa793913715f7f17d7cc8
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="data-migration-settings-mysqltosql"></a>データ移行の設定 (MySQLToSQL)
  
## <a name="data-migration-settings"></a>データ移行の設定  
**データの移行設定**データ移行のためのカスタム クエリを記述することができます。  
  
-   このタブは、使用可能な場合に**拡張データの移行オプション**に設定されている**表示**に設定した場合は非表示と**を非表示に**プロジェクトの設定。 プロジェクトの移行設定の詳細については、次を参照してください。[プロジェクトの設定 (移行)](http://msdn.microsoft.com/en-us/2a3cba9e-cd54-4a8b-b858-8fc4cf2580d9)です。  
  
-   実装するカスタム SQL ステートメントの解析**データの移行設定**テーブル ノードのタブ。  
  
-   使用できる 2 つのチェック ボックスは次のとおり、**データの移行設定**viz。  
  
    1.  SQL Server テーブルを切り捨てる  
  
    2.  カスタムの使用を選択します。  
  
1.  **SQL Server テーブルを切り捨てます。**  
     このオプションでは、ユーザーが対象のデータベースに移行したデータを明確に表示します。  
  
    -   既定では、このテキスト ボックスがオンになっています。  
  
    -   このテキスト ボックスがオフの場合は、移行されるデータは対象のデータベースに既存のデータに追加されます。  
  
2.  **カスタムの使用を選択します。**  
     このオプションでは、ユーザーを変更する、**選択**ステートメントが存在 (**選択**ステートメントには、対象のデータベースに表示されるデータを選択できます)。  
  
    1.  既定では、このテキスト ボックスでは、チェックです。  
  
    2.  このテキスト ボックスをオンにしたかどうかは、ユーザーを変更することできます、**選択**ステートメントが存在します。  
  
存在する 2 つのボタンを viz。  
  
-   **適用:**クリックして**適用**変更されている設定を適用します。  
  
-   **キャンセル:**クリックして**キャンセル**変更が加えの前に存在する設定を復元します。  
  
## <a name="see-also"></a>参照  
[SQL Server または SQL azure の MySQL データの移行](http://msdn.microsoft.com/en-us/a6a7f4d6-68aa-4a38-93bf-53eba0d7dc82)  
  
