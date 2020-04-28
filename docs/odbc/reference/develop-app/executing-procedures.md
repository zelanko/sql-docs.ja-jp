---
title: プロシージャの実行 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], procedures
- procedures [ODBC], executing
ms.assetid: a75e497a-4661-438a-a10e-f598c65f81be
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3a796c615d7dfdec11a9acb90ab4b5129cf69717
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305713"
---
# <a name="executing-procedures"></a>プロシージャの実行
ODBC では、プロシージャを実行するための標準のエスケープシーケンスが定義されています。 このシーケンスの構文と、それを使用するコード例については、「[プロシージャ呼び出し](../../../odbc/reference/develop-app/procedure-calls.md)」を参照してください。  
  
 プロシージャを実行するために、アプリケーションは次の操作を実行します。  
  
1.  任意のパラメーターの値を設定します。 詳細については、このセクションで後述する「[ステートメントパラメーター](../../../odbc/reference/develop-app/statement-parameters.md)」を参照してください。  
  
2.  **SQLExecDirect**を呼び出し、プロシージャを実行する SQL ステートメントを含む文字列を渡します。 このステートメントでは、ODBC または DBMS 固有の構文で定義されているエスケープシーケンスを使用できます。DBMS 固有の構文を使用するステートメントは相互運用できません。  
  
3.  **SQLExecDirect**が呼び出されると、ドライバーは次のようになります。  
  
    -   現在のパラメーター値を取得し、必要に応じて変換します。 詳細については、このセクションで後述する「[ステートメントパラメーター](../../../odbc/reference/develop-app/statement-parameters.md)」を参照してください。  
  
    -   データソース内のプロシージャを呼び出し、変換されたパラメーター値を送信します。 ドライバーがプロシージャを呼び出す方法は、ドライバーによって異なります。 たとえば、データソースの SQL 文法を使用するように SQL ステートメントを変更し、このステートメントを実行に送信したり、DBMS のデータストリームプロトコルで定義されているリモートプロシージャコール (RPC) メカニズムを使用してプロシージャを直接呼び出したりする場合があります。  
  
    -   プロシージャが成功したと仮定して、入力/出力パラメーターまたは出力パラメーターまたはプロシージャの戻り値の値を返します。 これらの値は、プロシージャによって生成された他のすべての結果 (行数と結果セット) が処理されるまで使用できない可能性があります。 プロシージャが失敗した場合、ドライバーはエラーを返します。
