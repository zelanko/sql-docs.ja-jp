---
title: データ移行の設定 (OracleToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 91f7f558-025d-4f4d-ac2c-aa095e7d1ace
caps.latest.revision: 3
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 9dd11d93fe40e65836f778191c025daba5a76d0d
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2018
ms.locfileid: "40393764"
---
# <a name="data-migration-settings-oracletosql"></a>データ移行の設定 (OracleToSQL)
  
## <a name="data-migration-settings"></a>データの移行設定  
**データ移行の設定**データ移行のためのカスタム クエリを記述できます。  
  
-   このタブは、使用可能な場合に**データ移行のオプションの拡張**に設定されている**表示**と非表示設定した場合に**を非表示に**プロジェクト設定。 プロジェクトの移行設定の詳細については、次を参照してください。[プロジェクトの設定 (移行)](http://msdn.microsoft.com/fcd6b988-633b-4b2b-9f36-6368b5e86b60)します。  
  
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
[SQL Server への Oracle データの移行](migrating-oracle-data-into-sql-server-oracletosql.md)  
  
