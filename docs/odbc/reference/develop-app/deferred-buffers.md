---
title: 遅延バッファー |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1f7c90dacc375877b4e449b8d59533ce75ff8a4e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076831"
---
# <a name="deferred-buffers"></a>遅延バッファー
*遅延バッファー*は、関数呼び出しで指定され*た後*、ある時点で値が使用されるバッファーです。 たとえば、 **SQLBindParameter**を使用して、データバッファーを SQL ステートメントのパラメーターと関連付ける (または*バインド*する) ことができます。 このアプリケーションでは、パラメーターの番号を指定し、バッファーのアドレス、バイト長、および型を渡します。 ドライバーはこの情報を保存しますが、バッファーの内容を確認しません。 その後、アプリケーションがステートメントを実行すると、ドライバーは情報を取得し、それを使用してパラメーターデータを取得し、データソースに送信します。 そのため、バッファー内のデータの入力は遅延されます。 遅延バッファーは1つの関数で指定され、別の関数で使用されるため、遅延バッファーを解放するためのアプリケーションプログラミングエラーになります。詳細については、このセクションの後の「[バッファーの割り当てと解放](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md)」を参照してください。  
  
 入力バッファーと出力バッファーの両方を遅延させることができます。 次の表は、遅延バッファーの使用方法をまとめたものです。 結果セットの列にバインドされた遅延バッファーは**SQLBindCol**で指定され、SQL ステートメントのパラメーターにバインドされた遅延バッファーは**SQLBindParameter**で指定されることに注意してください。  
  
|バッファーの使用|種類|指定した場合|使用元|  
|----------------|----------|--------------------|-------------|  
|入力パラメーターのデータの送信|遅延入力|**SQLBindParameter**|**SQLExecute**<br /> **SQLExecDirect**|  
|結果セットに行を更新または挿入するためのデータの送信|遅延入力|**SQLBindCol**|**SQLSetPos**|  
|出力パラメーターと入出力パラメーターのデータを返す|遅延出力|**SQLBindParameter**|**SQLExecute**<br /> **SQLExecDirect**|  
|結果セットデータを返す|遅延出力|**SQLBindCol**|**SQLFetch**<br /> **SQLFetchScroll SQLSetPos**|
