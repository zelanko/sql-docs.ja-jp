---
title: "money および smallmoney (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- money_TSQL
- money
- smallmoney
- smallmoney_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- money data type, about money data type
- money data type
- smallmoney data type
- values [SQL Server], monetary
- currency [SQL Server]
ms.assetid: 57861137-89ea-4b89-b361-390597d7bccc
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bd07ecd1cdacc686e0f831320fd5e939c0c174da
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="money-and-smallmoney-transact-sql"></a>money および smallmoney (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

金銭や通貨の値を表す金額データ型です。
  
## <a name="remarks"></a>解説  
  
|データ型|範囲|ストレージ|  
|---|---|---|
|**money**|-922,337,203,685,477.5808 に 922,337,203,685,477.5807 (-922,337,203,685,477.58<br />Informatica の 922,337,203,685,477.58 to。  Informatica のみをサポートしている小数点以下 2 桁、4 されません。)|8 バイト|  
|**smallmoney**|- 214,748.3648 ～ 214,748.3647|4 バイト|  
  
**Money**と**smallmoney**データ型を表している通貨単位の 10,000 の精度はします。 Informatica、用、 **money**と**smallmoney**データ型は、厳密には、それが表している通貨単位の 1 分です。
  
すべての通貨単位からセントなどの部分通貨単位を区切るには、ピリオドを使用します。 たとえば、2.15 は 2 ドル 15 セントを表します。
  
これらのデータ型は次の通貨記号を使用できます。
  
![通貨記号、16 進値のテーブル](../../t-sql/data-types/media/money01.gif "通貨記号、16 進値のテーブル")
  
通貨データまたは金額データは単一引用符 (') で囲む必要はありません。 通貨記号が前に付いた金額値を指定することはできますが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はその記号に関連付けられた通貨情報を格納せず、数値のみを格納することに注意してください。
  
## <a name="converting-money-data"></a>Money データを変換します。
変換する場合**money**整数データ型から単位を想定して、通貨単位にします。 たとえば、4 の整数値に変換、 **money** 4 通貨単位に相当します。
  
次の例では変換**smallmoney**と**money**値を**varchar**と**decimal**それぞれのデータ型します。
  
```sql
DECLARE @mymoney_sm smallmoney = 3148.29,  
        @mymoney    money = 3148.29;  
SELECT  CAST(@mymoney_sm AS varchar) AS 'SM_MONEY varchar',  
        CAST(@mymoney AS decimal)    AS 'MONEY DECIMAL';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
SM_MONEY VARCHAR               MONEY DECIMAL  
------------------------------ ----------------------  
3148.29                        3148    
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照
[ALTER TABLE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-table-transact-sql.md) 
 [CAST および CONVERT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/cast-and-convert-transact-sql.md) 
[テーブルを作成する & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-table-transact-sql.md) 
[データ型 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/data-types-transact-sql.md) 
 [DECLARE @local_variable & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/declare-local-variable-transact-sql.md) 
[設定@local_variable& #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/set-local-variable-transact-sql.md) 
 [sys.types & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)
  
  

