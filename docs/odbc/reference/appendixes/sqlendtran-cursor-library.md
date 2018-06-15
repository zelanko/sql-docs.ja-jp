---
title: SQLEndTran (カーソル ライブラリ) |Microsoft ドキュメント
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
- SQLEndTran function [ODBC], Cursor Library
ms.assetid: 92340b87-9084-4838-a509-e9ca22d5fd5c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5fe61f62906c113d7ea07c96f20f816456c6bfb1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907417"
---
# <a name="sqlendtran-cursor-library"></a>SQLEndTran (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLEndTran**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLEndTran**を参照してください[SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。  
  
 カーソル ライブラリは、トランザクションをサポートしないへの呼び出しを渡す**SQLEndTran**ドライバーに直接できます。 ただし、カーソル ライブラリは SQL_CURSOR_ROLLBACK_BEHAVIOR と SQL_CURSOR_COMMIT_BEHAVIOR 情報の種類を持つデータ ソースによって返されるカーソルのコミットとロールバックの動作をサポートしています。  
  
-   トランザクション間でカーソルを保持しているデータ ソース、データ ソースにロールバックされる変更はロールバックされません、カーソル ライブラリのキャッシュにします。 データ ソースのデータと一致するキャッシュをするためには、アプリケーションする必要があります閉じてから、カーソル。  
  
-   データ ソースに対してトランザクションの境界でカーソルを閉じることのカーソル ライブラリ、カーソルを閉じるし、接続ですべてのステートメントのキャッシュを削除します。  
  
-   をトランザクション境界で準備されたステートメントを削除するデータ ソースのアプリケーションは、それらの前に、接続ですべての準備されたステートメントを再び準備する必要があります。
