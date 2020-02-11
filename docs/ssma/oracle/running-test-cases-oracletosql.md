---
title: テストケースの実行 (OracleToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: fc208cdb-7373-4f6b-8f6c-cdff9d3dcd02
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 79d3905c130e37c973a79a40369f97ae8f30ac5b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68266549"
---
# <a name="running-test-cases-oracletosql"></a>テスト ケースの実行 (OracleToSQL)
SSMA Tester がテストケースを実行すると、テスト用に選択されたオブジェクトが実行され、検証結果に関するレポートが作成されます。 結果が両方のプラットフォームで同一の場合、テストは成功しました。 Oracle と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の間のオブジェクトの対応は、現在の ssma プロジェクトのスキーママッピングの設定に従って決定されます。  
  
テストを成功させるために必要な要件は、すべての Oracle オブジェクトが変換され、ターゲットデータベースに読み込まれることです。 また、両方のプラットフォームのテーブルの内容が同期されるように、テーブルデータを移行する必要があります。  
  
## <a name="run-test-case"></a>テストケースの実行  
準備されたテストケースを実行するには:  
  
1.  [**実行**] ボタンをクリックします。  
  
2.  [ **Oracle への接続**] ダイアログボックスで、接続情報を入力し、[**接続**] をクリックします。  
  
テストが完了すると、テストケースレポートが作成されます。 [**レポート**] ボタンをクリックして、[テストケースレポート](viewing-test-case-reports-oracletosql.md)を表示します。 テストの結果 (テストケースレポート) は、後で使用できるように、[テスト結果リポジトリ](using-test-repositories-oracletosql.md)に自動的に格納されます。  
  
## <a name="test-case-execution-steps"></a>テストケースの実行ステップ  
  
### <a name="prerequisites"></a>前提条件  
SSMA Tester は、テストを開始する前に、テストの実行ですべての前提条件が満たされているかどうかを確認します。 条件が満たされていない場合は、エラーメッセージが表示されます。  
  
### <a name="initialization"></a>初期化する  
この手順で、SSMA Tester は、Oracle サーバーの SSMATESTER_ORACLE スキーマに補助オブジェクト (テーブル、トリガー、およびビュー) を作成します。 検証用に選択された影響を受けるオブジェクトで行われた変更のトレースを許可します。  
  
検証されたテーブルに USER_TABLE という名前が付けられているとします。 このようなテーブルの場合、次の補助オブジェクトが Oracle で作成されます。  
  
||||  
|-|-|-|  
|Name|種類|[説明]|  
|USER_TABLE $ Trg|トリガー (trigger)|検証されたテーブルの変更の監査をトリガーします。|  
|USER_TABLE $ AUD|テーブル|削除された行と上書きされた行が保存されるテーブル。|  
|USER_TABLE $ AUDID|テーブル|新しい行と変更された行が保存されるテーブル。|  
|USER_TABLE|view|テーブル変更の簡略化された表現。|  
|USER_TABLE $ NEW|view|挿入行と上書き行の簡略化された表現。|  
|USER_TABLE $ NEW_ID|view|挿入および変更された行の識別。|  
|USER_TABLE $ OLD|view|削除行と上書き行の簡略化された表現。|  
  
次のオブジェクトは、で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]検証されたテーブルのスキーマで作成されます。  
  
||||  
|-|-|-|  
|Name|種類|[説明]|  
|USER_TABLE $ Trg|トリガー (trigger)|検証されたテーブルの変更の監査をトリガーします。|  
  
次のオブジェクトは、ssmatesterdb データベース[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のに作成されます。  
  
||||  
|-|-|-|  
|Name|種類|[説明]|  
|USER_TABLE $ Aud|テーブル|削除された行と上書きされた行が保存されるテーブル。|  
|USER_TABLE $ AudID|テーブル|新しい行と変更された行が保存されるテーブル。|  
|USER_TABLE|view|テーブル変更の簡略化された表現。|  
|USER_TABLE $ new|view|挿入行と上書き行の簡略化された表現。|  
|USER_TABLE $ new_id|view|挿入および変更された行の識別。|  
|USER_TABLE $ old|view|削除行と上書き行の簡略化された表現。|  
  
### <a name="test-object-calls"></a>オブジェクト呼び出しのテスト  
この手順では、SSMA Tester はテスト用に選択された各オブジェクトを呼び出し、結果を比較して、レポートを表示します。  
  
### <a name="finalization"></a>最終  
終了処理中に、**初期化**ステップで作成された補助オブジェクトがクリーンアップされます。  
  
## <a name="next-step"></a>次のステップ  
[テストケースレポートの表示 &#40;OracleToSQL&#41;](../../ssma/oracle/viewing-test-case-reports-oracletosql.md)  
  
## <a name="see-also"></a>参照  
[&#40;OracleToSQL&#41;をテストするオブジェクトの選択と構成](../../ssma/oracle/selecting-and-configuring-objects-to-test-oracletosql.md)  
[影響を受けるオブジェクトの選択と構成 &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
[移行されたデータベースオブジェクト &#40;OracleToSQL&#41;のテスト](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
