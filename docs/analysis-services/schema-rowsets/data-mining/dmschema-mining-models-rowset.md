---
title: "DMSCHEMA_MINING_MODELS 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DMSCHEMA_MINING_MODELS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DMSCHEMA_MINING_MODELS rowset
ms.assetid: 1636f4cf-b342-4e2e-93b4-04136e2d41ef
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 838f17f1e9725738686635b3000f28929084c122
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="dmschemaminingmodels-rowset"></a>DMSCHEMA_MINING_MODELS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]現在のカタログ内のデータ マイニング モデルを列挙します。 **DMSCHEMA_MINING_MODELS**行セットには、モデル名、処理日、および各マイニング モデルに関連付けられたマイニング アルゴリズムなどの情報が含まれています。  
  
 のインスタンスにアクセスするたびに SQL Server ログインを指定する必要はありません。 **DMSCHEMA_MINING_MODELS**スキーマ行セットはよく似ています、 [DBSCHEMA_TABLES](../../../analysis-services/schema-rowsets/ole-db/dbschema-tables-rowset.md)スキーマ行セットと同じ方法で使用することができます。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DMSCHEMA_MINING_MODELS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|Description|  
|-----------------|--------------------|-----------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**|カタログ名。 モデルがメンバーとして含まれているデータベースの名前を使用して設定されます。|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|修飾されていないスキーマ名。 は、この列はサポートされていない[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 常に含まれている**NULL**です。|  
|**MODEL_NAME**|**DBTYPE_WSTR**|マイニング モデル名。 この列には、マイニング モデルの名前が格納され、空になることはありません。|  
|**MODEL_TYPE**|**DBTYPE_WSTR**|モデルの種類。|  
|**MODEL_GUID**|**DBTYPE_GUID 型**|モデルの GUID。|  
|**DESCRIPTION**|**DBTYPE_WSTR**|モデルについてのわかりやすい説明。|  
|**MODEL_PROPID**|**DBTYPE_UI4**|モデルのプロパティ ID。 は、この列はサポートされていない[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 常に含まれている**NULL**です。|  
|**DATE_CREATED**|**DBTYPE_DBTIMESTAMP**|モデルの作成日。|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**|モデル定義の最終変更日。|  
|**SERVICE_TYPE_ID**|**DBTYPE_UI4**|モデルによって使用されるデータ マイニング アルゴリズムの種類を識別する列挙。 この種類は、次のいずれかの値になります。<br /><br /> **DM_SERVICETYPE_CLASSIFICATION** (1)<br /><br /> **DM_SERVICETYPE_SEGMENTATION**(2)<br /><br /> **DM_SERVICETYPE_ アソシエーション**(4)<br /><br /> **DM_SERVICETYPE_ DENSITY_ESTIMATE**(8)<br /><br /> **DM_SERVICETYPE_SEQUENCE**(16)。|  
|**SERVICE_NAME**|**DBTYPE_WSTR**|モデルによって使用されるデータ マイニング アルゴリズムのプロバイダー固有の名前。|  
|**CREATION_STATEMENT**|**DBTYPE_WSTR**|マイニング モデルの作成に使用されたステートメント。|  
|**PREDICTION_ENTITY**|**DBTYPE_WSTR**|予測可能なマイニング列を示すコンマ区切りの一覧。|  
|**IS_POPULATED**|**DBTYPE_BOOL**|モデルにデータが設定されているかどうかを示すブール型のフラグ。<br /><br /> **TRUE**モデルが設定されている、それ以外の場合**FALSE**です。|  
|**MINING_PARAMETERS**|**DBTYPE_WSTR**|モデルが作成されたときに使用されたパラメーターのコンマ区切りの一覧。|  
|**MINING_STRUCTURE**|**DBTYPE_WSTR**|モデルの基になるマイニング構造の ID。|  
|**LAST_PROCESSED**|**DBTYPE_DBTIMESTAMP**|モデルの最終処理日。|  
|**MSOLAP_IS_DRILLTHROUGH_ENABLED**|**DBTYPE_BOOL**|モデルでドリルスルーがサポートされるかどうかを示すブール型のフラグ。|  
|**フィルター**|**DBTYPE_WSTR**|マイニング モデルに関連付けられているフィルター式。<br /><br /> NULL または空の文字列は、フィルターが適用されていないことを示します。|  
|**TRAINING_SET_SIZE**|**DBTYPE_UIS**|マイニング モデル トレーニング構造が処理された後、およびすべてのフィルターがモデルに適用された後のセットに含まれているケースの数。|  
  
## <a name="restriction-columns"></a>制限の列  
 **DMSCHEMA_MINING_MODELS**行セットは、次の表の列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**|省略可。|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|省略可。|  
|**MODEL_NAME**|**DBTYPE_WSTR**|省略可。|  
|**MODEL_TYPE**|**DBTYPE_WSTR**|省略可。|  
|**SERVICE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**SERVICE_TYPE_ID**|**DBTYPE_UI4**|省略可。|  
|**MINING_STRUCTURE**|**DBTYPE_WSTR**|省略可。|  
  
 この行セットのクエリを実行する方法の例については、次を参照してください。[マイニング モデルの作成に使用されるパラメーターをクエリ](../../../analysis-services/data-mining/query-the-parameters-used-to-create-a-mining-model.md)です。  
  
## <a name="see-also"></a>参照  
 [データ マイニング スキーマ行セット](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
