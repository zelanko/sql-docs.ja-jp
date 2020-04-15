---
title: サポートされているカーソル モデル (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cf3400f24e20a8fa864404612bf07ea44efce49e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301128"
---
# <a name="supported-cursor-model-visual-foxpro-odbc-driver"></a>サポートされるカーソル モデル (Visual FoxPro ODBC ドライバー)
ビジュアル フォックスプロ ODBC ドライバーは *、ブロック*(*行セット*) と*静的*カーソルの両方をサポートしています。 静的カーソルは、レベル 1 の ODBC 準拠に準拠するすべてのドライバーでサポートされます。 ドライバーは、動的カーソル、キーセット ドリブン カーソル、または混合 (キーセットカーソルと動的カーソル) カーソルをサポートしていません。  
  
 アプリケーションは、SQL_CURSOR_FORWARD_ONLY (ブロック カーソル) またはSQL_CURSOR_STATIC (静的カーソル) のSQL_CURSOR_TYPEオプションを指定して[SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md)を呼び出すことができます。  
  
> [!NOTE]  
>  SQL_CURSOR_FORWARD_ONLYまたはSQL_CURSOR_STATIC以外のSQL_CURSOR_TYPEオプションを指定して**SQLSetStmtOption**を呼び出すと、この関数は、01S02 (オプション値が変更された) の SQLSTATE を持つSQL_SUCCESS_WITH_INFOを戻します。 ドライバーは、すべてのサポートされていないカーソル モードをSQL_CURSOR_STATICに設定します。  
  
 カーソルの種類と**SQLSetStmtOption**の詳細については[、ODBC プログラマ リファレンス を参照してください](../../odbc/reference/odbc-programmer-s-reference.md)。  
  
## <a name="block-cursor"></a>ブロック カーソル (block cursor)  
 前方スクロール、読み取り専用の結果セットがクライアントに返され、データのストレージを管理する責任があります。  
  
## <a name="static-cursor"></a>静的カーソル (static cursor)  
 クエリによって定義されたデータ セットのスナップショット。 静的カーソルは、他のユーザーによる基になるデータのリアルタイムの変更を反映しません。 カーソルのメモリ バッファは ODBC カーソル ライブラリによって維持され、前方スクロールと逆方向スクロールが可能です。  
  
## <a name="rowset"></a>行セット (rowset)  
 データ ソースから取得した行を表す、カーソルに格納されているデータのブロック。
