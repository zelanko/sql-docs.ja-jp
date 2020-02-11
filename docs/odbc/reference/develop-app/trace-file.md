---
title: トレースファイル |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c94c3718c116b37eb198264887dfb4a319bd1dc3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67985153"
---
# <a name="trace-file"></a>トレース ファイル
アプリケーションでは、Odbc .ini レジストリエントリで**tracefile**キーワードを設定するか、SQL_ATTR_TRACEFILE 接続属性を使用して**SQLSetConnectAttr**を呼び出すことによって、トレースファイルを指定します。 トレースを有効にしたときにファイルが存在しない場合は、ドライバーマネージャーによってファイルが作成されます。 競合を回避するには、各アプリケーションに専用のトレースファイルを用意する必要があります。 アプリケーションでは、複数のトレースファイルを使用できます。アプリケーションのセットアッププログラムでは、ユーザーにトレースファイルを選択させることができます。 トレースが動的に有効になっている場合は、トレースファイルにログ記録するのではなく、トレース結果を表示することもできます。  
  
 トレースファイルは、すべての引数のデータ型と値を使用して、各 ODBC 関数呼び出しのログを提供します。 すべての入力関数をログに記録し、返されたすべての関数をリターンコードとエラー状態と共にログに記録します。  
  
 ODBC 3.x では、接続関数に対するパラメーターがトレース DLL に提供されませ*ん。*
