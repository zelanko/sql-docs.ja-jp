---
title: 結果セットは作成されましたか? | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], determining if created
ms.assetid: 4a83b8cb-2d57-4e64-b497-80bd587ee1f9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c171a154dd16a291c5dbe1dcade8c01ea95fb084
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294550"
---
# <a name="was-a-result-set-created"></a>結果セットは作成されましたか?
ほとんどの場合、アプリケーション プログラマは、アプリケーションが実行するステートメントが結果セットを作成するかどうかを知っています。 これは、アプリケーションがプログラマによって作成されたハードコーディングされた SQL ステートメントを使用する場合に当てはまる場合です。 通常、アプリケーションが実行時に SQL ステートメントを作成する場合に、プログラマは**SELECT**ステートメントまたは**INSERT**ステートメントのどちらを構築するかを示すコードを簡単にインクルードできます。 いくつかの状況では、プログラマはステートメントが結果セットを作成するかどうかを知ることはできません。 これは、アプリケーションがユーザーが SQL ステートメントを入力して実行する方法を提供する場合に当てはまります。 アプリケーションが実行時にプロシージャを実行するステートメントを構築する場合も同様です。  
  
 このような場合、アプリケーションは**SQLNumResultCols**を呼び出して、結果セット内の列の数を決定します。 これが 0 の場合、ステートメントは結果セットを作成しませんでした。他の数値の場合、ステートメントは結果セットを作成しました。  
  
 アプリケーションは、ステートメントの準備または実行後にいつでも**SQLNumResultCols**を呼び出すことができます。 ただし、データ ソースによっては、準備済みステートメントによって作成される結果セットを簡単に記述できないため、ステートメントの準備後、実行前に**SQLNumResultCols**が呼び出されると、パフォーマンスが低下します。  
  
 一部のデータ ソースでは、SQL ステートメントが結果セットに返す行数の決定もサポートされます。 これを行うには、アプリケーションは**SQLRowCount**を呼び出します。 行数が表す正確な内容は、 **SQLGetInfo**の呼び出しによって返されるSQL_DYNAMIC_CURSOR_ATTRIBUTES2、SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2、SQL_KEYSET_CURSOR_ATTRIBUTES2、またはSQL_STATIC_CURSOR_ATTRIBUTES2オプションの設定によって示されます( カーソルのタイプに応じて)。 このビットマスクは、各カーソル・タイプについて、返される行数が正確であるか、近似であるか、まったく使用できないかを示します。 静的カーソルまたはキーセット ドリブン カーソルの行数が**SQLBulkOperations**または**SQLSetPos**を使用した変更によって影響を受けるかどうか、または位置指定更新または削除ステートメントによって影響を受けるかどうかは、上記のオプション引数によって返される他のビットによって決まります。 詳細については[、SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明を参照してください。
