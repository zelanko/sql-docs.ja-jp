---
title: "sp_estimated_rowsize_reduction_for_vardecimal (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_estimated_rowsize_reduction_for_vardecimal
- sp_estimated_rowsize_reduction_for_vardecimal_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_estimated_rowsize_reduction_for_vardecimal
- decimal data type, compressing
- numeric data type, compressing
- estimate decimal compression
- table compression [SQL Server]
ms.assetid: 0fe45983-f9f2-4c7f-938a-0fd96e1cbe8d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bd67eb412ba93dd19a828963f2f10d0589d1987c
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spestimatedrowsizereductionforvardecimal-transact-sql"></a>sp_estimated_rowsize_reduction_for_vardecimal (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  テーブルで vardecimal ストレージ形式が有効になっている場合に、行の平均サイズの削減量を見積もります。 この数値を使用して、テーブル サイズ全体の削減量を見積もることができます。 行サイズの平均削減量を計算するには、統計サンプリングが使用されます。このため、結果はあくまでも見積もりとして扱ってください。 vardecimal ストレージ形式を有効にした後、まれに行サイズが増加する場合があります。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代わりに、行の圧縮とページの圧縮を使用してください。 詳細については、「 [Data Compression](../../relational-databases/data-compression/data-compression.md)」を参照してください。 テーブルとパーティション インデックスのサイズに圧縮効果を参照してください。 [sp_estimate_data_compression_savings &#40;です。TRANSACT-SQL と #41 です;](../../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md)。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_estimated_rowsize_reduction_for_vardecimal [ [ @table_name = ] 'table'] [;]  
```  
  
## <a name="arguments"></a>引数  
 [  **@table=** ] **'***テーブル***'**  
 ストレージ形式を変更するテーブルの、3 つの要素で構成された名前を指定します。 *テーブル*は**nvarchar (776)**です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 現在のテーブル サイズと見積もりテーブル サイズの情報に関する、以下の結果セットが返されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**avg_rowlen_fixed_format**|**decimal (12, 2)**|固定 decimal ストレージ形式での行の長さ。|  
|**avg_rowlen_vardecimal_format**|**decimal (12, 2)**|vardecimal ストレージ形式を使用した場合の平均行サイズ。|  
|**row_count**|**int**|テーブル内の行の数。|  
  
## <a name="remarks"></a>解説  
 使用して**sp_estimated_rowsize_reduction_for_vardecimal**見積もることは、テーブルで vardecimal ストレージ形式を有効にした場合にします。 たとえば、行の平均サイズを 40% 削減できれば、テーブル サイズを 40% 削減できる可能性があります。 ただし FILL FACTOR と行サイズによっては、テーブル領域を削減できない場合もあります。 たとえば、長さ 8,000 バイトの行があり、そのサイズを 40% を削減したとしても、データ ページに収まるのは 1 行のみであることに変わりはないので、領域は削減されません。  
  
 場合の結果**sp_estimated_rowsize_reduction_for_vardecimal**ことを示していること、テーブルが大きくなるつまり、多くの行の表で使用ほぼの有効桁数の decimal データ型と、小規模の追加vardecimal ストレージ形式に必要なオーバーヘッドは、vardecimal ストレージ形式による削減量を超えています。 めったにありませんが、このような場合は vardecimal ストレージ形式を使用しないでください。  
  
 テーブルが vardecimal ストレージ形式の有効な場合を使用して**sp_estimated_rowsize_reduction_for_vardecimal**を vardecimal ストレージ形式が無効になっている場合、行の平均サイズを推定します。  
  
## <a name="permissions"></a>Permissions  
 テーブルに対する CONTROL 権限が必要です。  
  
## <a name="examples"></a>使用例  
 場合、次の例が行サイズ削減量を見積もります、`Production.WorkOrderRouting`テーブルに、`AdventureWorks2012`データベースが圧縮されています。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_estimated_rowsize_reduction_for_vardecimal 'Production.WorkOrderRouting' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_db_vardecimal_storage_format &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql.md)   
 [sp_tableoption &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)  
  
  
