---
title: "Odbc 入力元のカスタム プロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 362bbcd8-b7b0-4bab-8afe-1212b2ad1af9
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 15c78bdb8f093b07ce62a7d710ba583aad96548d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="odbc-source-custom-properties"></a>ODBC 入力元のカスタム プロパティ
  次の表は、ODBC 入力元のカスタム プロパティを示しています。 すべてのプロパティは、SSIS プロパティ式から設定できます。  
  
|プロパティ名|データ型|Description|  
|-------------------|---------------|-----------------|  
|接続|ODBC Connection|入力元データベースにアクセスするための ODBC 接続。|  
|AccessMode|Integer (列挙)|データベースへのアクセスに使用するモード。 有効な値は、テーブル名 (0) およびSQLコマンド (1) です。<br /><br /> 既定値はテーブル名 (0) です。|  
|BatchSize|Integer|一括抽出のバッチのサイズ。 これは、配列として抽出されるレコード数です。 選択した ODBC プロバイダーが配列をサポートしていない場合のバッチ サイズは 1 です。|  
|BindCharColumnAs|Integer (列挙)|このプロパティは、ODBC 入力元で SQL_CHAR、SQL_VARCHAR、SQL_LONGVARCHAR などの複数バイト文字列型の列をバインドする方法を決定します。<br /><br /> 有効な値は、SQL_C_WCHAR として列をバインドする Unicode (0) と、SQL_C_CHAR として列をバインドする ANSI (1) です。 既定値は Unicode (0) です。<br /><br /> **注**: このプロパティは、 **ODBC 入力元エディター**では使用できませんが、 **詳細エディター**を使用して設定できます。|  
|BindNumericAs|Integer (列挙)|このプロパティは、ODBC 入力元で SQL_TYPE_NUMERIC データ型および SQL_TYPE_DECIMAL データ型の数値データの列をバインドする方法を決定します。<br /><br /> 有効なオプションは、SQL_C_CHAR として列をバインドする Char (0) と、SQL_C_NUMERIC として列をバインドする Numeric (1) です。 既定値は Char (0) です。<br /><br /> **注**: このプロパティは、 **ODBC 入力元エディター**では使用できませんが、 **詳細エディター**を使用して設定できます。|  
|DefaultCodePage|Integer|文字列の出力列に対して使用するコード ページ。<br /><br /> **注**: このプロパティは、 **ODBC 入力元エディター**では使用できませんが、 **詳細エディター**を使用して設定できます。|  
|ExposeCharColumnsAsUnicode|ブール値|このプロパティは、コンポーネントが CHAR 型の列を公開する方法を決定します。 既定値は False で、CHAR 型の列がマルチバイト文字列 (DT_STR) として公開されることを示します。 True の場合、CHAR 型の列はワイド文字列 (DT_WSTR) として公開されます。<br /><br /> **注**: このプロパティは、 **ODBC 入力元エディター**では使用できませんが、 **詳細エディター**を使用して設定できます。|  
|FetchMethod|Integer (列挙)|データの取得に使用されるメソッド。 有効なオプションは、行ごと (0) およびバッチ (1) です。 既定値はバッチ (1) です。<br /><br /> これらのオプションの詳細については、「 [ODBC ソース](../../integration-services/data-flow/odbc-source.md)」を参照してください。<br /><br /> **注**: このプロパティは、 **ODBC 入力元エディター**では使用できませんが、 **詳細エディター**を使用して設定できます。|  
|SqlCommand|文字列|AccessMode が SQL コマンドに設定されている場合に実行される SQL コマンド。|  
|StatementTimeout|Integer|エラーを返してアプリケーションに戻らず、SQL ステートメントが実行されるまで待機する秒数。 既定値は 120 です。 値 0 は、システムがタイムアウトしないことを示します。|  
|TableName|文字列|AccessMode がテーブル名に設定されている場合に使用される、データが保存されているテーブルの名前。|  
|LobChunckSize|Integer|LOB 列のチャンク サイズ割り当て。|  
||||  
  
## <a name="see-also"></a>「  
 [Odbc 入力元](../../integration-services/data-flow/odbc-source.md)   
 [Odbc 入力元エディター & #40 です。接続マネージャー ページ &#41;](../../integration-services/data-flow/odbc-source-editor-connection-manager-page.md)  
  
  
