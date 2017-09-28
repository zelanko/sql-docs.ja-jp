---
title: "CONCAT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2573d9f42b48205dab712ca401a1ac61ae4a17e2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="concat-transact-sql"></a>CONCAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

2 つ以上の文字列値を連結した結果の文字列を返します。 (連結中に分ける値を追加するを参照してください[CONCAT_WS](../../t-sql/functions/concat-ws-transact-sql.md)。)。
  
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
  
## <a name="remarks"></a>解説  
**CONCAT**可変個の文字列引数を受け取り、1 つの文字列に連結します。 最小で 2 つの入力値が必要です。それ以外の場合は、エラーが発生します。 すべての引数は、暗黙的に文字列型に変換され、連結されます。 Null 値は暗黙的に空の文字列に変換されます。 すべての引数が null、空の文字列型の場合**varchar**(1) が返されます。 文字列への暗黙の変換は、データ型変換の既存の規則に従います。 データ型変換の詳細については、次を参照してください。 [CAST および CONVERT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/cast-and-convert-transact-sql.md).
  
戻り値の型は、引数の種類によって異なります。 次の表に、マッピングを示します。
  
|入力型|出力型と長さ|  
|---|---|
|引数が SQL CLR システム型、SQL CLR UDT、または `nvarchar(max)` の場合|**nvarchar(max)**|  
|それ以外の場合、いずれかの引数は**varbinary (max)**または**varchar (max)**|**varchar (max)**パラメーターのいずれかがない限り、 **nvarchar**任意の長さ。 そのため、結果は場合**nvarchar (max)**です。|  
|それ以外の場合、いずれかの引数は**nvarchar**(< = 4000)|**nvarchar**(< = 4000)|  
|それ以外の他のすべての場合|**varchar**(< = 8000) パラメーターのいずれかの任意の長さの nvarchar でない限り、します。 そのため、結果は場合**nvarchar (max)**です。|  
  
引数が < = 4000 の**nvarchar**、または < = 8000 の**varchar**、暗黙的な変換が、結果の長さを与えることができます。 他のデータ型は、暗黙的に文字列に変換された場合は異なる長さになります。 たとえば、 **int** (14) が、文字列の長さは 12 中、 **float**がの長さは 32 です。 このように 2 つの整数を連結した結果としての長さは少なくとも 24 です。
  
入力引数がサポートされるラージ オブジェクト (LOB) の型ではない場合、戻り値の型に関係なく、戻り値の型は長さ 8000 に切り詰められます。 この切り捨てではスペースが保持され、効率的なプラン生成をサポートします。
  
CONCAT 関数は、バージョンでは、リンク サーバーでリモートで実行することができます[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降。 古いバージョンのリンク サーバー、CONCAT 操作が実行されるローカルで、非連結された値が、リンク サーバーから返された後です。
  
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
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-concat"></a>C. CONCAT を使用する  
  
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
## <a name="see-also"></a>参照
[文字列関数 (TRANSACT-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  
[CONCAT_WS (TRANSACT-SQL)](../../t-sql/functions/concat-ws-transact-sql.md)   
  



