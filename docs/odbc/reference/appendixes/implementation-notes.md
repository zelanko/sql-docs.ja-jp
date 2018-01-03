---
title: "実装に関するメモ |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ec14b9c-69b8-4c6e-838a-88d1ebdc8725
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 017c58b72d1b190d8d11f08cf7ecce5ff58f65b1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="implementation-notes"></a>実装に関するメモ
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このセクションでは、ODBC カーソル ライブラリを実装する方法について説明します。 カーソル ライブラリによるそのキャッシュに格納方法、SQL ステートメントを実行方法、および ODBC 関数を実装する方法を説明します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [カーソル ライブラリのキャッシュ](../../../odbc/reference/appendixes/cursor-library-cache.md)  
  
-   [SQL ステートメントの処理](../../../odbc/reference/appendixes/processing-sql-statements.md)  
  
-   [ODBC 関数およびカーソル ライブラリ](../../../odbc/reference/appendixes/odbc-functions-and-the-cursor-library.md)
