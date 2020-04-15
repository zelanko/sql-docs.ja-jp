---
title: ODBC でのエスケープ シーケンス |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4d41b0c03ecbe6de63cba1a28a1f39f12a42dc86
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300422"
---
# <a name="escape-sequences-in-odbc"></a>ODBC でのエスケープ シーケンス
外部結合やスカラー関数呼び出しなど、多くの言語機能は、一般に DBMS によって実装されています。 ただし、これらの機能の構文は、標準構文がさまざまな標準の本文で定義されている場合でも、DBMS に固有の構文になる傾向があります。 このため、ODBC では、次の言語機能の標準構文を含むエスケープ シーケンスを定義します。  
  
-   日付、時刻、タイムスタンプ、および日時間隔リテラル  
  
-   数値、文字列、データ型変換関数などのスカラー関数  
  
-   LIKE 述部エスケープ文字  
  
-   外部結合  
  
-   プロシージャ コール  
  
 ODBC で使用されるエスケープ シーケンスは次のとおりです。  
  
```  
  
(extension)  
  
```  
  
## <a name="remarks"></a>解説  
 エスケープ シーケンスは、ドライバーによって認識および解析され、エスケープ シーケンスが DBMS 固有の文法に置き換えられます。 エスケープ シーケンス構文の詳細については、「付録 C: SQL 文法」の[「ODBC エスケープ シーケンス](../../../odbc/reference/appendixes/odbc-escape-sequences.md)」を参照してください。  
  
> [!NOTE]  
>  ODBC 2 で。*x*、これはエスケープシーケンスの標準構文でした: **--(\*ベンダー (**_ベンダー名_**), 製品 (**_製品名_**)**_拡張_**\*) -**  
>   
>  この構文に加えて、形式 {_拡張_ **}** の形式の短縮構文が定義されました **。**  
>   
>  ODBC 3 で。*x*を指定すると、エスケープ シーケンスの長い形式は非推奨となり、短縮形は排他的に使用されます。  
  
 エスケープ シーケンスはドライバーによって DBMS 固有の構文にマップされるため、アプリケーションではエスケープ シーケンスまたは DBMS 固有の構文を使用できます。 ただし、DBMS 固有の構文を使用するアプリケーションは相互運用できません。 エスケープ シーケンスを使用する場合、アプリケーションは、SQL_ATTR_NOSCAN ステートメント属性がオフになっていることを確認する必要があります。 それ以外の場合、エスケープ シーケンスはデータ ソースに直接送信され、通常は構文エラーが発生します。  
  
 ドライバーは、基になる言語機能にマップできるエスケープ シーケンスのみをサポートします。 たとえば、データ ソースが外部結合をサポートしていない場合、ドライバーもサポートされません。 サポートされているエスケープ シーケンスを決定するために、アプリケーションは**SQLGetTypeInfo**と**SQLGetInfo**を呼び出します。 詳細については、次のセクション「[日付、時刻、およびタイムスタンプのリテラル](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md)」を参照してください。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [日付、時刻、およびタイムスタンプのリテラル](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md)  
  
-   [スカラー関数の呼び出し](../../../odbc/reference/develop-app/scalar-function-calls.md)  
  
-   [LIKE 述語のエスケープ文字](../../../odbc/reference/develop-app/like-predicate-escape-character.md)  
  
-   [外部結合](../../../odbc/reference/develop-app/outer-joins.md)  
  
-   [プロシージャ呼び出し](../../../odbc/reference/develop-app/procedure-calls.md)
