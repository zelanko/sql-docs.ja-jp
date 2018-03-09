---
title: "ODBC と標準の CLI |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC [ODBC], CLI
- CLI [ODBC]
- CLI [ODBC], about CLI
- call-level interface [ODBC]
- call-level interface [ODBC], about call-level interface
ms.assetid: 79b9c268-16ac-4b80-b451-f9dcd8c02ca4
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8133a266e81a1711947af9acb34a89b861a32b16
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-and-the-standard-cli"></a>ODBC と標準の CLI
ODBC は、次の仕様および標準呼び出しレベル インターフェイス (CLI) での処理を整列させます。 (ODBC の機能は、これらの標準の各のスーパー セットです)。  
  
-   Open Group CAE 仕様"Data Management: SQL 呼び出しレベルのインターフェイス (CLI)"  
  
-   ISO/IEC 9075-3:1995 (E) 呼び出しレベルのインターフェイス (SQL/CLI)  
  
 この配置では、結果として、次に該当します。  
  
-   ODBC 3 では、Open Group と ISO CLI 仕様に記述されたアプリケーションは動作します。*x*ドライバーまたは ODBC 3 では、コンパイル時の標準に準拠したドライバー *。x*ヘッダー ファイルし、ODBC 3 とリンクします*。x*ライブラリ、ドライバーは ODBC 3 へのアクセスを得る場合および*。x*ドライバー マネージャー。  
  
-   Open Group および ISO CLI 仕様に記述されたドライバーは ODBC 3 では機能*.x*アプリケーションまたは ODBC 3 では、コンパイル時の標準に準拠したアプリケーション*.x*ヘッダー ファイルし、リンクODBC 3*.x*ライブラリ、ODBC 3 を使用してドライバー、アプリケーションがアクセスおよび*.x*ドライバー マネージャー。 (詳細については、次を参照してください。[標準に準拠したアプリケーションやドライバー](../../odbc/reference/develop-app/standards-compliant-applications-and-drivers.md)です。  
  
 コア インターフェイスへの準拠レベルには、ISO CLI 内のすべての機能および開くグループ CLI で nonoptional すべての機能が含まれます。 開くグループ CLI の省略可能な機能より高いインターフェイスへの準拠レベルに表示されます。 すべての ODBC 3 です。*x*ドライバーは、コア インターフェイスへの準拠レベルで機能をサポートするために必要な true を次に示します。  
  
-   ODBC 3 です。*x*ドライバーは、標準に準拠したアプリケーションで使用されるすべての機能をサポートします。  
  
-   ODBC 3 です。*x* ISO CLI の機能のみおよび開くグループ cli nonoptional の機能を使用してアプリケーションを任意の標準に準拠したドライバーで動作します。  
  
 ISO/IEC および開くグループ CLI 規格に含まれている呼び出しレベルのインターフェイスの仕様、に加えて ODBC は、次の機能を実装します。 (これらの機能の一部は ODBC が ODBC 3 より前のバージョンに存在します。*x*)。  
  
-   1 つの関数の呼び出しによって複数行のフェッチ  
  
-   パラメーターの配列へのバインド  
  
-   ブックマーク、可変長のブックマークを一括してフェッチを含むブックマーク サポートは、更新および連続しない行のブックマーク操作によって削除  
  
-   行方向のバインド  
  
-   オフセットのバインド  
  
-   ストアド プロシージャ内またはを通じて実行された SQL ステートメントのシーケンスとして、SQL ステートメントのバッチ サポート**SQLExecute**または**SQLExecDirect**  
  
-   真数または概数値カーソル行をカウントします。  
  
-   更新および削除操作およびバッチ更新および削除を関数呼び出しによって配置されている (**SQLSetPos**)  
  
-   カタログ情報スキーマ ビューをサポートする必要がない情報スキーマから情報を抽出する関数  
  
-   外部結合、スカラー関数、日付時刻リテラル、間隔のリテラル値、およびストアド プロシージャのエスケープ シーケンス  
  
-   コード ページ変換ライブラリ  
  
-   ドライバーの ANSI 準拠レベルと SQL のサポートに関するレポート  
  
-   実装パラメーター記述子をオンデマンドで自動設定  
  
-   診断の機能強化および行およびパラメーターの状態配列  
  
-   Datetime、間隔、数値または 10 進数、および 64 ビット整数アプリケーション バッファー型  
  
-   非同期の実行  
  
-   エスケープ シーケンスを含むストアド プロシージャのサポートは、パラメーター バインディング機構を出力し、カタログ関数  
  
-   接続属性および属性が参照するためのサポートを含む接続の強化
