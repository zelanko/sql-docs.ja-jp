---
title: "Write (データベース エンジン) |Microsoft ドキュメント"
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Write_TSQL
- Write
dev_langs:
- TSQL
helpviewer_keywords:
- Write [Database Engine]
ms.assetid: 7c554334-d2d9-4eae-a4ae-097aa4020e1a
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 60707b57671c2ad607bd85b0fedececccd478038
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="write-database-engine"></a>Write (データベース エンジン)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

書き込みのバイナリ表現を書き込みます**SqlHierarchyId**に渡された**BinaryWriter**です。 使用して書き込みを呼び出すことができません[!INCLUDE[tsql](../../includes/tsql-md.md)]です。 代わりに、CAST または CONVERT を使用してください。
  
## <a name="syntax"></a>構文  
  
```sql
void Write( BinaryWriter w )   
```  
  
## <a name="arguments"></a>引数  
*w*  
A **BinaryWriter**オブジェクトをこのバイナリ表現**hierarchyid**ノードが書き出されます。
  
## <a name="return-types"></a>戻り値の型  
**CLR 型: void の戻り値**
  
## <a name="remarks"></a>解説  
書き込みが内部で使用される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]である場合など、必要なからデータを読み込むときに、 **hierarchyid**列です。 間で変換が行われるときに、書き込みは内部的に呼び出されますも**hierarchyid**と**varbinary**です。
  
## <a name="examples"></a>使用例  
  
```sql
MemoryStream stream = new MemoryStream();  
BinaryWriter bw = new BinaryWriter(stream);  
hid.Write(bw);  
byte[] encoding = stream.ToArray();  
  
```  
  
## <a name="see-also"></a>参照
[読み取り (&) #40";"データベース エンジン"&"#41;](../../t-sql/data-types/read-database-engine.md)  
[ToString (&) #40";"データベース エンジン"&"#41;](../../t-sql/data-types/tostring-database-engine.md)  
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[hierarchyid データ型メソッド リファレンス](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  

