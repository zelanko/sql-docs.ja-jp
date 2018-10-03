---
title: テスト_ケースのレポート (OracleToSQL) の表示 |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8da14323-9dd6-4019-bf79-3e8b972a9bc0
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: ce59e126ce24e30e091b4a5456d8b78c84355e88
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47641770"
---
# <a name="viewing-test-case-reports-oracletosql"></a>テスト ケースのレポートの表示 (OracleToSQL)
テスト_ケースのレポートは、テスト検証の結果とテストの一般的な情報を示します。 失敗した場合、テスト、検証済みのオブジェクト内の一致しないデータに関する情報も表示されます。  
  
## <a name="report-structure"></a>レポートの構造  
レポートの上部では、これらの統計情報を示します。  
  
-   テスト対象のオブジェクトと、テストが成功したオブジェクトの数の合計数。  
  
-   検証済みのテーブルと外部キーの合計数とテーブルと外部キーが正常に一致の数。  
  
-   開始時刻、テスト ケースの終了時刻と実行にかかった合計時間。  
  
レポートの残りの部分では、4 つのカテゴリの情報が表示されます。  
  
**前提条件エラー**  
発生したエラーをすべて表示、**の前提条件手順。** 通常、これはスキップされます。  
  
**初期化**  
としての実行の状態を表示**成功**または**エラー**します。  
  
**テスト結果のオブジェクト**  
結果 (成功または失敗) と SSMA テスターの検出エラーが発生した場合の不一致を比較します。  
  
**終了処理**  
としての実行の状態を表示**成功**または**エラー**します。  
  
## <a name="see-also"></a>参照  
[テスト_ケースを実行している&#40;OracleToSQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[移行されたデータベース オブジェクトのテスト&#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
