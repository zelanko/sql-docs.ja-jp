---
title: "テスト_ケース (SybaseToSQL) を実行している |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords: Tester Component,Execution Steps
ms.assetid: 195ffdef-cfde-4bf4-a3ae-e7402bb07972
caps.latest.revision: "6"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 686e7701014a85e141fed9d4f9bbcecdb029f015
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="running-test-cases-sybasetosql"></a>テスト_ケース (SybaseToSQL) を実行します。
SSMA テスト担当者がテスト_ケースを実行すると、テスト用に選択されたオブジェクトを実行し、検証結果に関するレポートを作成します。 結果が両方のプラットフォームで同一の場合、テストが成功しました。 Sybase 間のオブジェクトの対応付けと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SSMA プロジェクトを現在のスキーマ マッピングの設定に従って決定されます。  
  
成功したテストのために必要な要件は、Sybase のすべてのオブジェクトが変換され、ターゲット データベースに読み込まれることです。 また、両方のプラットフォーム上のテーブルの内容が同期されるようにテーブルのデータを移行する必要があります。  
  
## <a name="run-test-case"></a>テスト_ケースを実行します。  
準備された場合は、テスト_ケースを実行します。  
  
1.  クリックして、**実行**ボタンをクリックします。  
  
2.  **Sybase への接続**ダイアログ ボックスでは、接続情報を入力し、をクリックして**接続**です。  
  
テストが完了したら、テスト_ケースのレポートが作成されます。 をクリックして、**レポート**を表示するボタン、[テスト_ケース レポートを表示する &#40;です。SybaseToSQL &#41;](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md). テスト (テスト ケース レポート) の結果がで自動的に格納されている、[テスト リポジトリの使用 &#40;です。SybaseToSQL &#41;](../../ssma/sybase/using-test-repositories-sybasetosql.md)を後で使用します。  
  
## <a name="test-case-execution-steps"></a>テスト_ケースの実行手順  
  
### <a name="prerequisites"></a>前提条件  
SSMA テスターは、テストの開始前にテストの実行のすべての前提条件を満たしているかどうかを確認します。 一部の条件が満たされない場合、エラー メッセージが表示されます。  
  
### <a name="initialization"></a>初期化  
この手順で、SSMA Tester オブジェクトを作成補助 (テーブル、トリガー、およびビュー) 両方で、Sybase、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 テーブルの比較モードの場合、検証に対して選択した影響を受けるテーブルで行われた変更によってトレースできる**のみが変更され**です。  
  
検証済みのテーブルが USER_TABLE をという名前のものとします。 このようなテーブルの場合は、次の補助オブジェクトが Sybase に作成されます。  
  
SSMATESTER2005db または SSMATESTER2008db データベース中および、Sybase で、次のオブジェクトが作成された[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ssmatesterdb_syb データベースにします。  
  
|名前|型|Description|  
|--------|--------|---------------|  
|USER_TABLE$ Trg|トリガー|検証済みのテーブルで変更の監査をトリガーします。|  
|USER_TABLE$ Aud|Table|テーブルな行が削除され、上書きを保存します。|  
|USER_TABLE$ AudID|Table|追加または変更された行が保存されているテーブルです。|  
|USER_TABLE|表示|テーブルの変更の簡略化された表現。|  
|新しい USER_TABLE $|表示|挿入、および上書きされた行の簡略化された表現。|  
|USER_TABLE$ new_id|表示|挿入および変更された行の id です。|  
|古い USER_TABLE $|表示|行が削除され、上書きの簡略化された表現。|  
  
Sybase で検証済みのテーブルのデータベースで次のオブジェクトを作成し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
|名前|型|Description|  
|--------|--------|---------------|  
|USER_TABLE$ Trg|トリガー|検証済みのテーブルで変更の監査をトリガーします。|  
  
### <a name="test-object-calls"></a>テスト オブジェクトを呼び出し、  
この手順で、SSMA テスター、テスト用に選択した各オブジェクトを呼び出します、した結果を比較およびレポートを示しています。  
  
### <a name="finalization"></a>最終処理  
SSMA テスターがで作成された補助オブジェクトをクリーンアップ、終了処理中に、**初期化**手順です。  
  
## <a name="next-step"></a>次の手順  
[テスト_ケースのレポートの表示 &#40;です。SybaseToSQL &#41;](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md)  
  
## <a name="see-also"></a>参照  
[選択とテスト &#40; オブジェクトの構成SybaseToSQL &#41;](../../ssma/sybase/selecting-and-configuring-objects-to-test-sybasetosql.md)  
[選択して、影響を受けるオブジェクト &#40; を構成します。SybaseToSQL &#41;](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md)  
[データベース オブジェクト &#40; 移行テストSybaseToSQL &#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
