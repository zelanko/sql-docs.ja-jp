---
title: NEWSEQUENTIALID (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/08/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NEWSEQUENTIALID
- NEWSEQUENTIALID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- NEWSEQUENTIALID function
- GUIDs [SQL Server]
ms.assetid: e06d2cab-f1ff-42f1-8550-6aaec57be36f
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6993a36f0c1c67ffcfbb9897bcd36354088c8c5c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="newsequentialid-transact-sql"></a>NEWSEQUENTIALID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Windows が起動されてから、指定されたコンピューターで、この関数によりこれまでに生成されたどの GUID よりも大きい GUID を生成します。 Windows の再起動後、GUID は、より小さい値の範囲から始まることもありますが、グローバルに一意のままです。 GUID 列を行識別子 (ROWID) として使用する場合は、NEWSEQUENTIALID を使用すると、NEWID 関数を使用するよりも処理が高速になることがあります。 これは、NEWID 関数では、ランダムなアクティビティが発生し、使用されるキャッシュ データ ページが少なくなるためです。 また、NEWSEQUENTIALID を使用すると、データ ページとインデックス ページを完全に埋めることができます。  
  
> [!IMPORTANT]  
>  プライバシーを重視する場合は、この関数は使用しないでください。 次に生成される GUID の値が予測されるため、その GUID に関連するデータへのアクセスが発生する可能性があります。  
  
 NEWSEQUENTIALID は、Windows の [UuidCreateSequential](http://go.microsoft.com/fwlink/?LinkId=164027) 関数のラッパーであり、何らかの[バイト シャッフルが適用されます](https://blogs.msdn.microsoft.com/dbrowne/2012/07/03/how-to-generate-sequential-guids-for-sql-server-in-net/)。
  
> [!WARNING]  
>  UuidCreateSequential の関数には、ハードウェアの依存関係があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 、データベース (包含データベースの場合) などは、他のコンピューターに移動すると、連続した値のクラスターを開発できます。 Always On を [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] で使用するとき、データベースの別のコンピューターへのフェールオーバーが失敗した場合、シーケンシャル値のクラスターが発生する可能性があります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
NEWSEQUENTIALID ( )  
```  
  
## <a name="return-type"></a>戻り値の型  
 **uniqueidentifier**  
  
## <a name="remarks"></a>Remarks  
 NEWSEQUENTIALID() は、型のテーブル列の既定の制約でのみ使用できます **uniqueidentifier**です。 例 :  
  
```  
CREATE TABLE myTable (ColumnA uniqueidentifier DEFAULT NEWSEQUENTIALID());   
```  
  
 NEWSEQUENTIALID() を DEFAULT 式で使用する場合、他のスカラー演算子と組み合わせることはできません。 たとえば、次を実行することはできません。  
  
```  
CREATE TABLE myTable (ColumnA uniqueidentifier DEFAULT dbo.myfunction(NEWSEQUENTIALID()));  
```  
  
 この例で、`myfunction()` は、`uniqueidentifier` 値を受け入れて返すユーザー定義スカラー関数です。  
  
 クエリで NEWSEQUENTIALID を参照することはできません。  
  
 NEWSEQUENTIALID を使って GUID を生成し、インデックスのリーフ レベルでページの分割とランダム IO を減らすことができます。  
  
 NEWSEQUENTIALID を使用して生成された各 GUID は、そのコンピューター上で一意です。 NEWSEQUENTIALID を使用することによって生成された GUID は、ソース コンピューターにネットワーク カードがある場合にのみ、複数のコンピューター間で一意になります。  
  
## <a name="see-also"></a>参照  
 [NEWID &#40;Transact-SQL&#41;](../../t-sql/functions/newid-transact-sql.md)   
 [比較演算子 (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/comparison-operators-transact-sql.md)  
  
  
