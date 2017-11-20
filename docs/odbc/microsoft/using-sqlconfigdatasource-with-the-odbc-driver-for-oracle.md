---
title: "SQLConfigDatasource を with the ODBC Driver for Oracle を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLConfigDataSource function [ODBC], ODBC driver for Oracle
ms.assetid: e535d1ef-aff9-4ae7-a3ed-ef4ca2584289
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: aa32db53ef43da7f01200dcf057f9855a4f5707e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-sqlconfigdatasource-with-the-odbc-driver-for-oracle"></a>SQLConfigDatasource を with the ODBC Driver for Oracle を使用してください。
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 次の表にリストが有効な**SQLConfigDatasource** Microsoft ODBC Driver for Oracle、バージョン 1.0 (Msorcl10.dll) と、Microsoft ODBC Driver for Oracle、バージョン 2.0 (Msorcl32.dll) に設定します。  
  
> [!NOTE]  
>  Msorcl10.dll ドライバー (version 1.0) を除くすべての設定をサポートしている**サーバー**です。 Msorcl32.dll ドライバー (バージョン 2.0 以降) では、すべての設定をサポートします。  
  
 一部の設定は、ドライバーでは無視されますで受け入れられる**SQLConfigDatasource**です。 ODBC 接続文字列にこれらの設定を含めることは実行時に同意したが唯一の方法です。 無視された設定はレジストリに保存されず**SQLConfigDatasource**データ ソースを作成します。  
  
 次の表に*A/N*許容最大長以内の有効な英数字の文字列を意味します。 *最大 Len* (最大長) は、文字列の最大許容長文字列ターミネータ文字を含むの設定で受け入れられます。  
  
|設定|最大の長さ|既定値|有効な値|Description|  
|-------------|-------------|-------------------|------------------|-----------------|  
|BufferSize|7|65535|1000|最小のフェッチ バッファー サイズは最大 65535 バイト|  
|CatalogCap|2|1|0 または 1|1 の場合、nonquoted 識別子は、カタログで大文字に変換関数になります。|  
|ConnectString|128|""|A/N|接続文字列: Msorcl10.dll ドライバーでサーバー名を指定する必要なメソッドです。|  
|Description|256|""|A/N|説明|  
|DSN (DSN)|33|""|A/N|データ ソースの名前。|  
|GuessTheColDef|4|0|A/N|列は Oracle 定義のスケールを 0 以外の値を返します。|  
|NumberFloat|2|""|0 または 1|0 の場合、浮動小数点数の列が使用できますとして扱われます。 1 の場合、浮動小数点数の列が SQL_DOUBLE として扱われます。|  
|PWD|30|""|A/N|パスワードです。|  
|RDOSupport|2|""|0 または 1|Oracle のプロシージャを呼び出す RDO を使用できます。|  
|解説|2|0|0 または 1|カタログ関数では、「解説」をが含まれます。|  
|RowLimit|4|""|0 ~ 99 の範囲|SELECT ステートメントによって返される行の最大数。 長さ 0 の文字列では、制限を適用しないことを示します。|  
|[サーバー]|128|""|A/N|Oracle サーバーの名前。|  
|SynonymColumns|2|1|0 または 1|SQLColumns、シノニムがあります。|  
|システム テーブル|2|""|0 または 1|0 の場合、システム テーブルは表示されません。 1 の場合、システム テーブルが表示されます。|  
|TranslationDLL|33|""|A/N|翻訳 .dll の名前です。|  
|TranslationName|33|""|A/N|翻訳の名前。|  
|TranslationOption|33|""|A/N|翻訳オプション。|  
|TxnCap|2|""|A/N|トランザクションに対応します。 0 の場合、ドライバーは、トランザクションをサポートしないを報告します。 1 の場合、ドライバーはトランザクションを実行できることを報告します。|  
|UID|30|""|A/N|ユーザー名。|

