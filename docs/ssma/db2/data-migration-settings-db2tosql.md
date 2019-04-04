---
title: データ移行の設定 (DB2ToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 573e673e-a194-4cb2-9aba-aaac6e1a225c
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 7dbdee734d6d8a1dac825ad8f502c5851f746f42
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51681080"
---
# <a name="data-migration-settings-db2tosql"></a>データ移行の設定 (DB2ToSQL)
  
## <a name="data-migration-settings"></a>データの移行設定  
**データ移行の設定**データ移行のためのカスタム クエリを記述できます。  
  
-   このタブは、使用可能な場合に**データ移行のオプションの拡張**に設定されている**表示**と非表示設定した場合に**を非表示に**プロジェクト設定。 プロジェクトの移行設定の詳細については、[プロジェクトの設定 (移行)](https://msdn.microsoft.com/48aaa8e6-a9cb-487d-9ba5-fc3f1c4786ae)を参照してください。  
  
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
[SQL Server への DB2 データの移行](https://msdn.microsoft.com/86cbd39f-6dac-409a-9ce1-7dd54403f84b)  
  
