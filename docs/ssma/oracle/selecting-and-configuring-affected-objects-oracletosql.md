---
title: "影響を受けたオブジェクト (OracleToSQL) の選択と構成 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Columns Comparison Settings
- Selection of Affected Objects
ms.assetid: 545eeda2-9829-4187-a858-619a96b4b71d
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 75fd62bd569709733c1915357057d9b8a88556e6
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="selecting-and-configuring-affected-objects-oracletosql"></a>影響を受けたオブジェクト (OracleToSQL) の選択と構成
このページでは、テーブルを選択して、SSMA、前の手順で選択されたオブジェクトの実行の結果を検証するときに、外部キーを変更とを比較する必要があります。 また、検証パラメーターをカスタマイズすることができます。  
  
## <a name="selection-of-affected-objects"></a>影響を受けるオブジェクトの選択  
Oracle オブジェクト ツリーで、ウィンドウの左側にある、テーブルと外部キーを確認する変更が同一になるに比較する必要があります。  
  
SSMA テスターは、これらのオブジェクトのいずれかを確認できない場合、は、ラベルの付いたリンクが表示されます**によって選択したオブジェクトには、エラーが含まれている**[オブジェクト] ツリー。 なぜこれらのオブジェクトを比較することはできません、上の理由からや不適切なオブジェクトの選択を解除するは、このリンクをクリックします。  
  
## <a name="table"></a>Table  
あるテーブル タブには、選択されたテーブルのグリッド ビューが含まれています。 グリッドには、選択したテーブルについては、次の情報が含まれています。  
  
-   列名  
  
-   データ型  
  
-   有効桁数  
  
-   Scale  
  
-   Rule  
  
-   既定値  
  
-   Identity  
  
-   [可]  
  
## <a name="sql"></a>Sql  
[SQL] タブには、"Create table"が含まれています。 選択されたテーブルの SQL です。  
  
## <a name="data"></a>Data  
[データ] タブでは、選択されたテーブル内のデータが表示されます。  
  
## <a name="properties"></a>プロパティ  
[プロパティ] タブには、選択したテーブルのプロパティが表示されます。 次のフィールド、[プロパティ] タブの下。  
  
-   作成または最後に変更されました。  
  
-   Object Name  
  
## <a name="columns-comparison-settings"></a>列の比較の設定  
テーブルの列に対して比較の規則を確立**列比較**ページ。 次の設定を行うことができます。  
  
### <a name="use-during-test-comparisons"></a>テストの比較の際に使用します。  
この列は、テスト結果の検証に参加するかどうかを決定します。  
  
-   選択した場合**True**SSMA は Oracle の SQL Server 内の列の内容と、テストの実行後にこの列の内容を比較します。 
  
-   選択した場合**False**列は、結果の検証から除外されます。  
  
### <a name="use-custom-scale"></a>カスタムのスケールを使用します。  
数値データ型の列の場合は、比較のためのカスタムのスケールを設定できます。  
  
-   選択した場合**True**によると、数値は丸められます、**を比較するスケール**値の比較がします。  
  
-   選択した場合**False**、数値比較を正確になります。  
  
### <a name="comparing-scale"></a>スケールの比較  
  
-   使用可能な場合にのみ、**使用縮尺**オプションに設定されて**True**です。 これは、数値比較の有効桁数です。  
  
### <a name="date-time-comparing"></a>日付時刻を比較します。  
定義方法、日付/時刻値が比較されます。  
  
-   選択した場合**全体の日付を比較**、両方のプラットフォームからの値の詳しい比較が行われます。  
  
-   選択した場合**日付のみを比較**、時刻部分は無視されます。  
  
-   選択した場合**時刻のみを比較**日付の部分は無視されます。  
  
-   選択した場合**(ミリ秒) を無視する**結果は、秒までと比較されます。  
  
-   選択した場合**無視日時 (ミリ秒)**、1 秒あたりの時間部分でのみ比較し、無視の小数部になります。  
  
### <a name="ignore-strings-case"></a>文字列の大文字小文字を区別します。  
比較の大文字小文字の区別を制御します。  
  
-   選択した場合**True**比較は大文字小文字を区別されます。  
  
-   選択した場合**False**大文字と小文字のアカウントは、比較します。  
  
## <a name="comparing-sql"></a>SQL の比較  
SSMA テスターによって生成された SELECT ステートメントを表示することができます、**を比較する SQL**ページ。 テスト担当者は、行ごとにこれらのステートメントの結果セットを比較します。 [次へ]、Oracle の結果セットの各行を SQL Server で生成された結果セットの次の行と同じにする必要があります。
  
カスタム検証を提供するような SELECT ステートメントを編集することができます。 Oracle および SQL Server ステートメントで変更を保存するには、**適用**これに対応して、ソースとターゲット SQL では、下にあるボタンをクリックします。  
  
## <a name="next-step"></a>次の手順  
[呼び出し順序 &#40;OracleToSQL&#41; のカスタマイズ](../../ssma/oracle/customizing-calls-order-oracletosql.md)  
  
## <a name="see-also"></a>参照  
[フィニッシュのテスト_ケース準備 &#40;OracleToSQL&#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
[実行するテスト_ケース &#40;OracleToSQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[データベース オブジェクト &#40;OracleToSQL&#41; 移行テスト](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  

