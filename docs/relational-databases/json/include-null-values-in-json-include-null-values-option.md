---
title: "JSON に Null 値を含める - INCLUDE_NULL_VALUES オプション | Microsoft Docs"
ms.custom: SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: INCLUDE_NULL_VALUES (FOR JSON)
ms.assetid: 06873768-3778-4ed8-a1db-61758726bda0
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6a44f712ecec89a1a5aae2f19f505c7a924b120d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="include-null-values-in-json---includenullvalues-option"></a>JSON に Null 値を含める - INCLUDE_NULL_VALUES オプション
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  **FOR JSON** 句の JSON の出力に null 値を含めるには、 **INCLUDE_NULL_VALUES** オプションを指定します。  
  
 **INCLUDE_NULL_VALUES** オプションを指定しない場合、クエリ結果で値が null のプロパティは JSON の出力に含まれません。  
  
## <a name="examples"></a>使用例  
 **INCLUDE_NULL_VALUES** オプションを指定した場合と指定しなかった場合の **FOR JSON** 句の出力例を以下に示します。  
  
|**INCLUDE_NULL_VALUES** オプションを指定しなかった場合|**INCLUDE_NULL_VALUES** オプションを指定した場合|  
|--------------------------------------------------|-----------------------------------------------|  
|`{    "name": "John",    "surname": "Doe" }`|`{    "name": "John",    "surname": "Doe",    "age": null,    "phone": null }`|  
  
 次に、 **FOR JSON** 句で **INCLUDE_NULL_VALUES** オプションを指定した別の例を示します。  
  
 **Query**  
  
```sql  
SELECT name, surname  
FROM emp  
FOR JSON AUTO, INCLUDE_NULL_VALUES    
```  
  
 **結果**  
  
```json  
[{
    "name": "John",
    "surname": null
}, {
    "name": "Jane",
    "surname": "Doe"
}] 
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>SQL Server に組み込まれている JSON サポートの詳細情報  
多くの具体的なソリューション、ユース ケース、推奨事項については、Microsoft のプログラム マネージャー Jovan Popovic による SQL Server および Azure SQL Database に[組み込まれている JSON のサポートに関するブログ投稿](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)をご覧ください。  

## <a name="see-also"></a>参照  
 [FOR 句 &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
  
  
