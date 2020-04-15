---
title: SQLEndTRAN (カーソル ライブラリ) |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c2277a67cd5410ea3c2a5d5b03b16d4533ed6ee1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304773"
---
# <a name="sqlendtran-cursor-library"></a>SQLEndTran (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソル・ライブラリーでの**SQLEndTran**関数の使用について説明します。 **SQLEndTran**の一般的な情報については、「 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)」を参照してください。  
  
 カーソル ライブラリはトランザクションをサポートせず **、SQLEndTran**への呼び出しをドライバーに直接渡します。 ただし、カーソル ライブラリは、データ ソースから返されるカーソル のコミットおよびロールバックの動作を、SQL_CURSOR_ROLLBACK_BEHAVIORおよびSQL_CURSOR_COMMIT_BEHAVIOR情報型でサポートしています。  
  
-   トランザクション間でカーソルを保持するデータ ソースの場合、データ ソースでロールバックされた変更は、カーソル ライブラリのキャッシュにロールバックされません。 キャッシュをデータ ソース内のデータと一致させるには、アプリケーションでカーソルを閉じて再度開く必要があります。  
  
-   トランザクション境界でカーソルをクローズするデータ・ソースの場合、カーソル・ライブラリーはカーソルをクローズし、接続上のすべてのステートメントのキャッシュを削除します。  
  
-   トランザクション境界で準備済みステートメントを削除するデータ・ソースの場合、アプリケーションは、接続上のすべての準備済みステートメントを再準備してから、それらを再実行する必要があります。
