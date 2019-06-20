---
title: SQLEndTran (カーソル ライブラリ) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLEndTran function [ODBC], Cursor Library
ms.assetid: 92340b87-9084-4838-a509-e9ca22d5fd5c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e2e218035473d1ebb980aa5f44da8cc7b8ef843d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63199487"
---
# <a name="sqlendtran-cursor-library"></a>SQLEndTran (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないようにして、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLEndTran**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLEndTran**を参照してください[SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)します。  
  
 カーソル ライブラリは、トランザクションをサポートしていませんしへの呼び出しを渡します**SQLEndTran**ドライバーに直接します。 ただし、カーソル ライブラリは SQL_CURSOR_ROLLBACK_BEHAVIOR と SQL_CURSOR_COMMIT_BEHAVIOR 情報の種類を持つデータ ソースによって返されるカーソルのコミットとロールバックの動作をサポートしています。  
  
-   トランザクション間でカーソルを保持するデータ ソースの場合は、データ ソースには、ロールバックされた変更はロールバックされません、カーソル ライブラリのキャッシュにします。 キャッシュのデータ ソースのデータと一致するために、アプリケーションは必要があります、カーソルを閉じて。  
  
-   トランザクションの境界でカーソルを閉じてデータ ソースの場合は、カーソル ライブラリは、カーソルを閉じるし、接続ですべてのステートメントのキャッシュを削除します。  
  
-   をトランザクションの境界で準備されたステートメントを削除するデータ ソースのアプリケーションは、それらの前に、接続でのすべての準備済みステートメントを再び準備する必要があります。
