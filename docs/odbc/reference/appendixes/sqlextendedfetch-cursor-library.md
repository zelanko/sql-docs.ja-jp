---
title: "SQLExtendedFetch (カーソル ライブラリ) |Microsoft ドキュメント"
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
- SQLExtendedFetch function [ODBC], Cursor Library
ms.assetid: 06fbf06f-127b-475c-b636-7b784918475d
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9c39b299dc2f42fdf1eb51010e7b4fac2bb9bcfd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlextendedfetch-cursor-library"></a>SQLExtendedFetch (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLExtendedFetch**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLExtendedFetch**を参照してください[SQLExtendedFetch 関数](../../../odbc/reference/syntax/sqlextendedfetch-function.md)です。  
  
 カーソル ライブラリを実装する**SQLExtendedFetch**を繰り返し呼び出して**SQLFetch**ドライバーにします。  
  
 カーソル ライブラリ呼び出しをサポートする**SQLExtendedFetch**で、 *FetchOrientation* SQL_FETCH_BOOKMARK のです。  
  
 カーソル ライブラリを使用する場合を呼び出す**SQLExtendedFetch**いずれかへの呼び出しを混在させることはできません**SQLFetchScroll**または**SQLFetch**です。
