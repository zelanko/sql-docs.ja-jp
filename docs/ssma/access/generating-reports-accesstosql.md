---
title: レポート (AccessToSQL) の生成 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-access
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: abb4264a-622e-4215-af5b-14e309b8a399
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 3116ae117dc7e75a8efc4d898b1c2b18cae85759
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="generating-reports-accesstosql"></a>レポートの生成 (AccessToSQL)
オブジェクト ツリーのレベルで SSMA コンソールで、コマンドを使用して実行される特定のアクティビティのレポートが生成されます。  
  
レポートを生成するのにには、次の手順を使用します。  
  
1.  指定して、**書き込みで概要レポート-を**パラメーター。 (指定した場合)、ファイル名と関連するレポートが格納されているフォルダーにするかを指定します。 ファイル名は、where 句、次の表で説明したようにシステム定義済み**&lt;n&gt;** 同じコマンドの実行ごとに 1 桁の数字で増加する一意のファイル数です。  
  
    レポート vis à-vis コマンドは次のとおりです。  
  
    ||||  
    |-|-|-|  
    |**Sl. No.**|**Command**|**レポートのタイトル**|  
    |1|generate-assessment-report|AssessmentReport&lt;n&gt;です。XML|  
    |2|変換とスキーマ|SchemaConversionReport&lt;n&gt;です。XML|  
    |3|データの移行|DataMigrationReport&lt;n&gt;です。XML|  
    |4|同期ターゲット|TargetSynchronizationReport&lt;n&gt;です。XML|  
    |5|データベースからの更新|SourceDBRefreshReport&lt;n&gt;.XML|  
  
    > [!IMPORTANT]  
    > レポートの出力、評価レポートと異なります。 前者は、コマンドの実行中のパフォーマンスに関するレポート、後者は、プログラムによる使用量の XML レポートします。  
  
    コマンド オプションの出力からのレポート (上記の Sl. No. 2 ~ 4) を参照してください、 [SSMA コンソールを実行する&#40;AccessToSQL&#41; ](../../ssma/access/executing-the-ssma-console-accesstosql.md)セクションです。  
  
2.  詳細レポートの詳細設定を使用して、出力レポートに目的の範囲を指定します。  
  
    ||||  
    |-|-|-|  
    |**Sl. No.**|**コマンドとパラメーター**|**出力の説明**|  
    |1|verbose=”false”|アクティビティの集計レポートを生成します。|  
    |2|verbose=”true”|各アクティビティの概要と詳細の状態レポートを生成します。|  
  
    > [!NOTE]  
    > 上記で指定したレポートの詳細設定-評価-レポートの生成、変換とスキーマ、データの移行コマンド適切です。  
  
3.  詳細エラー報告の設定を使用して、エラー レポートに目的の範囲を指定します。  
  
    ||||  
    |-|-|-|  
    |**Sl. No.**|**コマンドとパラメーター**|**出力の説明**|  
    |1|report-errors=”false”|エラーの詳細情報なし/警告/情報メッセージです。|  
    |2|report-errors=”true”|詳細なエラー/警告/情報メッセージです。|  
  
    > [!NOTE]  
    > 上記で指定したエラー報告の設定は-評価-レポートの生成、変換とスキーマ、データの移行コマンドに適用します。  
  
**例:**  
  
```xml  
<generate-assessment-report  
  
    object-name="testschema"  
  
    object-type="Schemas"  
  
    verbose="yes"  
  
    report-erors="yes"  
  
    write-summary-report-to="$AssessmentFolder$\Report1.xml"  
  
    assessment-report-folder="$AssessmentFolder$\assesment_report"  
  
    assessment-report-overwrite="true"  
  
/>  
```  
  
### <a name="synchronize-target"></a>-ターゲットの同期:  
コマンドは、**同期ターゲット**が**レポートでエラーを**パラメーターで、同期操作のエラー レポートの場所を指定します。 次に、名前のファイルが**TargetSynchronizationReport&lt;n&gt;です。XML**指定した場所に作成された場所**&lt;n&gt;** 同じコマンドの実行ごとに 1 桁の数字で増加する一意のファイル数です。  
  
**注:** フォルダーのパスを指定するとかどうか、は、' レポートでエラーを 'パラメーターはコマンド' 同期ターゲット ' の省略可能な属性になります。  
  
```xml  
<!-- Example: Synchronize target entire Database with all attributes-->  
  
<synchronize-target  
  
    object-name="$TargetDB$.dbo"  
  
    on-error="fail-script"  
  
    report-errors-to="$SynchronizationReports$"  
  
/>  
```  
**オブジェクト名:** (こともできます indivdual オブジェクト名またはグループ オブジェクトの名前) の同期の対象オブジェクトを指定します。  
  
**エラー:** 同期エラーを警告またはエラーとして指定するかどうかを指定します。 エラー時に使用できるオプションは:  
  
-   report-total-as-warning  
  
-   report-each-as-warning  
  
-   失敗するスクリプト  
  
### <a name="refresh-from-database"></a>データベースから更新します。  
コマンドは、**データベースからの更新**が**レポートでエラーを**パラメーターで、更新操作のエラー レポートの場所を指定します。 次に、名前のファイルが**SourceDBRefreshReport&lt;n&gt;です。XML**指定した場所に作成された場所**&lt;n&gt;** 同じコマンドの実行ごとに 1 桁の数字で増加する一意のファイル数です。  
  
**注:** フォルダーのパスを指定するとかどうか、は、' レポートでエラーを 'パラメーターはコマンド' 同期ターゲット ' の省略可能な属性になります。  
  
```xml  
<!-- Example: Refresh entire Schema (with all attributes)-->  
  
<refresh-from-database  
  
    object-name="$SourceDatabaseStandard$"  
  
    object-type ="Databases"  
  
    on-error="fail-script"  
  
    report-errors-to="$RefreshDBFolder$\RefreshReport.xml"  
  
/>  
```  
**オブジェクト名:** (こともできます indivdual オブジェクト名またはグループ オブジェクトの名前) の更新の対象オブジェクトを指定します。  
  
**エラー:** 更新エラーを警告またはエラーとして指定するかどうかを指定します。 エラー時に使用できるオプションは:  
  
-   report-total-as-warning  
  
-   report-each-as-warning  
  
-   失敗するスクリプト  
  
## <a name="see-also"></a>参照  
[SSMA コンソール (アクセス) を実行します。](http://msdn.microsoft.com/en-us/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  
