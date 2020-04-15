---
title: 遅延バッファ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- buffers [ODBC], deferred
- deferred buffers [ODBC]
ms.assetid: 02c9a75c-2103-4f68-a1db-e31f7e0f1f03
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f34c6d3d886a0a75c309dc4f5c71f5c7ba3df447
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305983"
---
# <a name="deferred-buffers"></a>遅延バッファー
*遅延バッファー*とは、関数呼び出しで指定された*後*に、ある時点で値が使用されるバッファーです。 たとえば **、SQLBindParameter**は、SQL ステートメントのパラメーターにデータ バッファーを関連付ける (*バインド*) するために使用します。 アプリケーションは、パラメーターの数を指定し、アドレス、バイト長、およびバッファーの型を渡します。 ドライバーは、この情報を保存しますが、バッファーの内容を調べません。 その後、アプリケーションがステートメントを実行すると、ドライバーは情報を取得し、パラメーター データを取得し、データ ソースに送信するを使用します。 したがって、バッファー内のデータの入力は遅延されます。 遅延バッファーは、ある関数で指定され、別の関数で使用されるため、遅延バッファーを解放するアプリケーション プログラミング エラーは、ドライバーが存在することを期待している間です。詳細については、このセクションの後半の[「バッファの割り当てと解放](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md)」を参照してください。  
  
 入力バッファーと出力バッファーの両方を据え置くことができます。 次の表は、遅延バッファーの使用を要約したものです。 結果セット列にバインドされた遅延バッファーは**SQLBindCol**で指定され、SQL ステートメント パラメーターにバインドされた遅延バッファーは**SQLBindParameter**で指定されます。  
  
|バッファの使用|Type|で指定|使用元|  
|----------------|----------|--------------------|-------------|  
|入力パラメータのデータの送信|遅延入力|**SQLBindParameter**|**SQLExecute**<br /> **SQLExecDirect**|  
|結果セット内の行を更新または挿入するためのデータの送信|遅延入力|**SQLBindCol**|**SQLSetPos**|  
|出力パラメータおよび入出力パラメータのデータの返す|遅延出力|**SQLBindParameter**|**SQLExecute**<br /> **SQLExecDirect**|  
|結果セット・データの戻り|遅延出力|**SQLBindCol**|**SQLFetch**<br /> **SQL フェッチスクロール**|
