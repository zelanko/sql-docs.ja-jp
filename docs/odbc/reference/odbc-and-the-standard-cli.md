---
title: ODBC と標準 CLI |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], CLI
- CLI [ODBC]
- CLI [ODBC], about CLI
- call-level interface [ODBC]
- call-level interface [ODBC], about call-level interface
ms.assetid: 79b9c268-16ac-4b80-b451-f9dcd8c02ca4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 56dc0ac73c77cbbb77943d2e9ba308796b259dbb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305143"
---
# <a name="odbc-and-the-standard-cli"></a>ODBC と標準の CLI
ODBC は、コール レベル インターフェイス (CLI) を扱う次の仕様と標準に準拠しています。 (ODBC 機能は、これらの各標準のスーパーセットです。  
  
-   オープングループ CAE 仕様 「データ管理: SQL コールレベルインタフェース(CLI)」  
  
-   ISO/IEC 9075-3:1995 (E) コールレベルインタフェース(SQL/CLI)  
  
 この配置の結果、次の条件が満たされます。  
  
-   オープングループおよび ISO CLI 仕様書に記述されたアプリケーションは、ODBC 3.x ヘッダーファイルを使用してコンパイルされ、ODBC *3.x*ライブラリにリンクされ、ODBC 3.x ドライバ マネージャを通じてドライバにアクセスする場合に、ODBC *3.x* *3.x*ドライバまたは標準準拠ドライバで動作します。 *3.x*  
  
-   オープングループおよび ISO CLI 仕様書に書き込まれたドライバーは、ODBC *3.x*ヘッダーファイルを使用してコンパイルされ、ODBC *3.x*ライブラリにリンクされ、ODBC *3.x*ドライバー マネージャーを使用してアプリケーションがドライバーにアクセスできる場合に、ODBC *3.x*アプリケーションまたは標準準拠アプリケーションで動作します。 (詳細については、「[標準準拠のアプリケーションとドライバ](../../odbc/reference/develop-app/standards-compliant-applications-and-drivers.md)」を参照してください。  
  
 コア インターフェイス準拠レベルは、ISO CLI のすべての機能と、オープン グループ CLI のすべての非オプション機能を含みます。 オープングループ CLI のオプション機能は、より高いインターフェイス準拠レベルで表示されます。 すべての ODBC *3.x*ドライバーは、コア インターフェイス準拠レベルの機能をサポートする必要があるため、次の条件を満たします。  
  
-   ODBC *3.x*ドライバは、標準に準拠したアプリケーションで使用されるすべての機能をサポートします。  
  
-   ISO CLI の機能のみを使用する ODBC *3.x*アプリケーションと、オープン グループ CLI のオプション以外の機能は、標準準拠のドライバーで動作します。  
  
 ODBC では、ISO/IEC およびオープン グループ CLI 標準に含まれているコール レベルインターフェイス仕様に加えて、次の機能を実装しています。 (これらの機能の一部は、ODBC *3.x*以前のバージョンの ODBC に存在します。  
  
-   1 回の関数呼び出しによる複数行フェッチ  
  
-   パラメーターの配列へのバインド  
  
-   ブックマークによるフェッチ、可変長ブックマーク、連続していない行に対するブックマーク操作による一括更新と削除を含むブックマークのサポート  
  
-   行方向のバインド  
  
-   バインド オフセット  
  
-   ストアド プロシージャ内または**SQLExecute**または**SQLExecDirect**を使用して実行される一連の SQL ステートメントとして、SQL ステートメントのバッチのサポート  
  
-   正確または近似カーソル行数  
  
-   位置指定更新および削除操作、およびバッチ処理された更新と削除を関数呼び出し (**SQLSetPos**)  
  
-   情報スキーマビューをサポートすることなく情報スキーマから情報を抽出するカタログ関数  
  
-   外部結合、スカラー関数、日時リテラル、間隔リテラル、およびストアド プロシージャのエスケープ シーケンス  
  
-   コード・ページ変換ライブラリー  
  
-   ドライバーの ANSI 準拠レベルと SQL サポートのレポート  
  
-   実装パラメータ記述子のオンデマンド自動生成  
  
-   拡張診断および行およびパラメーターのステータス・アレイ  
  
-   日時、間隔、数値/10 進数、および 64 ビット整数のアプリケーション・バッファー・タイプ  
  
-   非同期実行  
  
-   ストアド プロシージャのサポート (エスケープ シーケンス、出力パラメータ のバインド機構、カタログ関数など)  
  
-   接続属性および属性参照のサポートを含む接続の拡張
