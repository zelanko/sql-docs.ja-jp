---
title: SQLRowCount |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLRowCount function
ms.assetid: 967ed3d4-3d31-4485-ac92-027076ebc829
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: adc8dbc8083ec1de98951db618dabad8a145d7d6
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82702183"
---
# <a name="sqlrowcount"></a>SQLRowCount
  パラメーター値の配列がステートメントの実行にバインドされると、 `SQLRowCount` ステートメントの実行時にパラメーター値のいずれかの行でエラー状態が発生した場合に SQL_ERROR が返されます。 関数の*Rowcountptr*引数によって値が返されることはありません。  
  
 アプリケーションは、SQL_ATTR_PARAMS_PROCESSED_PTR ステートメント属性を使用して、エラーが発生するまでに処理されたパラメーター数をキャプチャできます。  
  
 また、SQL_ATTR_PARAM_STATUS_PTR ステートメント属性を使用してバインドされた状態値の配列を使用して、問題のあるパラメーター行の配列オフセットをキャプチャできます。 アプリケーションは、状態配列をすべて確認し、実際に処理された行数を判断できます。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]Output 句を使用して INSERT、UPDATE、DELETE、または MERGE ステートメントを実行すると、SQLRowCount は、output 句によって生成された結果セット内のすべての行が使用されるまで、影響を受ける行の数を返しません。 これらの行を使用するには、SQLFetch または SQLFetchScroll を呼び出します。 SQLResultCols は、すべての結果行が使用されるまで-1 を返します。 SQLFetch または SQLFetchScroll が SQL_NO_DATA を返すと、アプリケーションは SQLRowCount を呼び出して、次の結果に移動するために SQLMoreResults を呼び出す前に、影響を受けた行の数を確認する必要があります。  
  
## <a name="see-also"></a>参照  
 [SQLRowCount 関数](https://go.microsoft.com/fwlink/?LinkId=59367)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
