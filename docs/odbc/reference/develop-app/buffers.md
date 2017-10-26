---
title: "バッファー |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- input buffers [ODBC]
- length/indicator buffers [ODBC]
- output buffers [ODBC]
- buffers [ODBC], about buffers
- application buffers [ODBC]
- buffers [ODBC]
ms.assetid: 42c5226c-cb40-4d1e-809f-2ea50ce6bd55
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5953f3409a3886abbf76963d0207a89be1e83aec
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="buffers"></a>バッファー
バッファーは、アプリケーションとドライバーの間でデータを渡すために使用するアプリケーションのメモリの任意の断片です。 たとえば、アプリケーション バッファー関連付けることができる、または*、バインド*結果セットの列**SQLBindCol**です。 各の行がフェッチされる間、これらのバッファー内の各列のデータが返されます。 *入力バッファー*アプリケーションからドライバーにデータを渡すために使用*出力バッファー*ドライバーからアプリケーションにデータを返すために使用します。  
  
> [!NOTE]  
>  ODBC 関数では、SQL_ERROR が返されます、その関数の出力引数の内容は未定義です。  
  
 このディスカッションは、不確定の型のバッファーを主にそれ自体を扱います。 これらのバッファーのアドレスがなどの SQLPOINTER、型の引数として表示されます、 *TargetValuePtr*引数**SQLBindCol**です。 ただし、バッファーで使用する引数など、ここで説明されている項目の一部にも適用する、ドライバーに文字列を渡すための引数、 *TableName*引数**SQLTables**です。  
  
 通常、これらのバッファーはペアになっています。 *データ バッファー*はときに、データ自体を渡すために使用、*長さ/インジケーター バッファー*データ バッファーやデータが NULL であることを示す SQL_NULL_DATA などの特殊な値のデータの長さを渡すために使用します。 データ バッファー内のデータの長さは、それ自体のデータ バッファーの長さと異なります。 次の図は、データ バッファーおよび長さ/インジケーター バッファーの関係を示しています。  
  
 ![データ バッファーおよび長さ (&) #47; インジケーター バッファー](../../../odbc/reference/develop-app/media/pr09.gif "pr09")  
  
 データ バッファーに文字またはバイナリ データなどの可変長データが含まれている場合、長さ/インジケーター バッファーが必要です。 データ バッファーには、整数や日付構造体などの固定長データが含まれている場合、長さ/インジケーター バッファーは、データの長さが既にわかっているので、インジケーターの値を渡すためにのみ必要です。 アプリケーションでは、固定長のデータの長さ/インジケーター バッファーを使用している場合、ドライバーは、渡された任意の長さを無視します。  
  
 データ バッファーとが含まれているデータの両方の長さは文字ではなくバイト単位で測定されます。 この区別はのバイト数と文字の長さが同じなので、ANSI 文字列を使用するプログラムの重要ではありません。  
  
 アプリケーションのデータ バッファーは、ドライバーの定義済みの記述子フィールド、診断フィールドまたは属性を表している場合は、ドライバー マネージャーがフィールドまたは属性の値を示す関数の引数の特性に示す必要があります。 アプリケーションは、次の値のいずれかに、フィールドまたは属性を設定する関数呼び出しで長の引数を設定します。 (同じはフィールドまたは値に設定関数の引数自体では、引数が指す例外で、属性の値を取得する関数の場合は true)。  
  
-   フィールドまたは属性の値を示す関数の引数が文字の文字列へのポインターである場合、*長さ*引数は SQL_NTS または文字列の長さ。  
  
-   フィールドまたは属性の値を示す関数の引数がバイナリ バッファーへのポインターの場合は、アプリケーションは、SQL_LEN_BINARY_ATTR の結果を配置 (*長さ*) でマクロ、*長さ*引数。 これにより、配置に負の値、*長さ*引数。  
  
-   フィールドまたは属性の値を示す関数の引数が文字の文字列またはバイナリ文字列以外の値へのポインターである場合、*長さ*引数は SQL_IS_POINTER 値でなければなりません。  
  
-   フィールドまたは属性の値を示す関数の引数には、固定長の値が含まれている場合、*長さ*引数が SQL_IS_INTEGER、SQL_IS_UINTEGER、SQL_IS_SMALLINT、または SQL_ISI_USMALLINT、必要に応じて。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [遅延バッファー](../../../odbc/reference/develop-app/deferred-buffers.md)  
  
-   [割り当てと解放バッファー](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md)  
  
-   [データ バッファーを使用します。](../../../odbc/reference/develop-app/using-data-buffers.md)

