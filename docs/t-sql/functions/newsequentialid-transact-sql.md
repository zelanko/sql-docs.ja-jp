---
title: "NEWSEQUENTIALID (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/08/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 39bd8a393a9cc3e19e457cda98c0521492e07911
ms.contentlocale: ja-jp
ms.lasthandoff: 10/24/2017

---
# <a name="newsequentialid-transact-sql"></a>NEWSEQUENTIALID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Windows が起動されてから、指定されたコンピューターで、この関数によりこれまでに生成されたどの GUID よりも大きい GUID を生成します。 Windows の再起動後、GUID は、より小さい値の範囲から始まることもありますが、グローバルに一意のままです。 GUID 列を行識別子 (ROWID) として使用する場合は、NEWSEQUENTIALID を使用すると、NEWID 関数を使用するよりも処理が高速になることがあります。 これは、NEWID 関数では、ランダムなアクティビティが発生し、使用されるキャッシュ データ ページが少なくなるためです。 また、NEWSEQUENTIALID を使用すると、データ ページとインデックス ページを完全に埋めることができます。  
  
> [!IMPORTANT]  
>  プライバシーを重視する場合は、この関数は使用しないでください。 次に生成される GUID の値が予測されるため、その GUID に関連するデータへのアクセスが発生する可能性があります。  
  
 NEWSEQUENTIALID は、windows のラッパーを[UuidCreateSequential](http://go.microsoft.com/fwlink/?LinkId=164027)でいくつかの関数[バイトをシャッフル適用](https://blogs.msdn.microsoft.com/dbrowne/2012/07/03/how-to-generate-sequential-guids-for-sql-server-in-net/)です。
  
> [!WARNING]  
>  UuidCreateSequential の関数には、ハードウェアの依存関係があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、連続した値のクラスターがデータベース (包含データベース) などがその他のコンピューターに移動したときに開発できます。 Always On を使用する場合とで[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]、連続した値のクラスターが、データベースが別のコンピューターにフェールオーバーした場合に開発できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
NEWSEQUENTIALID ( )  
```  
  
## <a name="return-type"></a>戻り値の型  
 **uniqueidentifier**  
  
## <a name="remarks"></a>解説  
 NEWSEQUENTIALID() は、型のテーブル列の既定の制約でのみ使用できます**uniqueidentifier**です。 例:  
  
```  
CREATE TABLE myTable (ColumnA uniqueidentifier DEFAULT NEWSEQUENTIALID());   
```  
  
 NEWSEQUENTIALID() を DEFAULT 式で使用する場合、他のスカラー演算子と組み合わせることはできません。 たとえば、次を実行することはできません。  
  
```  
CREATE TABLE myTable (ColumnA uniqueidentifier DEFAULT dbo.myfunction(NEWSEQUENTIALID()));  
```  
  
 前の例では、 `myfunction()` 、スカラー ユーザー定義スカラー値関数を受け入れて返す、`uniqueidentifier`値。  
  
 クエリで NEWSEQUENTIALID を参照することはできません。  
  
 NEWSEQUENTIALID を使って GUID を生成し、インデックスのリーフ レベルでページの分割とランダム IO を減らすことができます。  
  
 NEWSEQUENTIALID を使用して生成された各 GUID は、そのコンピューター上で一意です。 NEWSEQUENTIALID を使用することによって生成された GUID は、ソース コンピューターにネットワーク カードがある場合にのみ、複数のコンピューター間で一意になります。  
  
## <a name="see-also"></a>参照  
 [NEWID & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/newid-transact-sql.md)   
 [比較演算子 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/comparison-operators-transact-sql.md)  
  
  

