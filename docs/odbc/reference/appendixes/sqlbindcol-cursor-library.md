---
title: SQLBindCol (カーソル ライブラリ) |Microsoft ドキュメント
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
- SQLAllocStmt function [ODBC], Cursor Library
ms.assetid: f4dd546a-0a6c-4397-8ee7-fafa6b9da543
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0d18bcb0c437dacb3d9584b50c30179a36a000b3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907187"
---
# <a name="sqlbindcol-cursor-library"></a>SQLBindCol (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLBindCol**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLBindCol**を参照してください[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)です。  
  
 アプリケーションでは、カーソル ライブラリで現在の行セットを返すには 1 つ以上のバッファーを割り当てます。 呼び出す**SQLBindCol**結果セットにこれらのバッファーをバインドする 1 つ以上の時間。  
  
 アプリケーションが呼び出すことができます**SQLBindCol**結果を再バインドするには列を呼び出した後設定**SQLExtendedFetch**、 **SQLFetch**、または**SQLFetchScroll**C データ型、列のサイズとバインドされた列の 10 進数字は同じまま限り、します。 アプリケーションでは、異なるアドレスに列を再バインドする、カーソルは閉じられません必要があります。  
  
 カーソル ライブラリでは、バインドのオフセットを使用する SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性の設定をサポートします。 (**SQLBindCol**この再バインドが発生するに呼び出せる必要はありません)。ODBC 3 のかどうか、カーソル ライブラリを使用 *.x*ドライバー、バインドのオフセットがない場合に使用**SQLFetch**と呼びます。 場合、バインドのオフセットが使用される**SQLFetch**は、ODBC 2、カーソル ライブラリを使用する場合に呼び出されます *。x*ドライバーのため**SQLFetch**にマップされます**SQLExtendedFetch**です。  
  
 カーソル ライブラリ呼び出しをサポートする**SQLBindCol**ブックマーク列をバインドします。  
  
 ODBC 2 を使用場合します。*x*ドライバー、カーソル ライブラリで SQLSTATE HY090 が返されます (無効な文字列長またはバッファー長) と**SQLBindCol**ブックマーク列のバッファーの長さを 4 に等しくない値に設定すると呼びます。 ODBC 3 を使用するときに *.x*ドライバー、カーソル ライブラリにより、バッファーのサイズを変更します。
