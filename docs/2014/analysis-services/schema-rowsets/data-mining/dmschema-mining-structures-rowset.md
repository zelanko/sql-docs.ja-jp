---
title: DMSCHEMA_MINING_STRUCTURES 行セット |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DMSCHEMA_MINING_STRUCTURES
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_STRUCTURES rowset
ms.assetid: 6224556b-08a0-496e-bd7c-632c3e833e26
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ab600b39e4a8347e470153cf21510554605d1c71
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37323072"
---
# <a name="dmschemaminingstructures-rowset"></a>DMSCHEMA_MINING_STRUCTURES 行セット
  現在のカタログ内のマイニング構造に関する情報を列挙します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `DMSCHEMA_MINING_STRUCTURES`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`STRUCTURE_CATALOG`|`DBTYPE_WSTR`||カタログ名。|  
|`STRUCTURE_SCHEMA`|`DBTYPE_WSTR`||修飾されていないスキーマ名。 プロバイダーでスキーマがサポートされていない場合は、`NULL` になります。|  
|`STRUCTURE_NAME`|`DBTYPE_WSTR`||構造名。 この列に `NULL` を含めることはできません。|  
|`STRUCTURE_GUID`|`DBTYPE_GUID`||構造を一意に識別する GUID。 プロバイダーでサポートされていない場合は、`NULL` になります。|  
|`DESCRIPTION`|`DBTYPE_WSTR`||構造の簡潔な説明。 構造に関連付けられた説明が存在しない場合は、`NULL` になります。|  
|`STRUCTURE_PROPID`|`DBTYPE_UI4`||構造のプロパティ ID。 プロバイダーでサポートされていない場合は、`NULL` になります。|  
|`DATE_CREATED`|`DBTYPE_DBTIMESTAMP`||構造の作成日。 プロバイダーから情報が得られない場合は、`NULL` になります。|  
|`DATE_MODIFIED`|`DBTYPE_DBTIMESTAMP`||構造の最終変更日。 プロバイダーから情報が得られない場合は、`NULL` になります。|  
|`CREATION_STATEMENT`|`DBTYPE_WSTR`||(省略可) 元のデータ マイニング モデルの作成に使用されたステートメント。|  
|`IS_POPULATED`|`DBTYPE_BOOL`||構造にデータが設定されているかどうかを示すブール値。<br /><br /> 構造にデータが設定されている場合は `VARIANT_TRUE`、それ以外の場合は `VARIANT_FALSE` になります。|  
|`LAST_PROCESSED`|`DBTYPE_DBTIMESTAMP`||構造の最終処理日。 プロバイダーから情報が得られない場合は、`NULL` になります。|  
|`HOLDOUT_MAXPERCENT`|`DBTYPE_ UI1`||テスト セットとして提示される入力ケースの最大割合を示すユーザー指定の値。<br /><br /> 0 または `NULL` は制限がないことを示します。|  
|`HOLDOUT_MAXCASES`|`DBTYPE_UI8`||テスト セットとして提示される入力ケースの最大数を示すユーザー指定の値。<br /><br /> 0 または `NULL` は制限がないことを示します。|  
|`HOLDOUT_SEED`|`DBTYPE_UI8`||反復可能なパーティション分割用のシードとして使用されるユーザー指定の値。<br /><br /> 0 は、マイニング構造 ID のハッシュがシードとして使用されることを示します。|  
|`HOLDOUT_ACTUAL_SIZE`|`DBTYPE_UI8`||マイニング構造が処理されている場合、この値はテスト データ セットの実際のサイズをケース数で示します。<br /><br /> `NULL` は、マイニング構造が処理されていないことを示します。|  
  
 行セットは、`STRUCTURE_CATALOG`、`STRUCTURE_SCHEMA`、`STRUCTURE_NAME` を基準に並べ替えることができます。  
  
## <a name="restriction-columns"></a>制限の列  
 `DMSCHEMA_MINING_STRUCTURES`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`STRUCTURE_CATALOG`|`DBTYPE_WSTR`|任意。|  
|`STRUCTURE_SCHEMA`|`DBTYPE_WSTR`|任意。|  
|`STRUCTURE_NAME`|`DBTYPE_WSTR`|任意。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング スキーマ行セット](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
