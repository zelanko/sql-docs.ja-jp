---
title: "DMSCHEMA_MINING_STRUCTURES 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DMSCHEMA_MINING_STRUCTURES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DMSCHEMA_MINING_STRUCTURES rowset
ms.assetid: 6224556b-08a0-496e-bd7c-632c3e833e26
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c648aeb0603661e249f205e43cfbb1d8c6dc125c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dmschemaminingstructures-rowset"></a>DMSCHEMA_MINING_STRUCTURES 行セット
  現在のカタログ内のマイニング構造に関する情報を列挙します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DMSCHEMA_MINING_STRUCTURES**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**STRUCTURE_CATALOG**|**DBTYPE_WSTR**||カタログ名。|  
|**STRUCTURE_SCHEMA**|**DBTYPE_WSTR**||修飾されていないスキーマ名。 **NULL**スキーマは、プロバイダーによってサポートされていない場合。|  
|**STRUCTURE_NAME**|**DBTYPE_WSTR**||構造名。 この列を含めることはできません**NULL**です。|  
|**STRUCTURE_GUID**|**DBTYPE_GUID 型**||構造を一意に識別する GUID。 **NULL**プロバイダーによってサポートされていない場合。|  
|**DESCRIPTION**|**DBTYPE_WSTR**||構造の簡潔な説明。 **NULL**構造に関連付けられた説明がない場合。|  
|**STRUCTURE_PROPID**|**DBTYPE_UI4**||構造のプロパティ ID。 **NULL**プロバイダーによってサポートされていない場合。|  
|**DATE_CREATED**|**DBTYPE_DBTIMESTAMP**||構造の作成日。 **NULL**プロバイダーから不明な場合です。|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**||構造の最終変更日。 **NULL**プロバイダーから不明な場合です。|  
|**CREATION_STATEMENT**|**DBTYPE_WSTR**||(省略可) 元のデータ マイニング モデルの作成に使用されたステートメント。|  
|**IS_POPULATED**|**DBTYPE_BOOL**||構造にデータが設定されているかどうかを示すブール値。<br /><br /> **VARIANT_TRUE**場合は、構造が格納されます。**VARIANT_FALSE**それ以外の場合。|  
|**LAST_PROCESSED**|**DBTYPE_DBTIMESTAMP**||構造の最終処理日。 **NULL**プロバイダーから不明な場合です。|  
|**HOLDOUT_MAXPERCENT**|**DBTYPE _ UI1**||テスト セットとして提示される入力ケースの最大割合を示すユーザー指定の値。<br /><br /> 0 または**NULL**制限がないことを示します。|  
|**HOLDOUT_MAXCASES**|**DBTYPE_UI8**||テスト セットとして提示される入力ケースの最大数を示すユーザー指定の値。<br /><br /> 0 または**NULL**制限がないことを示します。|  
|**HOLDOUT_SEED**|**DBTYPE_UI8**||反復可能なパーティション分割用のシードとして使用されるユーザー指定の値。<br /><br /> 0 は、マイニング構造 ID のハッシュがシードとして使用されることを示します。|  
|**HOLDOUT_ACTUAL_SIZE**|**DBTYPE_UI8**||マイニング構造が処理されている場合、この値はテスト データ セットの実際のサイズをケース数で示します。<br /><br /> **NULL**マイニング構造が処理されなかったことを示します。|  
  
 行セットが並べ替えられて**STRUCTURE_CATALOG**、 **STRUCTURE_SCHEMA**、 **STRUCTURE_NAME**です。  
  
## <a name="restriction-columns"></a>制限の列  
 **DMSCHEMA_MINING_STRUCTURES**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**STRUCTURE_CATALOG**|**DBTYPE_WSTR**|省略可。|  
|**STRUCTURE_SCHEMA**|**DBTYPE_WSTR**|省略可。|  
|**STRUCTURE_NAME**|**DBTYPE_WSTR**|省略可。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング スキーマ行セット](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  

