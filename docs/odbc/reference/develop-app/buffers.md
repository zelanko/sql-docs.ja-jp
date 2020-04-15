---
title: バッファ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- input buffers [ODBC]
- length/indicator buffers [ODBC]
- output buffers [ODBC]
- buffers [ODBC], about buffers
- application buffers [ODBC]
- buffers [ODBC]
ms.assetid: 42c5226c-cb40-4d1e-809f-2ea50ce6bd55
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0c49e83e12463665f86f8cc15dc595e6ba2c506f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306287"
---
# <a name="buffers"></a>バッファー
バッファは、アプリケーションとドライバの間でデータを渡すために使用されるアプリケーション メモリの一部です。 たとえば、アプリケーション バッファーは**SQLBindCol**を使用して結果セット列に関連付けたり *、バインド*したりできます。 各行がフェッチされると、これらのバッファー内の各列に対してデータが返されます。 *入力バッファーは*、アプリケーションからドライバーにデータを渡すために使用されます。*出力バッファーは、* ドライバーからアプリケーションにデータを返すために使用されます。  
  
> [!NOTE]  
>  ODBC 関数がSQL_ERRORを返す場合、その関数に対する出力引数の内容は未定義になります。  
  
 この議論は、主に不確定型のバッファに関するものです。 これらのバッファーのアドレスは **、SQLBindCol**の*引数*として、たとえば、SQLPOINTER 型の引数として表示されます。 ただし、ここで説明する項目の一部 (バッファーで使用される引数など) は **、SQLTables**の*TableName*引数など、ドライバーに文字列を渡すために使用される引数にも適用されます。  
  
 これらのバッファは通常、ペアで提供されます。 *データ バッファー*はデータ自体を渡すために使用され、*長さ/インジケーター バッファー*はデータ バッファー内のデータの長さやSQL_NULL_DATAなどの特殊な値を渡すために使用されます。 データ バッファー内のデータの長さは、データ バッファー自体の長さと異なります。 次の図は、データ バッファーと長さ/インジケーター バッファーの関係を示しています。  
  
 ![データバッファーと長さ&#47;インジケーター・バッファー](../../../odbc/reference/develop-app/media/pr09.gif "pr09")  
  
 長さ/インジケーター バッファーは、データ バッファーに文字データやバイナリ データなどの可変長データが含まれている場合には必ず必要です。 データ・バッファーに整数または日付構造などの固定長データが入っている場合、データの長さが既にわかっているため、長さ/標識バッファーは標識値を渡すためだけに必要です。 アプリケーションが固定長データを持つ長さ/インジケーター バッファーを使用する場合、ドライバーは、その中に渡された長さを無視します。  
  
 データ バッファーとそれに含まれるデータの長さは、文字ではなくバイト単位で測定されます。 この区別は、バイトと文字の長さが同じであるため、ANSI 文字列を使用するプログラムでは重要ではありません。  
  
 データ バッファーは、ドライバー定義の記述子フィールド、診断フィールド、または属性を表す場合、アプリケーションは、ドライバー マネージャーに、フィールドまたは属性の値を示す関数の引数の性質を示す必要があります。 アプリケーションは、フィールドまたは属性を次のいずれかの値に設定する関数呼び出しで length 引数を設定することで、これを行います。 (フィールドまたは属性の値を取得する関数についても同じですが、引数が引数自体にある値を指している点が異なります)。  
  
-   フィールドまたは属性の値を示す関数引数が文字列へのポインターである場合、*長さ*引数はストリングまたはSQL_NTSの長さになります。  
  
-   フィールドまたは属性の値を示す関数引数がバイナリー・バッファーへのポインターである場合、アプリケーションは、length*引数に*SQL_LEN_BINARY_ATTR(*length*) マクロの結果を入れます。 この場合、*長さの*引数に負の値が入ります。  
  
-   フィールドまたは属性の値を示す関数引数が、文字列またはバイナリ文字列以外の値へのポインターである場合 *、length*引数にはSQL_IS_POINTER値を指定する必要があります。  
  
-   フィールドまたは属性の値を示す関数引数に固定長値が含まれている場合 *、length*引数は、必要に応じてSQL_IS_INTEGER、SQL_IS_UINTEGER、SQL_IS_SMALLINT、またはSQL_ISI_USMALLINTになります。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [遅延バッファー](../../../odbc/reference/develop-app/deferred-buffers.md)  
  
-   [バッファーの割り当てと解放](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md)  
  
-   [データ バッファーの使用](../../../odbc/reference/develop-app/using-data-buffers.md)
