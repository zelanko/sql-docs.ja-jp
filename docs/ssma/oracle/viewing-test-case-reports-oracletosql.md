---
title: テストケースレポートの表示 (OracleToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8da14323-9dd6-4019-bf79-3e8b972a9bc0
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 75ce91d7948b53522f6ac861a078f8f902b23ab7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086788"
---
# <a name="viewing-test-case-reports-oracletosql"></a>テスト ケースのレポートの表示 (OracleToSQL)
テストケースレポートには、テスト検証の結果と一般的なテスト情報が表示されます。 テストエラーが発生した場合、検証されたオブジェクト内の一致しないデータに関する情報も表示されます。  
  
## <a name="report-structure"></a>レポート構造  
レポートの上部には、次の統計情報が表示されます。  
  
-   テストされたオブジェクトの合計数と、テストが成功したオブジェクトの数。  
  
-   検証されたテーブルと外部キーの合計数と、正常に一致したテーブルと外部キーの数。  
  
-   テストケースの開始時刻、終了時刻、および実行にかかった合計時間。  
  
レポートの残りの部分では、次の4つのカテゴリに情報が表示されます。  
  
**前提条件のエラー**  
前提条件の手順で発生したすべてのエラーを表示**します。** 通常はスキップされます。  
  
**イニシャライズ**  
実行の状態を**成功**または**失敗**として表示します。  
  
**テストオブジェクトの結果**  
結果 (成功または失敗) と SSMA Tester が障害発生時に検出した不一致の比較。  
  
**最終**  
実行の状態を**成功**または**失敗**として表示します。  
  
## <a name="see-also"></a>参照  
[OracleToSQL&#41;&#40;のテストケースの実行](../../ssma/oracle/running-test-cases-oracletosql.md)  
[移行されたデータベースオブジェクト &#40;OracleToSQL&#41;のテスト](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
