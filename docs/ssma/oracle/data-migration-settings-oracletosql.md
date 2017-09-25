---
title: "データ移行の設定 (OracleToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91f7f558-025d-4f4d-ac2c-aa095e7d1ace
caps.latest.revision: 3
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9e92081e6dea57616636e2b404bce3a950ca8ea4
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="data-migration-settings-oracletosql"></a>データ移行の設定 (OracleToSQL)
  
## <a name="data-migration-settings"></a>データ移行の設定  
**データの移行設定**データ移行のためのカスタム クエリを記述することができます。  
  
-   このタブは、使用可能な場合に**拡張データの移行オプション**に設定されている**表示**に設定した場合は非表示と**を非表示に**プロジェクトの設定。 プロジェクトの移行設定の詳細については、次を参照してください。[プロジェクトの設定 (移行)](http://msdn.microsoft.com/en-us/fcd6b988-633b-4b2b-9f36-6368b5e86b60)です。  
  
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
  
存在する 2 つのボタンを viz  
  
-   **適用:**クリックして**適用**変更されている設定を適用します。  
  
-   **キャンセル:**クリックして**キャンセル**変更が加えの前に存在する設定を復元します。  
  
## <a name="see-also"></a>参照  
[SQL Server への Oracle データの移行](http://msdn.microsoft.com/en-us/e23c5268-41ed-4e55-9fe7-a11376202a13)  
  

