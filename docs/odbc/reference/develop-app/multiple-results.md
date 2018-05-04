---
title: 複数の結果 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLMoreResults function [ODBC], multiple results
- row counts [ODBC]
- multiple results [ODBC]
- result sets [ODBC], multiple results
- SQLGetInfo function [ODBC], multiple results
ms.assetid: a3c32e4b-8fe7-4a33-ae39-ae664001f315
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: be6cb4a2f7f03e63e3da9345b833b0382edd8e9d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="multiple-results"></a>複数の結果
A*結果*ものによって返されるデータ ソース、ステートメントが実行された後にします。 ODBC には 2 つの種類の結果: 結果セットと行の数。 *行のカウント*更新によって影響を受ける行の数は、削除、または insert ステートメントは、します。 説明されているバッチ、 [SQL ステートメントのバッチ](../../../odbc/reference/develop-app/batches-of-sql-statements.md)、複数の結果を生成できます。  
  
 次の表、 **SQLGetInfo**アプリケーションに使用するデータ ソースがバッチの種類ごとの複数の結果を返すかどうかを決定するオプションです。 具体的には、データ ソースは、ステートメントのバッチ全体の 1 つの行の数を返すことができますか、バッチ内の各ステートメントの個別の行をカウントします。 結果 – セットを生成するパラメーターの配列で実行された、ステートメントの場合、データ ソースが単一の結果セットのすべてのパラメーターのセットを返すことができます。 またはパラメーターのセットごとの個々 の結果を設定します。  
  
|バッチの種類|行をカウントします。|結果セット|  
|----------------|----------------|-----------------|  
|明示的なバッチ|SQL_BATCH_ROW_COUNT [a]|-[b]。|  
|手順|SQL_BATCH_ROW_COUNT [a]|-[b]。|  
|パラメーター配列|SQL_PARAM_ARRAYS_ROW_COUNTS|SQL_PARAM_ARRAYS_SELECTS|  
  
 [a] 行のバッチ内のステートメントのカウント – 生成はサポートされている可能性があります、まだ行カウントの戻り値はサポートされません。 SQL_BATCH_SUPPORT オプション**SQLGetInfo**示すかどうか行のカウント – を生成するステートメントがバッチで許可されている; SQL_BATCH_ROW_COUNTS オプションでは、これらの行カウントが、アプリケーションに返されるかどうかを示します。  
  
 [b] 明示的なバッチおよびプロシージャ、複数の結果セット: 生成するステートメントが含まれている、複数の結果セットを常に返します。  
  
> [!NOTE]  
>  ODBC 1.0 で導入された SQL_MULT_RESULT_SETS オプションは、複数の結果セットを返すことのできるかどうかに関する一般的なだけ情報を提供します。 具体的には、SQL_BS_SELECT_EXPLICIT、SQL_BS_SELECT_PROC または bits が SQL_BATCH_SUPPORT に対して返される場合、または SQL_PARAM_ARRAYS_SELECT の SQL_PAS_BATCH が返される場合は"Y"に設定されます。  
  
 複数の結果を処理するアプリケーションを呼び出す**SQLMoreResults**です。 この関数は、現在の結果を破棄し、次の結果を使用できるようにします。 複数結果がない場合に、SQL_NO_DATA を返します。 たとえば、次のステートメントがバッチとして実行します。  
  
```  
SELECT * FROM Parts WHERE Price > 100.00;  
UPDATE Parts SET Price = 0.9 * Price WHERE Price > 100.00  
```  
  
 アプリケーションがによって作成された結果セットから行をフェッチするこれらのステートメントが実行された後、**選択**ステートメントです。 呼び出すことにより、行のフェッチが完了したら、 **SQLMoreResults** repriced された部分の数を使用できるようにします。 必要に応じて、 **SQLMoreResults**取り出されていない行を破棄し、カーソルを閉じます。 その後、アプリケーションを呼び出す**SQLRowCount**方法多くの部分がによって repriced を決定する、**更新**ステートメントです。  
  
 これは、すべての結果を利用する前に、バッチ全体ステートメントが実行するかどうかドライバーに固有です。 一部の実装では、ケースでは、呼び出す他のユーザーに**SQLMoreResults**バッチ内の次のステートメントの実行を開始します。  
  
 バッチ内のステートメントのいずれかが失敗した場合、 **SQLMoreResults** SQL_ERROR または SQL_SUCCESS_WITH_INFO が返されます。 ステートメントが失敗したか失敗したステートメントがバッチ内の最後のステートメントとバッチが中止された場合**SQLMoreResults** SQL_ERROR が返されます。 ステートメントが失敗しました、障害が発生したステートメントなしで、バッチの最後のステートメントとバッチが中断されていない場合**SQLMoreResults** sql_success_with_info が返されます。 SQL_SUCCESS_WITH_INFO は、少なくとも 1 つの結果セットまたはカウントが生成されたことと、バッチが中断されていないことを示します。
