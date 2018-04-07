---
title: 使用可能なサンプル コンソール スクリプト FilesExecuting SSMA コンソール |Microsoft ドキュメント
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-access
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: ad75b648-d119-4119-98f0-d18f058be68d
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5b5140d8faf5c606abd103f15b93aaf2510b753c
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="working-with-the-sample-console-script-filesexecuting-the-ssma-console-accesstosql"></a>サンプルのコンソール スクリプト FilesExecuting SSMA コンソール (AccessToSQL) の使用
いくつかのサンプル ファイルは、ユーザーの参照と使用法について、製品と共に用意されています。 このセクションでは、エンドユーザーのニーズに合わせてこれらのスクリプトを簡単にカスタマイズする方法について説明します。  
  
## <a name="sample-console-script-files"></a>サンプル コンソール スクリプト ファイル  
ユーザーの参照には、さまざまなシナリオをカバーする次のサンプル コンソール スクリプト ファイルを提供されています。  
  
-   ServersConnectionFileSample.xml  
  
-   VariableValueFileSample.xml  
  
-   AssessmentReportGenerationSample.xml  
  
-   ConversionAndDataMigrationSample.xml  
  
-   **ServersConnectionFileSample.xml:**  
  
    -   このサンプルでは、利用可能な接続の種類のモードをソースとターゲット データベースにされ、ユーザーは、要求に応じていずれかのモードを選択できます。 このサンプルには、サーバーの定義が含まれています。  
  
    -   ユーザーは、必要なソースとターゲット サーバーの定義に値を変更するだけで、必要なデータベースに接続できます。 例で提供されるすべての値が用意されてで使用可能な値を変数として、 **VariableValueFileSample.xml**です。 その他のすべての接続パラメーターは、ユーザーの作業サーバーの接続ファイルから削除できます。  
  
    -   ソースとターゲット サーバーへの接続の詳細については、次を参照してください。[サーバー接続ファイルを作成する&#40;AccessToSQL&#41; ](../../ssma/access/creating-the-server-connection-files-accesstosql.md)です。  
  
-   **VariableValueFileSample.xml:**スクリプト ファイルのサンプルのコンソールで使用されているすべての変数と`ServersConnectionFileSample.xml`このファイルで照合されています。 ユーザーが単純に置き換えます。 サンプル変数にサンプルのコンソール スクリプトを実行するには、ユーザーに値は定義されているものと、このファイルをスクリプト ファイルと共に追加のコマンドライン引数として渡します。  
  
    値のさまざまなファイルの詳細については、次を参照してください。[変数値のファイルを作成する&#40;AccessToSQL&#41;](../../ssma/access/creating-variable-value-files-accesstosql.md)です。  
  
-   **AssessmentReportGenerationSample.xml:**このサンプルには、ユーザーが使用できる、ユーザーが分析のために変換し、データの移行は開始する前に xml 評価レポートの生成ができるようにします。  
  
    `generate-assessment-report` Mandatorily 変数の値を変更するユーザーが持ってコマンド (を参照してください**VariableValueFileSample.xml**) で、`object-name`属性をユーザーによって使用されているデータベース名。 指定された、オブジェクトの種類に応じて、`object-type`値を変更する必要があります。  
  
    ユーザーが複数のオブジェクトを評価する/彼のデータベースの場合は複数指定できます`metabase-object`ノードに示すように、`generate-assessment-report`サンプル コンソール スクリプト ファイルのコマンドの例 4 です。  
  
    レポートを生成する方法の詳細については、次を参照してください。[を生成するレポート&#40;AccessToSQL&#41;](../../ssma/access/generating-reports-accesstosql.md)です。  
  
    > [!NOTE]  
    > -   コンソール アプリケーションに渡される変数の値ファイルのコマンドライン引数を使用すると、VariableValueFileSample.xml が指定したユーザーに更新されることを確認して値。  
    > -   コンソール アプリケーションにサーバー接続ファイルのコマンドライン引数が渡されるパラメーター値が適切なサーバー、ServersConnectionFileSample.xml が更新されることを確認します。  
  
-   **ConversionAndDataMigrationSample.xml:**このサンプルには、データの移行への変換から、エンド ツー エンドな移行を実行するユーザーができるようにします。 変更する必要が必須の属性値の一覧は次のとおりです。  
  
    |コマンド名|Description|属性|  
    |----------------|---------------|-------------|  
    |`map-schema`|ターゲット スキーマへのソース データベースのスキーマ マッピングです。|`source-schema:` 変換を必要とするソース データベースを指定します。<br /><br />`sql-server-schema`: に移行するのには、ターゲット データベースを指定します。|  
    |`convert-schema`|ソースからターゲット スキーマへのスキーマの変換を実行します。<br /><br />ユーザーが複数のオブジェクトを評価する/彼のデータベースの場合は複数指定できます`metabase-object`ノードに示すように、`convert-schema`サンプル コンソール スクリプト ファイルのコマンドの例 4 です。|`object-name`: 指定した転送元データベース/オブジェクト名を変換する必要があります。 対応することを確認`object-type`で指定されているオブジェクトの種類に基づいて変更します `object-name`|  
    |`synchronize-target`|ターゲット データベースと、対象オブジェクトを同期します。<br /><br />ユーザーが複数のオブジェクトを評価する/彼のデータベースの場合は複数指定できます`metabase-object`ノードに示すように、`synchronize-target`サンプル コンソール スクリプト ファイルのコマンドの例 3 です。|`object-name:` Sql server データベースを指定する/オブジェクト名を作成する必要があります。 対応することを確認`object-type`で指定されているオブジェクトの種類に基づいて変更します `object-name`|  
    |`migrate-data`|ターゲットに、ソース データを移行します。<br /><br />ユーザーが複数のオブジェクトを評価する/彼のデータベースの場合は倍数を指定できます`metabase-object`ノードに示すように、`migrate-data`サンプル コンソール スクリプト ファイルのコマンドの例 2 です。|`object-name:` テーブルを移行するために必要な名前/ソース データベースを指定します。 対応することを確認`object-type`で指定されているオブジェクトの種類に基づいて変更します `object-name`|  
  
## <a name="see-also"></a>参照  
[変数の値のファイルを作成する&#40;AccessToSQL&#41;](../../ssma/access/creating-variable-value-files-accesstosql.md)  
[サーバー接続ファイルを作成する&#40;AccessToSQL&#41;](../../ssma/access/creating-the-server-connection-files-accesstosql.md)  
[レポートの生成&#40;AccessToSQL&#41;](../../ssma/access/generating-reports-accesstosql.md)  
  
