---
title: "SQL ステートメントの処理 |Microsoft ドキュメント"
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
helpviewer_keywords:
- ODBC cursor library [ODBC], statement processing
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
ms.assetid: 54dad6a3-e86c-477b-ba7c-4e95e0385ec1
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 754630b1c125f416c52645510969c1165d8567ae
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="processing-sql-statements"></a>SQL ステートメントの処理
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 ODBC カーソル ライブラリは、次を除くドライバーに直接すべての SQL ステートメントに渡します。  
  
-   更新プログラムの配置、および delete ステートメント  
  
-   **SELECT FOR UPDATE**ステートメント  
  
-   バッチ化された SQL ステートメント  
  
 位置指定更新を実行し、ステートメントを削除しを呼び出して行にカーソルを置き**SQLGetData**カーソル ライブラリは、その行に対して行を識別する検索結果のステートメントを構築します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [位置指定更新と Delete ステートメントの処理](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md)  
  
-   [SELECT FOR UPDATE ステートメントの処理](../../../odbc/reference/appendixes/processing-select-for-update-statements.md)  
  
-   [SQL ステートメントのバッチ処理](../../../odbc/reference/appendixes/processing-batches-of-sql-statements.md)  
  
-   [検索ステートメントの構築](../../../odbc/reference/appendixes/constructing-searched-statements.md)
