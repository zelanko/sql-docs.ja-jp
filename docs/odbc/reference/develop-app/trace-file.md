---
title: "[トレース ファイル] |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- trace files [ODBC]
- tracing options [ODBC], trace files
ms.assetid: ec97f949-126f-40a2-b67e-e74520a524cb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 82062fe767847023cd1aa6614173b292b0bff378
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="trace-file"></a>トレース ファイル
アプリケーション ファイルを指定します、トレース設定するか、 **TraceFile**キーワード Odbc.ini レジストリ エントリで、または呼び出すことによって**SQLSetConnectAttr** SQL_ATTR_TRACEFILE 接続属性を持つ。 トレースが有効にすると、ファイルが存在しない場合、ドライバー マネージャーは、ファイルを作成します。 各アプリケーションは、競合を避けるため、独自の専用のトレース ファイルが必要です。 アプリケーションは、複数のトレース ファイルを使用できます。アプリケーションのセットアップ プログラムは、トレース ファイルの選択したユーザーに提供できます。 トレースが動的に有効な場合、アプリケーションも表示できますログではなく、トレース結果トレース ファイルに。  
  
 トレース ファイルは、データ型を持つ各 ODBC 関数呼び出しのログとのすべての引数の値を提供します。 すべての入力関数をログに記録し、リターン コードとエラーの状態を使用して返されるすべての機能を記録します。  
  
 ODBC 3*.x*DLL は、トレース接続関数にパラメーターが指定されていません。

