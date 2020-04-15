---
title: ORACLE 用の ODBC ドライバーで SQLConfig データソースを使用する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLConfigDataSource function [ODBC], ODBC driver for Oracle
ms.assetid: e535d1ef-aff9-4ae7-a3ed-ef4ca2584289
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 718e444d63e0d4cf3821c0c03eb851732ed5b4e4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292772"
---
# <a name="using-sqlconfigdatasource-with-the-odbc-driver-for-oracle"></a>ODBC Driver for Oracle を使用した SQLConfigDatasource の使用
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 次の表は、Oracle 用のマイクロソフト ODBC ドライバー、バージョン 1.0 (Msorcl10.dll) および Oracle 用のマイクロソフト ODBC ドライバーバージョン 2.0 (Msorcl32.dll) の有効な**SQLConfigDatasource**設定を示しています。  
  
> [!NOTE]  
>  Msorcl10.dll ドライバ (バージョン 1.0) は **、サーバー**以外のすべての設定をサポートしています。 Msorcl32.dll ドライバ (バージョン 2.0 以降) はすべての設定をサポートしています。  
  
 一部の設定は、ドライバーによって無視されますが **、SQLConfig データソース**によって受け入れられます。 ODBC 接続文字列にこれらの設定を含めると、実行時に受け入れられる唯一の方法です。 無視された設定は **、SQLConfigDatasource**がデータ ソースを作成するときにレジストリに格納されません。  
  
 次の表では *、A/N*は、最大許容長までの有効な英数字文字列を意味します。 *最大 Len* (最大長) は、文字列終端文字を含む、設定で許容される最大文字列長です。  
  
|設定|マックス・レン|既定値|有効な値|説明|  
|-------------|-------------|-------------------|------------------|-----------------|  
|BufferSize|7|65,535|1000|最小フェッチ バッファ サイズは最大 65535 バイト|  
|カタログキャップ|2|1|0 または 1|1 の場合、引用符で囲まれていない識別子はカタログ関数で大文字に変換されます。|  
|ConnectString|128|""|A/N|接続文字列: Msorcl10.dll ドライバーでサーバー名を指定する方法が必要です。|  
|説明|256|""|A/N|説明|  
|DSN (DSN)|33|""|A/N|データ ソース名。|  
|ゲス・ザ・コルデフ|4|0|A/N|Oracle 定義のスケールを持たない列の 0 以外の値を返します。|  
|ナンバーフロート|2|""|0 または 1|0 の場合、FLOAT 列はSQL_FLOATとして扱われます。 1 の場合、FLOAT 列はSQL_DOUBLEとして扱われます。|  
|PWD|30|""|A/N|パスワード。|  
|RDOサポート|2|""|0 または 1|RDO が Oracle プロシージャを呼び出すことを許可します。|  
|解説|2|0|0 または 1|カタログ関数に REMARKS を含めます。|  
|Rowlimit|4|""|0 から 99|SELECT ステートメントによって返される最大行数。 長さ 0 の文字列は、制限が適用されないです。|  
|サーバー|128|""|A/N|Oracle サーバー名。|  
|シノニムカラム|2|1|0 または 1|SQL 列にシノニンを含めます。|  
|システムテーブル|2|""|0 または 1|0 の場合、システム テーブルは表示されません。 1 の場合、システム テーブルが表示されます。|  
|トランスレーションDLL|33|""|A/N|変換 .dll 名。|  
|翻訳名|33|""|A/N|翻訳名。|  
|翻訳オプション|33|""|A/N|翻訳オプション。|  
|トックスンキャップ|2|""|A/N|トランザクション対応。 0 の場合、ドライバーはトランザクションをサポートしていないことを報告します。 1 の場合、ドライバはトランザクションを実行できることを報告します。|  
|UID|30|""|A/N|ユーザー名。|
