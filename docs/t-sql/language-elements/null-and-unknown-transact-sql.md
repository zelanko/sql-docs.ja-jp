---
title: "NULL および不明 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 9d491846-4730-4740-a680-77c69fae4a58
caps.latest.revision: 5
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bdac1899707b3caa4f4c515324511a47830f2722
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="null-and-unknown-transact-sql"></a>NULL および不明 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  NULL では、値が不明であることを示します。 Null 値では、空または 0 の値と異なるです。 2 つの NULL 値は等しいとは限りません。 各 NULL の値が不明であるために、2 つの null 値または null 値とその他の値の間の比較は不明な返します。  
  
 Null 値は、通常、不明な適用できないデータを示すか、後で追加します。 たとえば、受注時には顧客のミドル名イニシャルはわかりません。  
  
 Null 値については、次に注意してください。  
  
-   クエリ内で NULL 値を調べるには、WHERE 句で IS NULL または IS NOT NULL を使用します。  
  
-   INSERT または UPDATE ステートメントで NULL を明示的に記述、または INSERT ステートメントからの列にすることで、null 値を列に挿入できます。  
  
-   Null 値は、主キーなど、またはディストリビューション キーなどの行の配信に使用される情報のテーブル内の別の行から、テーブル内の 1 つの行を区別するために必要な情報として使用できません。  
  
 データに NULL 値がある場合、論理演算子と比較演算子は、TRUE や FALSE ではなく UNKNOWN を返すことがあります。 このように 3 つの値を生成する論理は、アプリケーション エラーの原因になります。 次の表は、NULL 比較を採用した場合の結果を示しています。  
  
 次の表では、1 つのオペランドが NULL を返します 2 つのブール型オペランドに AND 演算子を適用した結果を示します。  
  
|第 1 オペランド|第 2 オペランド|結果|  
|---------------|---------------|------------|  
|TRUE|NULL|FALSE|  
|NULL|NULL|FALSE|  
|FALSE|NULL|FALSE|  
  
 次の表では、1 つのオペランドが NULL を返すの 2 つのブール型オペランドに OR 演算子を適用する結果を示します。  
  
|第 1 オペランド|第 2 オペランド|結果|  
|---------------|---------------|------------|  
|TRUE|NULL|TRUE|  
|NULL|NULL|UNKNOWN|  
|FALSE|NULL|UNKNOWN|  
  
## <a name="see-also"></a>参照  
 [および &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/and-transact-sql.md)   
 [または &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/or-transact-sql.md)   
 [いない &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/not-transact-sql.md)   
 [NULL と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/is-null-transact-sql.md)  
  
  

