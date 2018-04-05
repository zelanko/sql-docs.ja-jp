---
title: プロシージャ パラメーター |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
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
- procedure parameters [ODBC]
ms.assetid: 54fd857e-d2cb-467d-bb72-121e67a8e88d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ea30d30d66761e245a89fadd4bea37d6503c458b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="procedure-parameters"></a>プロシージャのパラメーター
プロシージャ呼び出しのパラメーター入力として使用できる、入力/出力、または出力パラメーターです。 これは、すべての他の SQL ステートメントで、入力パラメーターでは常にパラメーターと異なります。  
  
 プロシージャに値を送信する入力パラメーターが使用されます。 たとえば、部品テーブルに PartID、説明、および価格の列があるとします。 InsertPart プロシージャ、テーブル内の各列の入力パラメーターがあります。 例 :  
  
```  
{call InsertPart(?, ?, ?)}  
```  
  
 ドライバーはまで入力バッファーの内容を変更しないでください**SQLExecDirect**または**SQLExecute** SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、SQL_INVALID_HANDLE、または SQL_NO_DATA が返されます。 入力バッファーの内容は変更しないで、 **SQLExecDirect**または**SQLExecute** SQL_NEED_DATA または SQL_STILL_EXECUTING が返されます。  
  
 入力/出力パラメーターは、プロシージャに値を送信し、プロシージャから値を取得の両方に使用されます。 入力と出力パラメーターの両方として、同じパラメーターを使用して混乱する傾向にあり、避ける必要があります。 たとえば、プロシージャが注文 ID を受け取りし、顧客の ID を返します。 これは、1 つの入力/出力パラメーターを定義できます。  
  
```  
{call GetCustID(?)}  
```  
  
 2 つのパラメーターを使用する方がよい場合があります: 注文 ID と出力または顧客 ID の入力/出力パラメーターの入力パラメーター。  
  
```  
{call GetCustID(?, ?)}  
```  
  
 プロシージャの戻り値を取得して、プロシージャ引数; から値を取得する出力パラメーターが使用されます。値を返すプロシージャとも呼ばれる*関数*です。 たとえば、 **GetCustID**に説明した手順は、その注文を検索することがあったかどうかを示す値を返します。 次の呼び出しで最初のパラメーターは、出力パラメーターをプロシージャの戻り値を取得するため、2 番目のパラメーターが入力パラメーター、注文 ID を指定するために使用および 3 番目のパラメーターは、顧客 ID を取得するため、出力パラメーター。  
  
```  
{? = call GetCustID(?, ?)}  
```  
  
 ドライバーの入力値を処理および入出力プロシージャのパラメーターいいえ他の SQL ステートメントでは入力パラメーターとは異なります。 変数の値を取得するステートメントを実行するとこれらのパラメーターにバインドし、データ ソースに送信します。  
  
 ステートメントが実行された後に、ドライバーは、これらのパラメーターにバインドされた変数に、入力/出力の返された値と出力パラメーターを格納します。 値がプロシージャによって返されるすべての結果がフェッチされた後までに設定する保証はありませんこれらが返されますと**SQLMoreResults** SQL_NO_DATA が返されました。 ステートメントの実行エラーが発生する場合、入力/出力パラメーター バッファーまたは出力パラメーターのバッファーの内容は未定義です。  
  
 アプリケーションが呼び出す**SQLProcedure**プロシージャに戻り値があるかどうかを確認します。 呼び出す**SQLProcedureColumns**を各プロシージャ パラメーターの型 (戻り値、入力、入力/出力、または出力) を決定します。
