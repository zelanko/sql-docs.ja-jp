---
title: "サポートされるカーソル モデル (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント"
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
- Visual FoxPro ODBC driver [ODBC], cursors
- cursors [ODBC], Visual FoxPro ODBC driver
- FoxPro ODBC driver [ODBC], cursors
- static cursors [ODBC]
- block cursors [ODBC]
- rowset cursors [ODBC]
ms.assetid: be95bbb2-6886-491e-a5a7-f58028d19c1e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b80cb7cbbea13dbc6d491d757f28d44d5fda1ea6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="supported-cursor-model-visual-foxpro-odbc-driver"></a>サポートされるカーソル モデル (Visual FoxPro ODBC ドライバー)
Visual FoxPro ODBC ドライバーでは、両方がサポート*ブロック*(*行セット*) および*静的*カーソル。 レベル 1 の ODBC コンプライアンスに準拠しているすべてのドライバーでは、静的カーソルはサポートされます。 ドライバーが動的、キーセット ドリブンまたは混合 (キーセット カーソルおよび動的) をサポートしていないカーソル。  
  
 アプリケーションが呼び出すことができます[SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) SQL_CURSOR_FORWARD_ONLY (ブロック カーソル) または SQL_CURSOR_STATIC (静的カーソル) の SQL_CURSOR_TYPE オプションを使用します。  
  
> [!NOTE]  
>  呼び出す場合**SQLSetStmtOption**関数は、オプションでは、SQL_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY または SQL_CURSOR_STATIC 以外、01S02 の sqlstate SQL_SUCCESS_WITH_INFO が返されます (オプションの値が変更されました)。 ドライバーは、サポートされていないカーソルのすべてのモードを SQL_CURSOR_STATIC に設定します。  
  
 カーソルの種類について、バージョン情報の詳細については**SQLSetStmtOption**を参照してください、 [ODBC プログラマ リファレンス](../../odbc/reference/odbc-programmer-s-reference.md)です。  
  
## <a name="block-cursor"></a>ブロック カーソル (block cursor)  
 データの記憶域の管理を担当すると、クライアントに返される前方スクロール、読み取り専用の結果セットを返します。  
  
## <a name="static-cursor"></a>静的カーソル (static cursor)  
 クエリによって定義されたデータ セットのスナップショットです。 静的カーソルでは、他のユーザーによって基になるデータのリアルタイムな変更は反映されません。 カーソルのメモリ バッファーは、前方および後方にスクロールできる ODBC カーソル ライブラリで維持されます。  
  
## <a name="rowset"></a>行セット (rowset)  
 データ ソースから取得された行を表す、カーソルに格納されたデータのブロックです。

