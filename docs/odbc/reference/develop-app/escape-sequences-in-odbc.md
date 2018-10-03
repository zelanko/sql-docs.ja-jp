---
title: ODBC でのエスケープ シーケンス |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC]
- SQL statements [ODBC], escape sequences
- escape sequences [ODBC], about escape sequences
ms.assetid: cf229f21-6c38-4b5b-aca8-f1be0dfeb3d0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33259a56faa19dda2403996b6d6d8930ec2a87be
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706000"
---
# <a name="escape-sequences-in-odbc"></a>ODBC でのエスケープ シーケンス
さまざまな外部結合およびスカラー関数の呼び出しなどの言語機能は通常の Dbms によって実装されます。 ただし、これらの機能の構文は、さまざまな標準化団体によって標準の構文が定義されている場合でも、DBMS 固有にする傾向があります。 このため、ODBC では、標準の構文を次の言語機能を含むエスケープ シーケンスが定義されています。  
  
-   日付、時刻、タイムスタンプ、および datetime interval のリテラル  
  
-   数値などのスカラー関数、文字列、およびデータ型変換関数  
  
-   などの述語のエスケープ文字  
  
-   外部結合  
  
-   プロシージャ呼び出し  
  
 ODBC で使用されるエスケープ シーケンスは次のとおりです。  
  
```  
  
(extension)  
  
```  
  
## <a name="remarks"></a>コメント  
 エスケープ シーケンスが認識され、ドライバーで、エスケープ シーケンスを置き換えます DBMS 固有の文法で解析します。 エスケープ シーケンスの構文の詳細については、次を参照してください。 [ODBC エスケープ シーケンス](../../../odbc/reference/appendixes/odbc-escape-sequences.md)付録 c: SQL の文法でします。  
  
> [!NOTE]  
>  ODBC 2。*x*、これは、エスケープ シーケンスの標準の構文: **--(\*仕入先 (***仕入先名***)、製品 (***製品名***) * * * 拡張機能* **\*)--**  
>   
>  フォームのに加えて、この構文は、略式の構文が定義された: **{***拡張子***}**  
>   
>  ODBC 3。*x*、長い形式のエスケープ シーケンスは非推奨とされました、および短い形式を排他的に使用されます。  
  
 エスケープ シーケンスが、DBMS に固有の構文では、ドライバーによってマップされるため、アプリケーションは、エスケープ シーケンスまたは DBMS 固有の構文を使用できます。 ただし、DBMS 固有の構文を使用するアプリケーションは相互運用できません。 エスケープ シーケンスを使用する場合、アプリケーションは、SQL_ATTR_NOSCAN ステートメント属性を無効にする、既定ではこれを確認してください。 それ以外の場合、エスケープ シーケンスは、構文エラーを一般に発生、場所、データ ソースへの直接送信されます。  
  
 ドライバーは、基になる言語機能にマップできる、エスケープ シーケンスのみをサポートします。 たとえば、データ ソースが外部結合をサポートしていない場合は、ドライバーがも。 アプリケーションが呼び出すエスケープ シーケンスがサポートされているかを判断する**SQLGetTypeInfo**と**SQLGetInfo**します。 詳細については、次のセクションを参照してください。[日付、時刻、およびタイムスタンプのリテラル](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md)します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [日付、時刻、およびタイムスタンプのリテラル](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md)  
  
-   [スカラー関数の呼び出し](../../../odbc/reference/develop-app/scalar-function-calls.md)  
  
-   [LIKE 述語のエスケープ文字](../../../odbc/reference/develop-app/like-predicate-escape-character.md)  
  
-   [外部結合](../../../odbc/reference/develop-app/outer-joins.md)  
  
-   [プロシージャ呼び出し](../../../odbc/reference/develop-app/procedure-calls.md)
