---
title: "テスト_ケースのレポート (OracleToSQL) の表示 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8da14323-9dd6-4019-bf79-3e8b972a9bc0
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 99ee650698adb2536ebdcadf480ae0ccefda2628
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="viewing-test-case-reports-oracletosql"></a>テスト_ケースのレポートの表示 (OracleToSQL)
テスト_ケースのレポートは、テストの検証の結果とテストの一般的な情報を示します。 障害の発生、テスト、検証済みのオブジェクト内の一致しないデータに関する情報も表示されます。  
  
## <a name="report-structure"></a>レポートの構造体  
レポートの上部では、これらの統計情報を示します。  
  
-   テスト対象のオブジェクトと、テストが成功したオブジェクトの数の合計数。  
  
-   検証済みのテーブルと外部キーの合計数とテーブルと外部キーが正常に一致の数。  
  
-   開始時刻、終了時刻の場合は、テスト_ケースおよび実行にかかった合計時間です。  
  
レポートの残りの部分は、4 つのカテゴリ内の情報を示します。  
  
**前提条件のエラー**  
発生したエラーを示しています、**前提条件手順です。** 通常、これはスキップされます。  
  
**初期化**  
としての実行の状態を示しています。**成功**または**エラー**です。  
  
**オブジェクトのテスト結果**  
結果 (成功または失敗) と SSMA テスト担当者が障害発生時検出の不一致の比較できます。  
  
**最終処理**  
としての実行の状態を示しています。**成功**または**エラー**です。  
  
## <a name="see-also"></a>参照  
[実行するテスト_ケース &#40;OracleToSQL"&"#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[データベース オブジェクト &#40;OracleToSQL"&"#41; 移行テスト](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  

