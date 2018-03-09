---
title: "INDEXPROPERTY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- INDEXPROPERTY
- INDEXPROPERTY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- INDEXPROPERTY function
- indexes [SQL Server], viewing
- indexes [SQL Server], properties
ms.assetid: 998d5788-4871-44a8-8125-0d9390868b84
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f7099b3e11259d59c18ff6c5d8f591beca70846f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="indexproperty-transact-sql"></a>INDEXPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  指定されたテーブル ID 番号、インデックス名または統計名、およびプロパティ名の指定されたインデックスまたは統計プロパティ値を返します。 XML インデックスに対して NULL を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
INDEXPROPERTY ( object_ID , index_or_statistics_name , property )   
```  
  
## <a name="arguments"></a>引数  
 *object_ID*  
 インデックス プロパティ情報の提供元となるテーブルまたはインデックス付きビューのオブジェクト ID 番号を含む式です。 *object_ID*は**int**です。  
  
 *index_or_statistics_name*  
 返されるプロパティ情報の基となるインデックスまたは統計の名前を含む式です。 *index_or_statistics_name*は**nvarchar (128)**です。  
  
 *プロパティ*  
 返されるデータベース プロパティの名前を含む式です。 *プロパティ*は**varchar (128)**、これらの値のいずれかを指定できます。  
  
> [!NOTE]  
>  明記しない限り、NULL が返されます*プロパティ*有効なプロパティ名ではない*object_ID*が有効なオブジェクト ID、 *object_ID*のサポートされていないオブジェクト型です指定したプロパティまたは呼び出し元には、オブジェクトのメタデータを表示するアクセス許可がありません。  
  
|プロパティ|Description|値|  
|--------------|-----------------|-----------|  
|**インデックスについて**|インデックスの深さです。|インデックス レベルの数です。<br /><br /> NULL = XML インデックスまたは無効な入力|  
|**IndexFillFactor**|インデックスが作成されたとき、または最後に再構築されたときに使用された FILL FACTOR 値です。|FILL FACTOR|  
|**IndexID**|指定のテーブルまたはインデックス付きビュー上のインデックスの ID です。|インデックス ID です。|  
|**IsAutoStatistics**|ALTER DATABASE の AUTO_CREATE_STATISTICS オプションによって生成された統計です。|1 = True<br /><br /> 0 = FALSE または XML インデックス|  
|**IsClustered**|インデックスはクラスター化されています。|1 = True<br /><br /> 0 = FALSE または XML インデックス|  
|**IsDisabled**|インデックスは無効です。|1 = True<br /><br /> 0 = False<br /><br /> NULL = 無効な入力|  
|**IsFulltextKey**|インデックスは、テーブルのフルテキストおよびセマンティック インデックス作成のキーです。|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 1 = True<br /><br /> 0 = FALSE または XML インデックス<br /><br /> NULL = 無効な入力|  
|**IsHypothetical**|インデックスは仮想的であり、データへのアクセス パスとして直接使用することはできません。 仮想インデックスは、列レベルの統計を保持し、データベース エンジン チューニング アドバイザーによって管理および使用されます。|1 = True<br /><br /> 0 = false または XML インデックス<br /><br /> NULL = 無効な入力|  
|**IsPadIndex**|インデックスは各内部ノード上で空けておく領域を指定します。|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 1 = True<br /><br /> 0 = FALSE または XML インデックス|  
|**IsPageLockDisallowed**|ALTER INDEX の ALLOW_PAGE_LOCKS オプションによって設定されたページ ロックの値です。|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 1 = ページ ロックの禁止<br /><br /> 0 = ページ ロックの許可<br /><br /> NULL = 無効な入力|  
|**IsRowLockDisallowed**|ALTER INDEX の ALLOW_ROW_LOCKS オプションによって設定された行ロックの値です。|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 1 = 行ロックの禁止<br /><br /> 0 = 行ロックの許可<br /><br /> NULL = 無効な入力|  
|**IsStatistics**|*index_or_statistics_name*は、CREATE STATISTICS ステートメントまたは ALTER DATABASE の AUTO_CREATE_STATISTICS オプションによって作成された統計。|1 = True<br /><br /> 0 = FALSE または XML インデックス|  
|**IsUnique**|インデックスは一意です。|1 = True<br /><br /> 0 = FALSE または XML インデックス|  
|**IsColumnstore**|インデックスは xVelocity メモリ最適化列ストア インデックスです。|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 1 = True<br /><br /> 0 = False|  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="exceptions"></a>例外  
 エラーが発生した場合、または呼び出し元にオブジェクトの表示権限がない場合は、NULL が返されます。  
  
 ユーザーが所有しているか、または権限を与えられている、セキュリティ保護可能なリソースのメタデータのみを表示できます。 つまり、オブジェクトに対する権限がユーザーに与えられていない場合、メタデータを生成する組み込み関数 (INDEXPROPERTY など) が NULL を返す可能性があります。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
 次の例の値を返します、 **IsClustered**、**インデックスについて**、および**IndexFillFactor**のプロパティ、 `PK_Employee_BusinessEntityID` のインデックス`Employee`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
SELECT   
    INDEXPROPERTY(OBJECT_ID('HumanResources.Employee'),  
        'PK_Employee_BusinessEntityID','IsClustered')AS [Is Clustered],  
    INDEXPROPERTY(OBJECT_ID('HumanResources.Employee'),  
        'PK_Employee_BusinessEntityID','IndexDepth') AS [Index Depth],  
    INDEXPROPERTY(OBJECT_ID('HumanResources.Employee'),  
        'PK_Employee_BusinessEntityID','IndexFillFactor') AS [Fill Factor];  
  
```  
  
 Here is the result set:  
  
```  
Is Clustered Index Depth Fill Factor   
------------ ----------- -----------   
1            2           0  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例は、上のインデックスのいずれかのプロパティを調べ、`FactResellerSales`テーブル。  
  
```  
-- Uses AdventureWorks  
  
SELECT   
INDEXPROPERTY(OBJECT_ID('dbo.FactResellerSales'),  
    'ClusteredIndex_6d10fa223e5e4c1fbba087e29e16a7a2','IsClustered') AS [Is Clustered],  
INDEXPROPERTY(OBJECT_ID('dbo.FactResellerSales'),  
    'ClusteredIndex_6d10fa223e5e4c1fbba087e29e16a7a2','IsColumnstore') AS [Is Columnstore Index],  
INDEXPROPERTY(OBJECT_ID('dbo.FactResellerSales'),  
    'ClusteredIndex_6d10fa223e5e4c1fbba087e29e16a7a2','IndexFillFactor') AS [Fill Factor];  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [統計情報](../../relational-databases/statistics/statistics.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)   
 [sys.stats_columns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-stats-columns-transact-sql.md)  
  
  

