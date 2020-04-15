---
title: トレース ファイル |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- trace files [ODBC]
- tracing options [ODBC], trace files
ms.assetid: ec97f949-126f-40a2-b67e-e74520a524cb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ddd0ee24649592cf4a1a296a51404334145a3bab
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298059"
---
# <a name="trace-file"></a>トレース ファイル
アプリケーションは、Odbc.ini レジストリ エントリに**TraceFile**キーワードを設定するか、SQL_ATTR_TRACEFILE接続属性を指定して**SQLSetConnectAttr**を呼び出すことによって、トレース ファイルを指定します。 トレースが有効になっているときにファイルが存在しない場合、ドライバー マネージャーは、ファイルを作成します。 競合を避けるために、各アプリケーションに専用のトレース ファイルが必要です。 アプリケーションは、複数のトレース・ファイルを使用できます。アプリケーションのセットアップ プログラムは、トレース ファイルの選択をユーザーに提供できます。 トレースが動的に有効になっている場合、トレース ファイルにログを記録するのではなく、トレース結果を表示することもできます。  
  
 トレース ファイルは、すべての引数のデータ型と値を持つ各 ODBC 関数呼び出しのログを提供します。 すべての入力関数をログに記録し、戻りコードとエラー状態を持つすべての戻り関数をログに記録します。  
  
 ODBC *3.x*では、接続関数へのパラメーターはトレース DLL には提供されません。
