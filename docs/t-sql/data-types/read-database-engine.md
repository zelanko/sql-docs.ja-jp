---
title: "読み取り (データベース エンジン) |Microsoft ドキュメント"
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
- Read_TSQL
- Read
dev_langs:
- TSQL
helpviewer_keywords:
- Read [Database Engine]
ms.assetid: f2b8207c-b69f-4327-a874-100b3a1f27d8
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 21f27c627a36f747d9e3ecbb52d14d1ac6bc5d28
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="read-database-engine"></a>Read (データベース エンジン)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

読み取りのバイナリ表現の読み取り**SqlHierarchyId**から渡された**BinaryReader**設定と、 **SqlHierarchyId**オブジェクトをその値にします。 使用して読み取りを呼び出すことができません[!INCLUDE[tsql](../../includes/tsql-md.md)]です。 代わりに、CAST または CONVERT を使用してください。
  
## <a name="syntax"></a>構文  
  
```sql
void Read( BinaryReader r )   
```  
  
## <a name="arguments"></a>引数  
*r*  
 **BinaryReader**のバイナリ表現に対応するバイナリ ストリームを生成するオブジェクト、 **hierarchyid**ノード。  
  
## <a name="return-types"></a>戻り値の型
 **CLR 型: void の戻り値**  
  
## <a name="remarks"></a>解説  
 読み取りでは、入力は検証されません。 無効な binary 入力を指定すると、読み取りで例外が発生する可能性があります。 または、成功し、生成、無効な可能性があります**SqlHierarchyId**オブジェクト メソッドを持つ予期しない結果が得られますか、例外が発生します。  
  
 読み取りのみ呼び出し可能で、新しく作成**SqlHierarchyId**オブジェクト。  
  
 読み取りが内部で使用される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]である場合など、必要なデータを書き込む場合**hierarchyid**列です。 間で変換が行われるときに、読み取りは内部的に呼び出されますも**varbinary**と**hierarchyid**です。  
  
## <a name="examples"></a>使用例  
  
```sql
Byte[] encoding = new byte[] { 0x58 };  
MemoryStream stream = new MemoryStream(encoding, false /*not writable*/);  
BinaryReader br = new BinaryReader(stream);  
SqlHierarchyId hid = new SqlHierarchyId();  
hid.Read(br);   
```  
  
## <a name="see-also"></a>参照  
[書き込み (&) #40";"データベース エンジン"&"#41;](../../t-sql/data-types/write-database-engine.md)  
[ToString (&) #40";"データベース エンジン"&"#41;](../../t-sql/data-types/tostring-database-engine.md)  
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[hierarchyid データ型メソッド リファレンス](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  

