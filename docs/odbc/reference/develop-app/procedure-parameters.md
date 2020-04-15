---
title: プロシージャ パラメータ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- procedure parameters [ODBC]
ms.assetid: 54fd857e-d2cb-467d-bb72-121e67a8e88d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 35d43ca7cf6e603d7dabca9eacf1e026daa753b7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306960"
---
# <a name="procedure-parameters"></a>プロシージャのパラメーター
プロシージャ コールのパラメータは、入力パラメータ、入出力パラメータ、出力パラメータです。 これは、常に入力パラメーターである他のすべての SQL ステートメントのパラメーターとは異なります。  
  
 入力パラメータは、プロシージャに値を送信するために使用されます。 たとえば、パーツ テーブルに [パーツ ID]、[説明]、および [価格] 列があるとします。 InsertPart プロシージャには、テーブル内の各列の入力パラメーターがあります。 次に例を示します。  
  
```  
{call InsertPart(?, ?, ?)}  
```  
  
 **SQLExecDirect**または**SQLExecute**がSQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、SQL_INVALID_HANDLE、またはSQL_NO_DATAを返すまで、ドライバーは入力バッファーの内容を変更しないでください。 入力バッファーの内容は **、SQLExecDirect**または**SQLExecute**がSQL_NEED_DATAまたはSQL_STILL_EXECUTINGを返す間は変更しないでください。  
  
 入力/出力パラメータは、プロシージャに値を送信し、プロシージャから値を取得するために使用されます。 入力パラメータと出力パラメータの両方と同じパラメータを使用すると、混乱が生じやすくなり、避ける必要があります。 たとえば、あるプロシージャが注文 ID を受け取り、顧客の ID を返したとします。 これは、単一の入出力パラメータで定義できます。  
  
```  
{call GetCustID(?)}  
```  
  
 注文 ID の入力パラメーターと、顧客 ID の出力または入出力パラメーターの 2 つのパラメーターを使用する方が良い場合があります。  
  
```  
{call GetCustID(?, ?)}  
```  
  
 出力パラメータは、プロシージャの戻り値を取得し、プロシージャ引数から値を取得するために使用されます。値を返すプロシージャは、*関数*と呼ばれることもあります。 たとえば、前述の**GetCustID**プロシージャが、注文を見つけることができたかどうかを示す値を返したとします。 次の呼び出しでは、最初のパラメーターはプロシージャの戻り値を取得するために使用される出力パラメーター、2 番目のパラメーターは注文 ID の指定に使用される入力パラメーター、3 番目のパラメーターは顧客 ID の取得に使用される出力パラメーターです。  
  
```  
{? = call GetCustID(?, ?)}  
```  
  
 ドライバーは、他の SQL ステートメントの入力パラメーターと変わらない手順で入力パラメーターと入出力パラメーターの値を処理します。 ステートメントが実行されると、これらのパラメーターにバインドされた変数の値を取得して、データ ソースに送信します。  
  
 ステートメントが実行された後、ドライバーは、入力/出力パラメーターの戻り値を、それらのパラメーターにバインドされた変数に格納します。 これらの戻り値は、プロシージャから返されるすべての結果がフェッチされ **、SQLMoreResults**がSQL_NO_DATA返されるまで、設定される保証はありません。 ステートメントを実行するとエラーが発生した場合、入力/出力パラメーター バッファーまたは出力パラメーター バッファーの内容は未定義です。  
  
 アプリケーションは、プロシージャに戻り値があるかどうかを判断するために**SQLProcedure**を呼び出します。 **SQLProcedureColumns を**呼び出して、各プロシージャ パラメータの型 (戻り値、入力値、入出力、または出力) を決定します。
