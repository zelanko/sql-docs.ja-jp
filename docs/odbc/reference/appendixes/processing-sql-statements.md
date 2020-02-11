---
title: SQL ステートメントの処理 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], statement processing
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
ms.assetid: 54dad6a3-e86c-477b-ba7c-4e95e0385ec1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d9452ade90f6967dff6d72d5692efcf91b93154d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68057244"
---
# <a name="processing-sql-statements"></a>SQL ステートメントの処理
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新しい開発作業ではこの機能の使用を避け、現在この機能を使用しているアプリケーションの変更を検討してください。 Microsoft では、ドライバーのカーソル機能を使用することをお勧めします。  
  
 ODBC カーソルライブラリは、次の点を除いて、すべての SQL ステートメントを直接ドライバーに渡します。  
  
-   位置指定の update および delete ステートメント  
  
-   **SELECT FOR UPDATE**ステートメント  
  
-   バッチ処理された SQL ステートメント  
  
 位置指定の update および delete ステートメントを実行し、その行の**SQLGetData**を呼び出すためにカーソルを行に配置するには、カーソルライブラリによって、その行を識別する検索ステートメントが作成されます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [位置指定更新と Delete ステートメントの処理](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md)  
  
-   [SELECT FOR UPDATE ステートメントの処理](../../../odbc/reference/appendixes/processing-select-for-update-statements.md)  
  
-   [SQL ステートメントのバッチ処理](../../../odbc/reference/appendixes/processing-batches-of-sql-statements.md)  
  
-   [検索ステートメントの構築](../../../odbc/reference/appendixes/constructing-searched-statements.md)
