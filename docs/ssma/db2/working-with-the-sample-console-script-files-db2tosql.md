---
title: "サンプルのコンソール スクリプト ファイル (DB2ToSQL) の操作 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 5c3080c3-d074-4f99-a5f5-219ebeddc474
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 20583ed71781b093b3195d8dc1f192258a5b569a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="working-with-the-sample-console-script-files-db2tosql"></a>サンプルのコンソール スクリプト ファイル (DB2ToSQL) の操作
いくつかのサンプル ファイルは、ユーザーの参照と使用法について、製品と共に用意されています。 このセクションでは、エンドユーザーのニーズに合わせてこれらのスクリプトを簡単にカスタマイズする方法について説明します。  
  
## <a name="sample-console-script-files"></a>サンプル コンソール スクリプト ファイル  
ユーザーの参照には、さまざまなシナリオをカバーする次のサンプル コンソール スクリプト ファイルを提供されています。  
  
-   ServersConnectionFileSample.xml  
  
-   VariableValueFileSample.xml  
  
-   AssessmentReportGenerationSample.xml  
  
-   SqlStatementConversionSample.xml  
  
-   ConversionAndDataMigrationSample.xml  
  
1.  **ServersConnectionFileSample.xml:**  
  
    -   このサンプルでは、利用可能な接続の種類のモードをソースとターゲット データベースにされ、ユーザーは、要求に応じていずれかのモードを選択できます。 このサンプルには、サーバーの定義が含まれています。  
  
    -   ユーザーは、必要なソースとターゲット サーバーの定義に値を変更するだけで、必要なデータベースに接続できます。 例で提供されるすべての値が用意されてで使用可能な値を変数として、 **VariableValueFileSample.xml**です。  その他のすべての接続パラメーターは、ユーザーの作業サーバーの接続ファイルから削除できます。  
  
    -   ソースとターゲット サーバーへの接続の詳細については、次を参照してください。[サーバー接続ファイル &#40;DB2ToSQL&#41; を作成する](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)です。  
  
2.  **VariableValueFileSample.xml:**スクリプト ファイルのサンプルのコンソールで使用されているすべての変数と`ServersConnectionFileSample.xml`このファイルで照合されています。 ユーザーが単純に置き換えます。 サンプル変数にサンプルのコンソール スクリプトを実行するには、ユーザーに値は定義されているものと、このファイルをスクリプト ファイルと共に追加のコマンドライン引数として渡します。  
  
    値のさまざまなファイルの詳細については、次を参照してください。[変数値のファイルを作成する &#40;DB2ToSQL&#41;](../../ssma/db2/creating-variable-value-files-db2tosql.md)です。  
  
3.  **AssessmentReportGenerationSample.xml:**このサンプルには、ユーザーが使用できる、ユーザーが分析のために変換し、データの移行は開始する前に xml 評価レポートの生成ができるようにします。  
  
    `generate-assessment-report` Mandatorily 変数の値を変更するユーザーが持ってコマンド (を参照してください**VariableValueFileSample.xml**) で、`object-name`属性をユーザーによって使用されているデータベース名。 指定された、オブジェクトの種類に応じて、`object-type`値を変更する必要があります。  
  
    ユーザーが複数のオブジェクトを評価する/彼のデータベースの場合は複数指定できます`metabase-object`ノードに示すように、`generate-assessment-report`サンプル コンソール スクリプト ファイルのコマンドの例 4 です。  
  
    レポートを生成する方法の詳細については、次を参照してください。[レポートを生成する &#40;DB2ToSQL&#41;](../../ssma/db2/generating-reports-db2tosql.md)です。  
  
    **Notes:**  
  
    コンソール アプリケーションに渡される変数の値ファイルのコマンドライン引数を使用すると、VariableValueFileSample.xml が指定したユーザーに更新されることを確認して値。  
  
    コンソール アプリケーションにサーバー接続ファイルのコマンドライン引数が渡されるパラメーター値が適切なサーバー、ServersConnectionFileSample.xml が更新されることを確認します。  
  
4.  **SqlStatementConversionSample.xml:**このサンプルでは、対応するを生成するユーザー`t-sql`ソース データベースのスクリプトを`sql`コマンドの入力として指定します。  
  
    `convert-sql-statement` Mandatorily 変数の値を変更するユーザーが持ってコマンド (を参照してください**VariableValueFileSample.xml**) で、`context`属性をユーザーによって使用されているデータベースの名前にします。 ユーザーを変更する必要もあります、`sql`属性値をソース データベースに`sql`を変換するにより必要とするコマンド。  
  
    ユーザーには sql ファイルを変換できることもできます。 これは、で説明されているが、`convert-sql-statement`サンプル コンソール スクリプト ファイルのコマンドの例 4 です。  
  
    > [!NOTE]  
    > コンソール アプリケーションに渡される変数の値ファイルのコマンドライン引数を使用すると、VariableValueFileSample.xml が指定したユーザーに更新されることを確認して値。  
  
5.  **ConversionAndDataMigrationSample.xml:**このサンプルには、データの移行への変換から、エンド ツー エンドな移行を実行するユーザーができるようにします。 変更する必要が必須の属性値の一覧は次のとおりです。  
  
    |コマンド名|Description|属性|  
    |----------------|---------------|-------------|  
    |`map-schema`|ターゲット スキーマへのソース データベースのスキーマ マッピングです。|`source-schema:`変換を必要とするソース データベースを指定します。<br /><br />`sql-server-schema`: に移行するのには、ターゲット データベースを指定します。|  
    |`convert-schema`|ソースからターゲット スキーマへのスキーマの変換を実行します。<br /><br />ユーザーが複数のオブジェクトを評価する/彼のデータベースの場合は複数指定できます`metabase-object`ノードに示すように、`convert-schema`サンプル コンソール スクリプト ファイルのコマンドの例 4 です。|`object-name`: 指定した転送元データベース/オブジェクト名を変換する必要があります。 対応することを確認`object-type`で指定されているオブジェクトの種類に基づいて変更します`object-name`|  
    |`synchronize-target`|ターゲット データベースと、対象オブジェクトを同期します。<br /><br />ユーザーが複数のオブジェクトを評価する/彼のデータベースの場合は複数指定できます`metabase-object`ノードに示すように、`synchronize-target`サンプル コンソール スクリプト ファイルのコマンドの例 3 です。|`object-name:`Sql server データベースを指定する/オブジェクト名を作成する必要があります。 対応することを確認`object-type`で指定されているオブジェクトの種類に基づいて変更します`object-name`|  
    |`migrate-data`|ターゲットに、ソース データを移行します。<br /><br />ユーザーが複数のオブジェクトを評価する/彼のデータベースの場合は倍数を指定できます`metabase-object`ノードに示すように、`migrate-data`サンプル コンソール スクリプト ファイルのコマンドの例 2 です。|`object-name:`テーブルを移行するために必要な名前/ソース データベースを指定します。 対応することを確認`object-type`で指定されているオブジェクトの種類に基づいて変更します`object-name`|  
  
## <a name="see-also"></a>参照  
[変数値ファイル &#40;DB2ToSQL&#41; の作成](../../ssma/db2/creating-variable-value-files-db2tosql.md)  
[サーバーの接続ファイル &#40;DB2ToSQL&#41; の作成](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)  
[生成するレポート &#40;DB2ToSQL&#41;](../../ssma/db2/generating-reports-db2tosql.md)  
  

