---
title: SQLExtendedFetch (カーソル ライブラリ) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExtendedFetch function [ODBC], Cursor Library
ms.assetid: 06fbf06f-127b-475c-b636-7b784918475d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 600d90c14ae8b08a4860f3cff49c1615a9587063
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63199535"
---
# <a name="sqlextendedfetch-cursor-library"></a>SQLExtendedFetch (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないようにして、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLExtendedFetch**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLExtendedFetch**を参照してください[SQLExtendedFetch 関数](../../../odbc/reference/syntax/sqlextendedfetch-function.md)します。  
  
 カーソル ライブラリを実装して**SQLExtendedFetch**を繰り返し呼び出す**SQLFetch**ドライバー。  
  
 カーソル ライブラリ呼び出しをサポートする**SQLExtendedFetch**で、 *FetchOrientation* SQL_FETCH_BOOKMARK の。  
  
 カーソル ライブラリを使用すると、呼び出し**SQLExtendedFetch**いずれかへの呼び出しを混在させることはできません**SQLFetchScroll**または**SQLFetch**します。
