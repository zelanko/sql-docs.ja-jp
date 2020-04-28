---
title: 動的トレース |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305770"
---
# <a name="dynamic-tracing"></a>動的トレース
トレースは、アプリケーションの実行の任意の時点で有効または無効にすることができます。 これにより、アプリケーションは任意の数の関数呼び出しをトレースできます。  
  
 変数**ODBCSharedTraceFlag**は、トレースを動的に有効にするように設定されています。 この変数は、ドライバーマネージャーのすべての実行中のコピー間で共有されます。 アプリケーションによってこの変数が設定されている場合、現在実行中のすべての ODBC アプリケーションでトレースが有効になります。 動的トレースが有効になっているときにトレースをオフにするには、アプリケーションが**SQLSetConnectAttr**を呼び出して、SQL_ATTR_TRACE を SQL_TRACE_OFF に設定します。 この呼び出しは、そのアプリケーションに対してのみトレースをオフにします。 Odbc32.dll にリンクされているアプリケーションでは、この変数の使用を変更できます。 トレースデータは、ODBC セッションの後に開く必要があるトレースファイルではなく、リアルタイムのウィンドウで表示できます。 アプリケーションの画面にコントロールを追加して、その時点でトレースをオンまたはオフにすることができます。  
  
 ODBC 3.x に付属するトレース DLL は、スレッドセーフ*ではありません。* グローバルトレースが有効になっていて (変数**ODBCSharedTraceFlag**が設定されている)、複数のアプリケーションが同時にトレースファイルに書き込む場合は、ログファイルが正しく書き込まれることは保証されません。 この状態ではエラーは返されません。
