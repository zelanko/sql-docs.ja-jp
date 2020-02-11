---
title: ODBC でのエスケープシーケンス |Microsoft Docs
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
ms.openlocfilehash: 17183a7eacdc5348eea0ddcd7aee4cc493249e77
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68051124"
---
# <a name="escape-sequences-in-odbc"></a>ODBC でのエスケープ シーケンス
外部結合やスカラー関数呼び出しなどの多くの言語機能は、通常、Dbms によって実装されます。 ただし、これらの機能の構文は、標準の構文がさまざまな標準の本体によって定義されている場合でも、DBMS 固有の傾向があります。 このため、ODBC では、次の言語機能の標準的な構文を含むエスケープシーケンスが定義されています。  
  
-   Date、time、timestamp、および datetime interval リテラル  
  
-   数値、文字列、データ型変換関数などのスカラー関数  
  
-   LIKE 述語エスケープ文字  
  
-   外部結合  
  
-   プロシージャ呼び出し  
  
 ODBC で使用されるエスケープシーケンスは次のとおりです。  
  
```  
  
(extension)  
  
```  
  
## <a name="remarks"></a>解説  
 エスケープシーケンスは、ドライバーによって認識および解析されます。これにより、エスケープシーケンスは DBMS 固有の文法に置き換えられます。 エスケープシーケンスの構文の詳細については、「付録 C: SQL 文法」の「 [ODBC エスケープシーケンス](../../../odbc/reference/appendixes/odbc-escape-sequences.md)」を参照してください。  
  
> [!NOTE]  
>  ODBC 2 の場合。*x*は、エスケープシーケンスの標準構文です。 **--\*(vendor (**_ベンダ名_**)、product (**_製品名_**)**_拡張機能_ ** \*)--**  
>   
>  この構文に加えて、次の形式で短縮構文が定義されています: **{**_extension_**}**  
>   
>  ODBC 3 の場合。*x*では、エスケープシーケンスの長い形式は非推奨とされており、短縮形は排他的に使用されます。  
  
 エスケープシーケンスは、ドライバーによって DBMS 固有の構文にマップされるため、アプリケーションでは、エスケープシーケンスまたは DBMS 固有の構文のいずれかを使用できます。 ただし、DBMS 固有の構文を使用するアプリケーションは相互運用できません。 エスケープシーケンスを使用する場合、アプリケーションは、SQL_ATTR_NOSCAN statement 属性が既定で無効になっていることを確認する必要があります。 それ以外の場合、エスケープシーケンスはデータソースに直接送信されます。この場合、通常は構文エラーが発生します。  
  
 ドライバーは、基になる言語機能にマップできるエスケープシーケンスだけをサポートします。 たとえば、データソースが外部結合をサポートしていない場合は、どちらのドライバーも使用できません。 サポートされているエスケープシーケンスを特定するために、アプリケーションは**SQLGetTypeInfo**と**SQLGetInfo**を呼び出します。 詳細については、次のセクション「[日付、時刻、およびタイムスタンプリテラル](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md)」を参照してください。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [日付、時刻、およびタイムスタンプのリテラル](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md)  
  
-   [スカラー関数の呼び出し](../../../odbc/reference/develop-app/scalar-function-calls.md)  
  
-   [LIKE 述語のエスケープ文字](../../../odbc/reference/develop-app/like-predicate-escape-character.md)  
  
-   [外部結合](../../../odbc/reference/develop-app/outer-joins.md)  
  
-   [プロシージャ呼び出し](../../../odbc/reference/develop-app/procedure-calls.md)
