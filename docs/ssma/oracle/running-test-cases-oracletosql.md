---
title: テスト_ケース (OracleToSQL) を実行している |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc208cdb-7373-4f6b-8f6c-cdff9d3dcd02
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: bff5a571a8ad60e2baa3ea1211d6aff97c01c5ea
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="running-test-cases-oracletosql"></a>テスト_ケース (OracleToSQL) を実行します。
SSMA テスト担当者がテスト_ケースを実行すると、テスト用に選択されたオブジェクトを実行し、検証結果に関するレポートを作成します。 結果が両方のプラットフォームで同一の場合、テストが成功しました。 Oracle 間のオブジェクトの対応付けと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SSMA プロジェクトを現在のスキーマ マッピングの設定に従って決定されます。  
  
成功したテストのために必要な要件は、Oracle のすべてのオブジェクトが変換され、ターゲット データベースに読み込まれることです。 また、両方のプラットフォーム上のテーブルの内容が同期されるようにテーブルのデータを移行する必要があります。  
  
## <a name="run-test-case"></a>テスト_ケースを実行します。  
準備された場合は、テスト_ケースを実行します。  
  
1.  クリックして、**実行**ボタンをクリックします。  
  
2.  **Connect to Oracle**ダイアログ ボックスでは、接続情報を入力し、をクリックして**接続**です。  
  
テストが完了したら、テスト_ケースのレポートが作成されます。 クリックして、**レポート**を表示するボタン、[テスト_ケース レポート](http://msdn.microsoft.com/en-us/8da14323-9dd6-4019-bf79-3e8b972a9bc0)です。 テスト (テスト ケース レポート) の結果がで自動的に格納されている、[テストの結果リポジトリ](http://msdn.microsoft.com/en-us/f941cce4-d3e3-4aeb-a88a-4f101a97a9f4)を後で使用します。  
  
## <a name="test-case-execution-steps"></a>テスト_ケースの実行手順  
  
### <a name="prerequisites"></a>前提条件  
SSMA テスターは、テストの開始前にテストの実行のすべての前提条件を満たしているかどうかを確認します。 一部の条件が満たされない場合、エラー メッセージが表示されます。  
  
### <a name="initialization"></a>初期化  
この手順には、SSMA テスターは、Oracle サーバーの SSMATESTER_ORACLE スキーマで補助オブジェクト (テーブル、トリガー、およびビュー) を作成します。 検証の選択の影響を受けるオブジェクトに行われた変更によってトレース可能になります。  
  
検証済みのテーブルが USER_TABLE をという名前のものとします。 このようなテーブルの場合は、次の補助オブジェクトは Oracle に作成されます。  
  
||||  
|-|-|-|  
|名前|型|Description|  
|USER_TABLE$ Trg|トリガー (trigger)|検証済みのテーブルで変更の監査をトリガーします。|  
|USER_TABLE$ AUD|テーブル|テーブルな行が削除され、上書きを保存します。|  
|USER_TABLE$ AUDID|テーブル|追加または変更された行が保存されているテーブルです。|  
|USER_TABLE|view|テーブルの変更の簡略化された表現。|  
|USER_TABLE $ 新規|view|挿入、および上書きされた行の簡略化された表現。|  
|USER_TABLE$ NEW_ID|view|挿入および変更された行の id です。|  
|USER_TABLE$ 古い|view|行が削除され、上書きの簡略化された表現。|  
  
次のオブジェクトが上の確認済みのテーブルのスキーマに作成[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
||||  
|-|-|-|  
|名前|型|Description|  
|USER_TABLE$ Trg|トリガー (trigger)|検証済みのテーブルで変更の監査をトリガーします。|  
  
次のオブジェクトを作成および[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ssmatesterdb データベースにします。  
  
||||  
|-|-|-|  
|名前|型|Description|  
|USER_TABLE$ Aud|テーブル|テーブルな行が削除され、上書きを保存します。|  
|USER_TABLE$AudID|テーブル|追加または変更された行が保存されているテーブルです。|  
|USER_TABLE|view|テーブルの変更の簡略化された表現。|  
|USER_TABLE$new|view|挿入、および上書きされた行の簡略化された表現。|  
|USER_TABLE$new_id|view|挿入および変更された行の id です。|  
|USER_TABLE$old|view|行が削除され、上書きの簡略化された表現。|  
  
### <a name="test-object-calls"></a>テスト オブジェクトを呼び出し、  
この手順で、SSMA テスター、テスト用に選択した各オブジェクトを呼び出します、した結果を比較およびレポートを示しています。  
  
### <a name="finalization"></a>最終処理  
SSMA テスターがで作成された補助オブジェクトをクリーンアップ、終了処理中に、**初期化**手順です。  
  
## <a name="next-step"></a>次の手順  
[テスト_ケースのレポートを表示する&#40;OracleToSQL&#41;](../../ssma/oracle/viewing-test-case-reports-oracletosql.md)  
  
## <a name="see-also"></a>参照  
[選択して、テストするオブジェクトを構成&#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-objects-to-test-oracletosql.md)  
[影響を受けたオブジェクトの選択と構成&#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
[データベース オブジェクトを移行テスト&#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
