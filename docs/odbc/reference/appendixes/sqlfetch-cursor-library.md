---
title: "SQLFetch (カーソル ライブラリ) |Microsoft ドキュメント"
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
- SQLFetch function [ODBC], Cursor Library
ms.assetid: 35a0d493-778b-4fb1-84ee-a13540e2fe0e
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1e5cabca53c503e2cd0c12147248b11da84ed157
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlfetch-cursor-library"></a>SQLFetch (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLFetch**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLFetch**を参照してください[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)です。  
  
 カーソル ライブラリを使用する場合を呼び出す**SQLFetch**いずれかへの呼び出しを混在させることはできません**SQLFetchScroll**または**SQLExtendedFetch**です。  
  
 場合**SQLFetch**呼びますドライバーへの呼び出しを渡す際に、カーソル ライブラリで SQL_ATTR_ROW_ARRAY_SIZE を 1 より大きい値に設定を使用します。 場合は、ドライバーは、ODBC 2 です。*x*ドライバー、行セットのサイズは無視されますを呼び出すと**SQLFetch** 1 行のデータが返されます。  
  
 場合は、カーソル ライブラリは、ODBC 2 と共に使用されます。*x*ドライバー、オフセット (で定義されている SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性) のバインドがない場合に使用**SQLFetch**と呼びます。  
  
 アプリケーションが呼び出すことはできません、カーソル ライブラリが読み込まれるときに**SQLFetch**ブックマーク列をフェッチします。 カーソル ライブラリへの呼び出しに渡します**SQLFetch**を介して、ドライバーが、関数にブックマークを有効にして、ブックマーク列をバインドへの呼び出しによって傍受されるカーソル ライブラリです。

