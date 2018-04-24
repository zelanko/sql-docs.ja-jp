---
title: CONCAT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CONCAT
- CONCAT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CONCAT function
ms.assetid: fce5a8d4-283b-4c47-95e5-4946402550d5
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 71f52ba08f2fd5fe94af4b16dbcac06746564e09
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="concat-transact-sql"></a>CONCAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

2 つ以上の文字列値を連結した結果の文字列を返します。 (連結時に区切り値を追加するには、「[CONCAT_WS](../../t-sql/functions/concat-ws-transact-sql.md)」をご覧ください。)
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
CONCAT ( string_value1, string_value2 [, string_valueN ] )  
```  
  
## <a name="arguments"></a>引数  
*string_value*  
他の値に連結する文字列値です。
  
## <a name="return-types"></a>戻り値の型
入力に依存する文字列、長さ、および型です。
  
## <a name="remarks"></a>Remarks  
**CONCAT** は、文字列引数の可変数を取得して、1 つの文字列に連結します。 最小で 2 つの入力値が必要です。それ以外の場合は、エラーが発生します。 すべての引数は、暗黙的に文字列型に変換され、連結されます。 Null 値は暗黙的に空の文字列に変換されます。 すべての引数が NULL の場合、**varchar(1)** 型の空の文字列が返されます。 文字列への暗黙の変換は、データ型変換の既存の規則に従います。 データ型変換についての詳細については、を参照してください。 [CAST および CONVERT & #40 です。TRANSACT-SQL と #41;](../../t-sql/functions/cast-and-convert-transact-sql.md).
  
戻り値の型は、引数の種類によって異なります。 次の表に、マッピングを示します。
  
|入力型|出力型と長さ|  
|---|---|
|引数が SQL CLR システム型、SQL CLR UDT、または `nvarchar(max)` の場合|**nvarchar(max)**|  
|それ以外の場合、引数が **varbinary (max)** または **varchar (max)** の場合|**varchar(max)**。ただし、いずれかのパラメーターが任意の長さの **nvarchar** である場合を除きます。 この場合、結果は **nvarchar (max)** です。|  
|それ以外の場合、引数が **nvarchar**(<= 4000) の場合|**nvarchar**(<= 4000)|  
|それ以外の他のすべての場合|**varchar**(<= 8000)。ただし、いずれかのパラメーターが任意の長さの nvarchar である場合を除きます。 この場合、結果は **nvarchar (max)** です。|  
  
引数が **nvarchar** では <= 4000 の場合、または **varchar** では <= 8000 の場合、暗黙的な変換は結果の長さに影響を与えます。 他のデータ型は、暗黙的に文字列に変換された場合は異なる長さになります。 たとえば、**int** (14) の文字列の長さは 12 ですが、**float** の長さは 32 です。 このように 2 つの整数を連結した結果としての長さは少なくとも 24 です。
  
入力引数がサポートされるラージ オブジェクト (LOB) の型ではない場合、戻り値の型に関係なく、戻り値の型は長さ 8000 に切り詰められます。 この切り捨てではスペースが保持され、効率的なプラン生成をサポートします。
  
バージョンでは、リンク サーバー上には CONCAT 関数をリモートで実行することができます [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降。 古いバージョンのリンク サーバー、CONCAT 操作が実行されるローカルで、非連結された値が、リンク サーバーから返された後です。
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-concat"></a>A. CONCAT を使用する  
  
```sql
SELECT CONCAT ( 'Happy ', 'Birthday ', 11, '/', '25' ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
-------------------------  
Happy Birthday 11/25  
  
(1 row(s) affected)  
```  
  
### <a name="b-using-concat-with-null-values"></a>B. NULL 値を持つ CONCAT を使用する  
  
```sql
CREATE TABLE #temp (  
    emp_name nvarchar(200) NOT NULL,  
    emp_middlename nvarchar(200) NULL,  
    emp_lastname nvarchar(200) NOT NULL  
);  
INSERT INTO #temp VALUES( 'Name', NULL, 'Lastname' );  
SELECT CONCAT( emp_name, emp_middlename, emp_lastname ) AS Result  
FROM #temp;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
------------------  
NameLastname  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)   
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40;Transact-SQL&#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40;Transact-SQL&#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF &#40;Transact-SQL&#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [TRANSLATE &#40;Transact-SQL&#41;](../../t-sql/functions/translate-transact-sql.md)  
 [文字列関数 &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  


