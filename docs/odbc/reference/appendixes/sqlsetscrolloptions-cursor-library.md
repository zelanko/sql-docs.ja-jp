---
title: "SQLSetScrollOptions (カーソル ライブラリ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLSetScrollOptions function [ODBC], Cursor Library
ms.assetid: c5c0ac6d-a6c1-4077-8186-1644df1944f8
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f97c24e12dd7a5ea0108eb791cb03a2c405bd205
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlsetscrolloptions-cursor-library"></a>SQLSetScrollOptions (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLSetScrollOptions**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLSetScrollOptions**を参照してください[SQLSetScrollOptions 関数](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)です。  
  
 カーソル ライブラリがサポートされる**SQLSetScrollOptions**旧バージョンと互換性のためだけのアプリケーションする必要があります、SQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_TYPE、および SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性代わりに使用します。
