---
title: 動的トレース |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- tracing options [ODBC], dynamic
- dynamic tracing [ODBC]
ms.assetid: ebe58a83-a7b0-4747-86c8-2af2940471ef
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8cbd2dbae4f4b437f45845ce2791f4a9b0aa8c8b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305770"
---
# <a name="dynamic-tracing"></a>動的トレース
トレースは、アプリケーションの実行のどの時点でも有効または無効にできます。 これにより、アプリケーションは任意の数の関数呼び出しをトレースできます。  
  
 変数**ODBCSharedTraceFlag**は、動的にトレースを有効にするように設定されています。 この変数は、ドライバー マネージャーのすべての実行中のコピー間で共有されます。 いずれかのアプリケーションがこの変数を設定すると、現在実行中のすべての ODBC アプリケーションでトレースが有効になります。 動的トレースが有効になっているときにトレースをオフにするには、アプリケーションは**SQLSetConnectAttr**を呼び出して、SQL_ATTR_TRACEをSQL_TRACE_OFFに設定します。 この呼び出しは、そのアプリケーションのトレースのみをオフにします。 Odbc32.lib にリンクされているアプリケーションは、この変数の使用を変更できます。 トレース データは、トレース ファイルではなくリアルタイム ウィンドウに表示できます。 コントロールをアプリケーションの画面に追加して、トレースのオンとオフを切り分けることができます。  
  
 ODBC 3 *.x*に付属のトレース DLL はスレッド セーフではありません。 グローバル トレースが有効になっている (変数**ODBCSharedTraceFlag**が設定されている) と、複数のアプリケーションが同時にトレース ファイルに書き込む場合、ログ ファイルが正しく書き込まれるとは保証されません。 この条件はエラーを返しません。
