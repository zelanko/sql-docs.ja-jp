---
title: 文字データや C 文字列 |Microsoft ドキュメント
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
ms.topic: article
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
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ef94062373af41fe662194b707dbdde1d85b438d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="character-data-and-c-strings"></a>文字データと C 文字列
(列名、動的パラメーターは、文字列の属性値など) の可変長文字データを参照する入力パラメーターでは、関連付けられた長さパラメーターがあります。 アプリケーション終了した場合は c 言語で一般的な null 文字を含む文字列、長さの文字列 (null 終端文字を除く) のバイト数または SQL_NTS (Null-Terminated 文字列) のいずれかを引数としては提供します。 負でない長の引数は、関連付けられている文字列の実際の長さを指定します。 Length 引数には、NULL 値とは異なりますが、長さ 0 の文字列を指定する可能性があります。 SQL_NTS 負の値は、null 終端文字を検索する文字列の長さを判別するのには、ドライバーに指示します。  
  
 アプリケーションに、ドライバーから文字データが返されると、ドライバー必要があります常に null で終了します。 これにより、アプリケーションは、文字列または文字配列としてデータを処理するかどうかを選択します。 アプリケーション バッファーがない場合のすべての文字データを返すのに十分な大きさ、ドライバーの null 終端文字によって必要なバイト数を引いたバッファーのバイトの長さに切り捨てます、切り捨てられたデータを null で終端されに格納しますバッファーです。 そのため、アプリケーションが文字データの取得に使用されるバッファーに null 終端文字のため余分なスペースを常に配置する必要があります。 たとえば、50 文字のデータを取得する 51 バイト バッファーが必要です。  
  
 特別な注意が必要、アプリケーションとの送信、またはを使用してパーツで長い文字データを取得するときに、ドライバーの両方で**SQLPutData**または**SQLGetData**です。 データが、一連の null で終わる文字列として渡されると、データが再構築する前に、これらの文字列で、null 終端文字を削除する必要があります。  
  
 ODBC プログラマの数は、文字データと C 文字列に混乱がします。 ODBC 関数を定義するときに、C 言語を使用する成果物は、これが発生しました。 ODBC ドライバーまたはアプリケーションが別の言語を使用している場合: ODBC は、言語に依存しないことに注意してください: この混乱が発生する可能性は低くします。  
  
 文字データを保持するために C 文字列を使用している場合、null 終端文字は、データの一部であると見なされないと、バイト長の一部としてはカウントされません。 たとえば、"ABC\0"C 文字列または文字の配列 {'A'、'B'、'C'} として文字データ"ABC"を保持できます。 データのバイトの長さは 3、文字列または文字配列として扱われるかどうか  
  
 アプリケーションやドライバー、文字データを保持するためによく C 文字列 (文字の null で終わる配列) を使用して、これを行う必要はありません。 C では、文字データがまた (null 終了あり) なしの文字の配列を個別に渡された長さ/インジケーター バッファーのバイト長として扱われますことができます。  
  
 -Null で終わる非配列内の文字データを保持できるバイト長が個別に渡されるためは、文字データに null 文字を埋め込むことが可能です。 ただし、ODBC 関数の動作でもは未定義とかどうか、ドライバーこれを正しく処理ドライバー固有の仕様はします。 したがって、相互運用可能アプリケーションでは、バイナリ データとして埋め込まれた null 文字を含めることができる文字データが常に処理します。
