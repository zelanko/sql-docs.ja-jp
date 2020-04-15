---
title: プロシージャの実行 |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305713"
---
# <a name="executing-procedures"></a>プロシージャの実行
ODBC は、プロシージャを実行するための標準エスケープ シーケンスを定義します。 このシーケンスの構文と、それを使用するコード例については、「[プロシージャ呼び出し](../../../odbc/reference/develop-app/procedure-calls.md)」を参照してください。  
  
 プロシージャを実行するには、アプリケーションは次のアクションを実行します。  
  
1.  任意のパラメータの値を設定します。 詳細については、このセクションの[後の「ステートメント パラメータ](../../../odbc/reference/develop-app/statement-parameters.md)」を参照してください。  
  
2.  **SQLExecDirect**を呼び出し、プロシージャを実行する SQL ステートメントを含む文字列を渡します。 このステートメントでは、ODBC または DBMS 固有の構文で定義されたエスケープ シーケンスを使用できます。DBMS 固有の構文を使用するステートメントは相互運用できません。  
  
3.  **SQLExecDirect**が呼び出されると、ドライバーは次のようになります。  
  
    -   現在のパラメーター値を取得し、必要に応じて変換します。 詳細については、このセクションの[後の「ステートメント パラメータ](../../../odbc/reference/develop-app/statement-parameters.md)」を参照してください。  
  
    -   データ ソース内のプロシージャを呼び出し、変換されたパラメーター値を送信します。 ドライバーがプロシージャを呼び出す方法は、ドライバー固有です。 たとえば、データ ソースの SQL 文法を使用してこのステートメントを実行するように SQL ステートメントを変更したり、DBMS のデータ ストリーム プロトコルで定義されているリモート プロシージャ コール (RPC) 機構を使用してプロシージャを直接呼び出したりできます。  
  
    -   プロシージャが成功すると、入力/出力パラメーターまたは出力パラメーターの値、またはプロシージャの戻り値を返します。 これらの値は、プロシージャーによって生成された他のすべての結果 (行カウントおよび結果セット) が処理されるまで使用できない場合があります。 手順が失敗した場合、ドライバーはエラーを返します。
