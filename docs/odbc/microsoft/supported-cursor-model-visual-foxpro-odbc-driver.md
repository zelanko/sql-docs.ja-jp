---
title: カーソル モデル (Visual FoxPro ODBC ドライバー) のサポート |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], cursors
- cursors [ODBC], Visual FoxPro ODBC driver
- FoxPro ODBC driver [ODBC], cursors
- static cursors [ODBC]
- block cursors [ODBC]
- rowset cursors [ODBC]
ms.assetid: be95bbb2-6886-491e-a5a7-f58028d19c1e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 875348a501c292e55b267ece769f16dd6bc9dbdd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63270936"
---
# <a name="supported-cursor-model-visual-foxpro-odbc-driver"></a>サポートされるカーソル モデル (Visual FoxPro ODBC ドライバー)
Visual FoxPro ODBC ドライバーでは、両方をサポート*ブロック*(*行セット*) と*静的*カーソル。 レベル 1 の ODBC コンプライアンスに準拠している任意のドライバーでは、静的カーソルはサポートされます。 ドライバーは、動的、キーセット ドリブンまたは混合 (キーセット カーソルおよび動的) をサポートしていませんカーソル。  
  
 アプリケーションが呼び出すことができます[SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) SQL_CURSOR_FORWARD_ONLY (ブロック カーソル) または SQL_CURSOR_STATIC (静的カーソル) の SQL_CURSOR_TYPE オプションを使用します。  
  
> [!NOTE]  
>  呼び出す場合**SQLSetStmtOption** SQL_CURSOR_TYPE オプション SQL_CURSOR_FORWARD_ONLY または SQL_CURSOR_STATIC 以外には、関数は、sql_success_with_info sqlstate 01S02 の (オプションの値が変更されました)。 ドライバーは、すべてのカーソルがサポートされていないモードを SQL_CURSOR_STATIC に設定します。  
  
 カーソルの種類について、バージョン情報の詳細については**SQLSetStmtOption**を参照してください、 [ODBC プログラマ リファレンス](../../odbc/reference/odbc-programmer-s-reference.md)します。  
  
## <a name="block-cursor"></a>ブロック カーソル (block cursor)  
 データ ストレージの管理を担当すると、クライアントに返される前方スクロール、読み取り専用の結果セットを返します。  
  
## <a name="static-cursor"></a>静的カーソル (static cursor)  
 クエリによって定義されたデータ セットのスナップショット。 静的カーソルでは、他のユーザーによって基になるデータのリアルタイムの変更は反映されません。 カーソルのメモリ バッファーは、前方と後方スクロールできる ODBC カーソル ライブラリによって維持されます。  
  
## <a name="rowset"></a>行セット (rowset)  
 行を表す、カーソルに格納されたデータのブロックは、データ ソースから取得されます。
