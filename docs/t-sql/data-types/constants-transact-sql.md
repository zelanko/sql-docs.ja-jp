---
title: "定数 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- uniqueidentifier data type
- bit data type
- constants [SQL Server]
- scalar values
- money data type, constants
- binary [SQL Server], constants
- float data type
- Unicode [SQL Server], constants
- constants [Transact-SQL]
- integer constants
- decimal data type, constants
- character strings [SQL Server], constants
- positive values [SQL Server]
- formats [SQL Server], constants
- datetime data type [SQL Server]
- literals [SQL Server], constants
- real data type
- negative values
ms.assetid: 58ae3ff3-b1d5-41b2-9a2f-fc7ab8c83e0e
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d9b212354492b96ca69ebf29afbc39c8ed1de6e3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="constants-transact-sql"></a>定数 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

リテラル値またはスカラー値としても知られる定数は、特定のデータ値を表す記号です。 定数の形式は、その定数が表す値のデータ型に依存します。
  
## <a name="character-string-constants"></a>文字列定数
文字列定数では、英数字 (a ～ z、A ～ Z、および 0 ～ 9)、感嘆符 (!)、アット マーク (@)、および番号記号 (#) などの特殊文字を単一引用符で囲みます。 COLLATE 句で照合順序を指定しない限り、文字列定数には現在のデータベースの既定の照合順序が割り当てられます。 ユーザーが入力した文字列は、コンピューターのコード ページで評価され、必要に応じてデータベースの既定のコード ページに翻訳されます。
  
QUOTED_IDENTIFIER オプションが on には、接続の OFF が設定されているが場合、文字列囲むこともできます、二重引用符は、Microsoft で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client プロバイダーと ODBC ドライバーは自動的に SET QUOTED_IDENTIFIER ON を使用します。 単一引用符を使用することをお勧めします。
  
単一引用符で囲まれた文字列に単一引用符を埋め込む場合は、単一引用符を 2 つ続けて並べることで 1 つの単一引用符を表します。 文字列が二重引用符で囲まれている場合は該当しません。
  
次に文字列の例を示します。
  
```sql
'Cincinnati'  
'O''Brien'  
'Process X is 50% complete.'  
'The level for job_id: %d should be between %d and %d.'  
"O'Brien"  
```  
  
空文字列は、2 つの単一引用符の間に何も挿入しないで表します。 6.x 互換性モードでは、空文字列は 1 つのスペースと見なされます。
  
文字列定数では、拡張照合順序がサポートされています。
  
> [!NOTE]  
>  文字定数 8000 バイトは、入力よりも大きい**varchar (max)**データ。  
  
## <a name="unicode-strings"></a>Unicode 文字列
Unicode 文字列の形式は文字列と同様ですが、Unicode 文字列には前に識別子 N が付きます。N は、SQL-92 標準の National Language を表します。 プレフィックス N は常に大文字になります。 たとえば、'Michél' は、N 'Michél' は Unicode 定数、文字定数です。 Unicode 定数は Unicode データとして解釈され、コード ページを使用した評価は行われません。 Unicode 定数は照合順序を持ちます。 この照合順序では主に比較と大文字小文字の区別が制御されます。 COLLATE 句で照合順序を指定しない限り、Unicode 定数には現在のデータベースの既定の照合順序が割り当てられます。 文字データでは 1 文字を 1 バイトで格納するのに対し、Unicode データでは 1 文字を 2 バイトで格納します。 詳細については、「 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)」を参照してください。
  
Unicode 文字列定数では、拡張照合順序がサポートされています。
  
> [!NOTE]  
>  Unicode 定数に 8,000 バイトは、入力よりも大きい**nvarchar (max)**データ。  
  
## <a name="binary-constants"></a>binary 型定数
バイナリ定数は、プレフィックスをある`0x`と 16 進数の文字列です。 引用符では囲みません。
  
次に binary 型文字列の例を示します。
  
```sql
0xAE  
0x12Ef  
0x69048AEFDD010E  
0x  (empty binary string)  
```  
  
> [!NOTE]  
>  8000 バイトは、入力よりも大きいバイナリ定数**varbinary (max)**データ。  
  
## <a name="bit-constants"></a>bit 型定数
**ビット**定数 0 または 1 の値で表され、引用符で囲まれていません。 bit 型定数に 1 より大きい数値を使用すると、その値は 1 に変換されます。
  
## <a name="datetime-constants"></a>datetime 型定数
**datetime**定数は単一引用符で囲まれた、特定の形式の日付文字値を使用して表されます。
  
例を次に**datetime**定数。
  
```sql
'December 5, 1985'  
'5 December, 1985'  
'851205'  
'12/5/98'  
```  
  
Datetime の定数の例は次のとおりです。
  
```sql
'14:30:24'  
'04:24 PM'  
```  
  
## <a name="integer-constants"></a>整数定数
**整数**定数は小数点を含まない引用符で囲まれていない数値文字列で表されます。 **整数**定数は整数である必要があります。 小数点以下を含めることができません。
  
例を次に**整数**定数。
  
```sql
1894  
2  
```  
  
## <a name="decimal-constants"></a>10 進定数
**10 進**定数は小数点を含む引用符で囲まれていない数値文字列で表されます。
  
例を次に**decimal**定数。
  
```sql
1894.1204  
2.0  
```  
  
## <a name="float-and-real-constants"></a>float 型と real 定数
**float**と**実際**定数は科学的表記法を使用して表されます。
  
例を次に**float**または**実際**値。
  
```sql
101.5E5  
0.5E-2  
```  
  
## <a name="money-constants"></a>money 型定数
**money**定数はオプションで小数点および通貨記号をプレフィックスとして数値の文字列として表されます。 **money**引用符で囲みません。
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、金額を表す文字列の 3 桁ごとにコンマ (,) を挿入するなどのグループ化ルールを設定することはできません。
  
> [!NOTE]  
>  コンマは、指定した任意の場所無視**money**リテラルです。  
  
例を次に**money**定数。
  
```sql
$12  
$542023.14  
```  
  
## <a name="uniqueidentifier-constants"></a>uniqueidentifier 定数
**uniqueidentifier**定数は、GUID を表す文字列。 文字型または binary 型文字列の形式で指定できます。
  
次の例は、両方とも同じ GUID を指定しています。
  
```sql
'6F9619FF-8B86-D011-B42D-00C04FC964FF'  
0xff19966f868b11d0b42d00c04fc964ff  
```  
  
## <a name="specifying-negative-and-positive-numbers"></a>負または正の数値の指定  
数値が正または負の値であるかどうかを示す、適用、  **+** または **-** 数値定数に単項演算子です。 この方法で、符号付き数値を表す数式を作成できます。 数値定数を使用して正ときに、  **+** または **-** 単項演算子は適用されません。
  
署名**整数**式。  
  
```sql
+145345234
-2147483648
```
署名**decimal**式。  
  
```sql
+145345234.2234
-2147483648.10
```
  
署名**float**式。  
  
```sql
+123E-3
-12E5
```
  
署名**money**式。  
  
```sql
-$45.56
+$423456.99
```
  
## <a name="enhanced-collations"></a>拡張照合順序  
SQL Server では、拡張照合順序をサポートする文字列定数および Unicode 文字列定数がサポートされています。 詳細については、次を参照してください。、 [COLLATE & #40 です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)句。
  
## <a name="see-also"></a>参照
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[演算子 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)
  
  

