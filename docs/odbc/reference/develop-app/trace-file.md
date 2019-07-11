---
title: トレース ファイル |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 8138a0cef3a28d31242a74162f0024e28e8b8fe9
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793930"
---
# <a name="trace-file"></a>トレース ファイル
アプリケーション ファイルを指定します、トレースを設定するか、 **TraceFile**キーワード Odbc.ini のレジストリ エントリで、または呼び出すことによって**SQLSetConnectAttr** SQL_ATTR_TRACEFILE 接続属性を持つ。 トレースが有効にすると、ファイルが存在しない場合、ドライバー マネージャーは、ファイルを作成します。 各アプリケーションの競合を回避するために、独自の専用のトレース ファイルが必要です。 アプリケーションが複数のトレース ファイルを使用できます。アプリケーションのセットアップ プログラムは、トレース ファイルの選択肢をユーザーに提供できます。 トレースが動的に有効な場合、アプリケーションも表示できますログ記録ではなく、トレース結果トレース ファイルに。  
  
 トレース ファイルは、データ型を持つ各 ODBC 関数呼び出しのログとすべての引数の値を示します。 すべての入力関数ログに記録し、返されたすべての関数のリターン コードとエラーの状態をログに記録します。  
  
 ODBC で*3.x*、接続関数に対するパラメーターは、トレース DLL には提供されません。
