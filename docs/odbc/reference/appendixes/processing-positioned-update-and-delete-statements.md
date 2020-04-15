---
title: 位置指定更新および削除ステートメントの処理 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- positioned deletes [ODBC]
- ODBC cursor library [ODBC], statement processing
- cursor library [ODBC], positioned update or delete
- positioned updates [ODBC]
- SQL statements [ODBC], cursor library
- ODBC cursor library [ODBC], positioned update or delete
- cursor library [ODBC], statement processing
ms.assetid: 2975dd97-48e6-4d0a-a9c7-40759a7d94c8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4b3f20da018bcd4e28e8ffca097fb5a4373d7f42
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81308023"
---
# <a name="processing-positioned-update-and-delete-statements"></a>位置指定更新と Delete ステートメントの処理
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 カーソル ライブラリでは、このようなステートメントの**WHERE CURRENT OF**句を、バインドされた各列のキャッシュに格納されている値を列挙する**WHERE**句に置き換えることで、位置指定更新および削除ステートメントをサポートします。 カーソル ライブラリは、新しく構築された**UPDATE**ステートメントと**DELETE**ステートメントをドライバーに渡して実行します。 位置指定更新ステートメントの場合、カーソル ライブラリは行セット バッファーの値からキャッシュを更新し、行の状態配列内の対応する値をSQL_ROW_UPDATEDに設定します。 位置指定削除ステートメントの場合、行の状態配列の対応する値をSQL_ROW_DELETEDに設定します。  
  
> [!CAUTION]  
>  現在の行を識別するためにカーソル ライブラリによって作成された**WHERE**句は、行の識別、別の行の識別、または複数行の識別に失敗する可能性があります。 詳細については、後の「[検索ステートメントの作成](../../../odbc/reference/appendixes/constructing-searched-statements.md)」を参照してください。  
  
 位置指定更新および削除ステートメントには、次の制限が適用されます。  
  
-   位置指定更新および削除ステートメントは、**次**の場合にのみ使用できます。**SELECT**ステートメントに結合 **、UNION**句、または**GROUP BY**句が含まれていない場合。また、選択リストで別名または式を使用する列が**SQLBindCol**でバインドされていない場合。  
  
-   アプリケーションが位置指定更新または削除ステートメントを準備する場合は、 SQLFetch または**SQLFetchScroll**を呼び出した後で準備する必要があります。 **SQLFetchScroll** カーソル ライブラリは準備のためにステートメントをドライバーに送信しますが、ステートメントを閉じて、アプリケーションが**SQLExecute**を呼び出すと直接実行します。  
  
-   ドライバーが 1 つのアクティブ ステートメントのみをサポートする場合、カーソル ライブラリは結果セットの残りの部分をフェッチし、現在の行セットをキャッシュから再フェッチしてから、位置指定更新または削除ステートメントを実行します。 アプリケーションが結果セット内のメタデータを返す関数 (**たとえば、SQLNumResultCols**や**SQLDescribeCol)** を呼び出すと、カーソル ライブラリはエラーを返します。  
  
-   更新が実行されるたびに自動的に更新されるタイムスタンプ列を含むテーブルの列に位置指定更新または削除ステートメントを実行すると、後続の位置指定更新または削除ステートメントは、タイム・スタンプ列がバインドされている場合、すべて失敗します。 これは、カーソル ライブラリが作成する検索された更新または削除ステートメントが、更新する行を正確に識別しないために発生します。 タイムスタンプ列の検索されたステートメントの値は、タイムスタンプ列の自動的に更新された値と一致しません。
