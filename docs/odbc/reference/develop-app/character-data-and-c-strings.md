---
title: 文字データと C 文字列 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data buffers [ODBC], length
- data buffers [ODBC], character data
- buffers [ODBC], C strings
- buffers [ODBC], character data
- character data and buffers [ODBC]
- length of data buffers [ODBC]
- data buffers [ODBC], C strings
- buffers [ODBC], length
- C strings and buffers [ODBC]
ms.assetid: 3a141cb4-229d-4027-9349-615cb2995e36
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7bb25022d4e0c0559f2a8f77b89a4ba26aeba33a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307492"
---
# <a name="character-data-and-c-strings"></a>文字データと C 文字列
可変長文字データを参照する入力パラメーター (列名、動的パラメーター、文字列属性値など) には、長さのパラメーターが関連付けられます。 C で一般的に示されているように、アプリケーションが null 文字で文字列を終了する場合は、文字列の長さ (null 終端文字を含まない) またはSQL_NTS (Null-Terminate String) のどちらかの引数として提供されます。 負でない長さ引数は、関連付けられた文字列の実際の長さを指定します。 長さ引数を 0 に設定すると、長さ 0 の文字列を指定できます。 負の値SQL_NTS、null 終端文字を見つけることによって、文字列の長さを決定するドライバーを指示します。  
  
 ドライバーからアプリケーションに文字データが返される場合、ドライバーは常に null 終了する必要があります。 これにより、アプリケーションはデータを文字列として処理するか、文字配列として処理するかを選択できます。 アプリケーション バッファーがすべての文字データを返すのに十分な大きさでない場合、ドライバーは、null 終了文字で必要なバイト数を減らすバッファーのバイト長に切り捨て、切り捨てられたデータを null 終了し、バッファーに格納します。 したがって、アプリケーションは、文字データの取得に使用されるバッファー内の NULL 終了文字用の余分なスペースを常に割り振る必要があります。 例えば、50 文字のデータを取り出すためには、51 バイトのバッファーが必要です。  
  
 **SQLPutData**または**SQLGetData**を使用して長い文字データを送信または取得する場合は、アプリケーションとドライバーの両方で特別な注意が必要です。 データが一連の null で終わる文字列として渡される場合、データを再構成する前に、これらの文字列の NULL 終了文字を削除する必要があります。  
  
 多くの ODBC プログラマが、文字データと C 文字列を混同しています。 これが起こったことは、ODBC 関数を定義するときに C 言語を使用する機能です。 ODBC ドライバまたはアプリケーションが別の言語を使用している場合、ODBC は言語に依存しないため、この混乱が発生する可能性は低くなります。  
  
 C 文字列を使用して文字データを保持する場合、NULL 終端文字はデータの一部とは見なされず、バイト長の一部としてカウントされません。 たとえば、文字データ "ABC" は、C 文字列 "ABC\0" または文字配列 {'A'、'B'、'C'} として保持できます。 データのバイト長は、文字列または文字配列として扱われるかどうかにかかわらず、3 です。  
  
 アプリケーションとドライバーは、文字データを保持するために C 文字列 (null で終端された文字の配列) を使用しますが、これを行う必要はありません。 C では、文字データは文字の配列として扱われ (ヌル終了なし)、バイト長は長さ/インジケーターバッファーで別々に渡されます。  
  
 文字データは NULL で終わる配列以外の配列に保持でき、バイト長は別々に渡されるため、文字データに NULL 文字を埋め込むことができます。 ただし、この場合の ODBC 関数の動作は定義されず、ドライバーがこれを正しく処理するかどうかは、ドライバー固有です。 したがって、相互運用可能なアプリケーションでは、バイナリ データとして null 文字を埋め込むことができる文字データを常に処理する必要があります。
