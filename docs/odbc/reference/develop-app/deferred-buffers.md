---
title: バッファーを遅延 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- buffers [ODBC], deferred
- deferred buffers [ODBC]
ms.assetid: 02c9a75c-2103-4f68-a1db-e31f7e0f1f03
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b494ac404632ed13fc617a9c6638e75bf6b2d1fd
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="deferred-buffers"></a>遅延バッファー
A*遅延バッファー*はしばらくの間で値が使用される 1 つ*後*関数呼び出しに指定されています。 たとえば、 **SQLBindParameter**関連付けるには、使用または*をバインドする*SQL ステートメントにパラメーターを持つデータ バッファー。 アプリケーションは、パラメーターの数を指定し、アドレス、バイトの長さ、およびバッファーの型を渡します。 ドライバーは、この情報を保存するが、バッファーの内容については検査しません。 後で、アプリケーションでは、ステートメントを実行するときに、ドライバー情報を取得しますを使用して、パラメーター データを取得して、データ ソースに送信します。 そのため、バッファー内のデータの入力が遅延されます。 遅延バッファーは 1 つの関数で指定された、他で使用されるため、これは、ドライバーもことを想定して; が存在する遅延のバッファーを解放するアプリケーション プログラミング エラー詳細については、次を参照してください。[割り当てと解放バッファー](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md)、このセクションで後述します。  
  
 入力と出力の両方のバッファーを延期することができます。 次の表は、遅延のバッファーの用途をまとめたものです。 遅延のバッファーが結果セット列にバインドされているがで指定されたことに注意してください**SQLBindCol**、SQL ステートメントのパラメーターにバインドされた遅延のバッファーがで指定されている**SQLBindParameter**です。  
  
|バッファーの使用|型|指定されました。|使用元|  
|----------------|----------|--------------------|-------------|  
|入力パラメーターのデータを送信します。|遅延の入力|**SQLBindParameter**|**SQLExecute**<br /> **SQLExecDirect**|  
|更新または結果の行を挿入するデータの送信の設定|遅延の入力|**SQLBindCol**|**SQLSetPos**|  
|出力パラメーターと入出力パラメーターのデータを返す|遅延出力|**SQLBindParameter**|**SQLExecute**<br /> **SQLExecDirect**|  
|データを設定する結果を返す|遅延出力|**SQLBindCol**|**SQLFetch**<br /> **SQLFetchScroll SQLSetPos**|
