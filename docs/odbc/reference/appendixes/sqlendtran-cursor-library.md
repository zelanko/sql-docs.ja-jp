---
title: SQLEndTran (カーソルライブラリ) |Microsoft Docs
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
ms.openlocfilehash: f713f9a0c96aaf3798cf160e648404470e3a4363
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064506"
---
# <a name="sqlendtran-cursor-library"></a>SQLEndTran (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新しい開発作業ではこの機能の使用を避け、現在この機能を使用しているアプリケーションの変更を検討してください。 Microsoft では、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソルライブラリでの**SQLEndTran**関数の使用について説明します。 **SQLEndTran**の一般的な情報については、「 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)」を参照してください。  
  
 カーソルライブラリはトランザクションをサポートしていないため、 **SQLEndTran**への呼び出しを直接ドライバーに渡します。 ただし、カーソルライブラリでは、データソースから返されるカーソルのコミットとロールバックの動作がサポートされており、SQL_CURSOR_ROLLBACK_BEHAVIOR と SQL_CURSOR_COMMIT_BEHAVIOR の情報の種類があります。  
  
-   トランザクション間でカーソルを保持するデータソースの場合、データソースでロールバックされた変更は、カーソルライブラリのキャッシュでロールバックされません。 キャッシュがデータソース内のデータと一致するようにするには、アプリケーションがカーソルを閉じてから再度開く必要があります。  
  
-   トランザクションの境界でカーソルを閉じるデータソースでは、カーソルライブラリによってカーソルが閉じられ、接続上のすべてのステートメントのキャッシュが削除されます。  
  
-   トランザクションの境界で準備されたステートメントを削除するデータソースの場合、アプリケーションは、接続で準備されたすべてのステートメントを再実行する前に再準備する必要があります。
