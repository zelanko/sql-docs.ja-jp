---
title: SQLExtendedFetch (カーソル ライブラリ) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLExtendedFetch function [ODBC], Cursor Library
ms.assetid: 06fbf06f-127b-475c-b636-7b784918475d
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 08fa807fcbfd3c55df7edcc221131479edee3e0b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlextendedfetch-cursor-library"></a>SQLExtendedFetch (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLExtendedFetch**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLExtendedFetch**を参照してください[SQLExtendedFetch 関数](../../../odbc/reference/syntax/sqlextendedfetch-function.md)です。  
  
 カーソル ライブラリを実装する**SQLExtendedFetch**を繰り返し呼び出して**SQLFetch**ドライバーにします。  
  
 カーソル ライブラリ呼び出しをサポートする**SQLExtendedFetch**で、 *FetchOrientation* SQL_FETCH_BOOKMARK のです。  
  
 カーソル ライブラリを使用する場合を呼び出す**SQLExtendedFetch**いずれかへの呼び出しを混在させることはできません**SQLFetchScroll**または**SQLFetch**です。
