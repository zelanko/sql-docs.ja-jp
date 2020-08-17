---
description: テスト ケースのレポートの表示 (OracleToSQL)
title: テストケースレポートの表示 (OracleToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8da14323-9dd6-4019-bf79-3e8b972a9bc0
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 62dfe8db323cfbf640ca1dc0f7df5e0c78aec3a7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88320038"
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
前提条件の手順で発生したすべてのエラーを表示 **します。** 通常はスキップされます。  
  
**初期化**  
実行の状態を **成功** または **失敗**として表示します。  
  
**テストオブジェクトの結果**  
結果 (成功または失敗) と SSMA Tester が障害発生時に検出した不一致の比較。  
  
**最終**  
実行の状態を **成功** または **失敗**として表示します。  
  
## <a name="see-also"></a>参照  
[OracleToSQL&#41;&#40;のテストケースの実行 ](../../ssma/oracle/running-test-cases-oracletosql.md)  
[移行されたデータベースオブジェクト &#40;OracleToSQL&#41;のテスト ](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
