---
title: 動的トレース |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- tracing options [ODBC], dynamic
- dynamic tracing [ODBC]
ms.assetid: ebe58a83-a7b0-4747-86c8-2af2940471ef
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4ea7116433a06e12a8df40a0b09d214ce0e8a2c5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="dynamic-tracing"></a>動的トレース
トレースを有効になっているまたは実行するアプリケーションのどの時点でも無効になっていることができます。 これにより、関数呼び出しの任意の数を追跡するアプリケーション。  
  
 変数**ODBCSharedTraceFlag**が動的にトレースを有効に設定します。 この変数は、実行中のすべてのコピー、ドライバー マネージャーの間で共有されます。 任意のアプリケーションでは、この変数を設定、現在実行されているすべての ODBC アプリケーションのトレースが有効です。 アプリケーションを呼び出す動的トレースが有効な場合は、トレースを有効にする**SQLSetConnectAttr** SQL_TRACE_OFF SQL_ATTR_TRACE に設定します。 この呼び出しは、そのアプリケーションのみに対してオフ トレースを有効にします。 Odbc32.lib とリンクされているアプリケーションは、この変数の使用を変更できます。 トレース データは、ODBC のセッション後に開く必要のあるトレース ファイルではなく、リアルタイムのウィンドウで表示できます。 コントロールでトレースをオンまたはオフは有効にするアプリケーションの画面に追加することができます。  
  
 ODBC 3 に DLL が付属してトレース *.x*はスレッド セーフではありません。 グローバル トレースが有効になっている場合にログ ファイルが正常に書き込まことは保証されません (変数**ODBCSharedTraceFlag**設定されている) 複数のアプリケーションが同時に、トレース ファイルに書き込みます。 このような状況では、エラーは返されません。
