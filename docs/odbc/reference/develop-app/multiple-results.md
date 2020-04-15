---
title: 複数の結果 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLMoreResults function [ODBC], multiple results
- row counts [ODBC]
- multiple results [ODBC]
- result sets [ODBC], multiple results
- SQLGetInfo function [ODBC], multiple results
ms.assetid: a3c32e4b-8fe7-4a33-ae39-ae664001f315
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d90414b631a7e81a7868ab7974b64ea84a0ea452
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302414"
---
# <a name="multiple-results"></a>複数の結果
*結果*は、ステートメントの実行後にデータ ソースから返されるものです。 ODBC には、結果セットと行数の 2 種類の結果があります。 *行数*は、更新、削除、または挿入ステートメントによって影響を受ける行の数です。 [SQL ステートメントのバッチで説明されているバッチ](../../../odbc/reference/develop-app/batches-of-sql-statements.md)は、複数の結果を生成できます。  
  
 次の表は、データ ソースがバッチの種類ごとに複数の結果を返すかどうかを判断するためにアプリケーションが使用する**SQLGetInfo**オプションを示しています。 特に、データ ソースは、バッチ内の各ステートメントのバッチ全体または個々の行カウントの 1 つの行カウントを返すことができます。 パラメータの配列を使用して実行される結果セット生成ステートメントの場合、データ ソースは、すべてのパラメータ セットに対して 1 つの結果セットを返すか、各パラメータ セットに対して個別の結果セットを返すことができます。  
  
|バッチ タイプ|行数|結果セット|  
|----------------|----------------|-----------------|  
|明示的なバッチ|SQL_BATCH_ROW_COUNT[a]|--[b]|  
|手順|SQL_BATCH_ROW_COUNT[a]|--[b]|  
|パラメータの配列|SQL_PARAM_ARRAYS_ROW_COUNTS|SQL_PARAM_ARRAYS_SELECTS|  
  
 [a] バッチ内の行数生成ステートメントはサポートされている可能性があるが、行数の戻り値はサポートされていない。 **SQLGetInfo**のSQL_BATCH_SUPPORT オプションは、行数生成ステートメントをバッチで使用できるかどうかを示します。SQL_BATCH_ROW_COUNTS オプションは、これらの行数がアプリケーションに返されるかどうかを示します。  
  
 [b] 明示的なバッチとプロシージャは、複数の結果セット生成ステートメントを含む場合、常に複数の結果セットを返します。  
  
> [!NOTE]  
>  ODBC 1.0 で導入されたSQL_MULT_RESULT_SETSオプションは、複数の結果セットを返すことができるかどうかに関する一般的な情報のみを提供します。 特に、SQL_BATCH_SUPPORTに対してSQL_BS_SELECT_EXPLICITまたはSQL_BS_SELECT_PROCビットが返された場合、またはSQL_PARAM_ARRAYS_SELECTに対してSQL_PAS_BATCHが返される場合は、"Y" に設定されます。  
  
 複数の結果を処理するために、アプリケーションは**SQLMoreResults**を呼び出します。 この関数は、現在の結果を破棄し、次の結果を使用可能にします。 これ以上結果が得られなかった場合SQL_NO_DATA返します。 たとえば、次のステートメントがバッチとして実行されるとします。  
  
```  
SELECT * FROM Parts WHERE Price > 100.00;  
UPDATE Parts SET Price = 0.9 * Price WHERE Price > 100.00  
```  
  
 これらのステートメントが実行されると、アプリケーションは**SELECT ステートメント**によって作成された結果セットから行をフェッチします。 行のフェッチが完了すると、再価格設定された部品の数を使用可能にするために**SQLMoreResults**を呼び出します。 必要に応じて **、SQLMoreResults**はフェッチされていない行を破棄し、カーソルを閉じます。 アプリケーションは **、UPDATE**ステートメントによって再価格設定された部分の数を決定する**SQLRowCount**を呼び出します。  
  
 結果が得られる前にバッチ ステートメント全体を実行するかどうかは、ドライバー固有です。 一部の実装では、この場合はこれに当てはまり、この場合はこれに当てはまる場合があります。他の場合は **、SQLMoreResults**を呼び出すと、バッチ内の次のステートメントの実行がトリガーされます。  
  
 バッチ内のステートメントの 1 つが失敗すると **、sqlMoreResults**はSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返します。 ステートメントが失敗した場合、または失敗したステートメントがバッチ内の最後のステートメントであったときにバッチが中止された場合 **、SQLMoreResults**はSQL_ERROR返します。 ステートメントが失敗したときにバッチが中止されず、失敗したステートメントがバッチ内の最後のステートメントではなかった場合 **、SQLMoreResults**はSQL_SUCCESS_WITH_INFO返します。 SQL_SUCCESS_WITH_INFOは、少なくとも 1 つの結果セットまたはカウントが生成され、バッチが中止されないことを示します。
