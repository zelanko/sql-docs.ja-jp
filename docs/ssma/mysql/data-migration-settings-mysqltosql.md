---
title: データ移行の設定 (MySQLToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9c396df4-5676-4f32-9c57-70d4f15f9b7a
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 90f76ef4d52fd5a1b7ed04d268954d0fed756324
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51681150"
---
# <a name="data-migration-settings-mysqltosql"></a>データ移行の設定 (MySQLToSQL)
  
## <a name="data-migration-settings"></a>データの移行設定  
**データ移行の設定**データ移行のためのカスタム クエリを記述できます。  
  
-   このタブは、使用可能な場合に**データ移行のオプションの拡張**に設定されている**表示**と非表示設定した場合に**を非表示に**プロジェクト設定。 プロジェクトの移行設定の詳細については、[プロジェクトの設定 (移行)](https://msdn.microsoft.com/2a3cba9e-cd54-4a8b-b858-8fc4cf2580d9)を参照してください。  
  
-   実装するカスタム SQL ステートメントの解析**データ移行の設定**テーブル ノードのタブ。  
  
-   使用できる 2 つのチェック ボックスは次のとおり、**データの移行設定**viz。  
  
    1.  SQL Server テーブルを切り捨てる  
  
    2.  カスタムの使用を選択します  
  
1.  **SQL Server テーブルを切り捨てます。**  
     このオプションは、ユーザーに対象のデータベースに移行したデータを明確に表示できます。  
  
    -   既定では、このテキスト ボックスがチェックされます。  
  
    -   このテキスト ボックスがオフの場合は、対象のデータベースに既存のデータに移行されるデータが追加されます。  
  
2.  **カスタムの使用を選択します。**  
     このオプションを変更するユーザーを使用する、**選択**ステートメントが存在する (**選択**ステートメントには、対象のデータベースに表示されるデータを選択できます)。  
  
    1.  既定ではこのテキスト ボックスがオフになっています。  
  
    2.  このテキスト ボックスをオンにしたかどうかは、ユーザーを変更できます、**選択**ステートメントが存在します。  
  
存在する 2 つのボタンを viz。  
  
-   **適用:** クリックして**適用**変更されている設定を適用します。  
  
-   **[キャンセル]:** クリックして**キャンセル**変更が行われた前に、現在の設定を復元します。  
  
## <a name="see-also"></a>参照  
[SQL Server または SQL Azure への MySQL データの移行](https://msdn.microsoft.com/a6a7f4d6-68aa-4a38-93bf-53eba0d7dc82)  
  
