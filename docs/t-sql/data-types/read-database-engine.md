---
title: Read (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 7/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a26aeb048a81d0ea7c9ff7104370302698cdfe74
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37422101"
---
# <a name="read-database-engine"></a>Read (データベース エンジン)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

読み取り のバイナリ表現を読み込む **SqlHierarchyId** から渡されるで **BinaryReader** し、設定、 **SqlHierarchyId** オブジェクトをその値にします。 読み取り [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して呼び出すことができない です。 代わりに、CAST または CONVERT を使用してください。
  
## <a name="syntax"></a>構文  
  
```sql
void Read( BinaryReader r )   
```  
  
## <a name="arguments"></a>引数  
*r*  
 **hierarchyid** ノードのバイナリ表現に対応するバイナリ ストリームを生成する **BinaryReader** オブジェクト。  
  
## <a name="return-types"></a>戻り値の型
 **CLR の戻り値の型: void**  
  
## <a name="remarks"></a>Remarks  
 読み取り は、入力は検証されません。 無効なバイナリの入力を指定した場合 読み取り で例外が発生します。 または、成功し、生成、無効な場合があります、 **SqlHierarchyId** オブジェクト メソッドを持つ予期しない結果が得られますか、例外が発生します。  
  
 **読み取り はのみ呼び出すことで、新しく作成された SqlHierarchyId** オブジェクトです。  
  
 読み取り [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]内部で使用される 必要な場合、ようにデータを書き込む場合 **hierarchyid** 列です。 読み取り 間で変換が行われるときに内部的に呼び出されますも **varbinary** と **hierarchyid**です。  
  
## <a name="examples"></a>使用例  
  
```sql
Byte[] encoding = new byte[] { 0x58 };  
MemoryStream stream = new MemoryStream(encoding, false /*not writable*/);  
BinaryReader br = new BinaryReader(stream);  
SqlHierarchyId hid = new SqlHierarchyId();  
hid.Read(br);   
```  
  
## <a name="see-also"></a>参照  
[書き込み (&) #40";"データベース エンジン"&"#41 です。](../../t-sql/data-types/write-database-engine.md)  
[ToString (&) #40";"データベース エンジン"&"#41 です。](../../t-sql/data-types/tostring-database-engine.md)  
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[hierarchyid データ型メソッド リファレンス](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  
