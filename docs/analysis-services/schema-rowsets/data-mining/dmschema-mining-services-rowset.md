---
title: DMSCHEMA_MINING_SERVICES 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0cf94fa4fb22e38ac52513d2dba52500df3bb9d5
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34033023"
---
# <a name="dmschemaminingservices-rowset"></a>DMSCHEMA_MINING_SERVICES 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  プロバイダーでサポートされている各データ マイニング アルゴリズムについて記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DMSCHEMA_MINING_SERVICES**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|Description|  
|-----------------|--------------------|-----------------|  
|**SERVICE_NAME**|**DBTYPE_WSTR**|アルゴリズムの名前。 この列はプロバイダー固有のものです。|  
|**SERVICE_TYPE_ID**|**DBTYPE_UI4**|この列には、マイニング サービスについて記述したビットマップが含まれています。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] この列に、次の値のいずれかを設定します。<br /><br /> **DM_SERVICETYPE_CLASSIFICATION** (**1**)<br /><br /> **DM_SERVICETYPE_CLUSTERING** (**2**)|  
|**SERVICE_DISPLAY_NAME**|**DBTYPE_WSTR**|ローカライズ可能なアルゴリズムの表示名。|  
|**SERVICE_GUID**|**DBTYPE_GUID 型**|アルゴリズムの GUID。|  
|**DESCRIPTION**|**DBTYPE_WSTR**|アルゴリズムについてのわかりやすい説明。|  
|**PREDICTION_LIMIT**|**DBTYPE_UI4**|モデルおよびアルゴリズムが提供可能な予測の最大数。|  
|**SUPPORTED_DISTRIBUTION_FLAGS**|**DBTYPE_WSTR**|アルゴリズムによってサポートされている統計分布について記述したフラグのコンマ区切りの一覧。 この列には、次の値が 1 つ以上含まれています。<br /><br /> "**標準**"<br /><br /> "**ログ標準**"<br /><br /> "**UNIFORM**"|  
|**SUPPORTED_INPUT_CONTENT_TYPES**|**DBTYPE_WSTR**|アルゴリズムによってサポートされている入力コンテンツの種類について記述したフラグのコンマ区切りの一覧。 この列には、次の値が 1 つ以上含まれています。<br /><br /> "**キー**"<br /><br /> "**DISCRETE**"<br /><br /> "**CONTINUOUS**"<br /><br /> "**DISCRETIZED**"<br /><br /> "**ORDERED**"<br /><br /> "キー**シーケンス**"<br /><br /> "**CYCLICAL**"<br /><br /> "**確率**"<br /><br /> "**差異**"<br /><br /> "**STDEV**"<br /><br /> "**サポート**"<br /><br /> "**確率分散**"<br /><br /> "**確率 STDEV**"<br /><br /> "**KEY TIME**"|  
|**SUPPORTED_PREDICTION_CONTENT_TYPES**|**DBTYPE_WSTR**|アルゴリズムによってサポートされている予測コンテンツの種類について記述したフラグのコンマ区切りの一覧。 この列には、次の値が 1 つ以上含まれています。<br /><br /> "**キー**"<br /><br /> "**DISCRETE**"<br /><br /> "**CONTINUOUS**"<br /><br /> "**DISCRETIZED**"<br /><br /> "**ORDERED**"<br /><br /> "キー**シーケンス**"<br /><br /> "**CYCLICAL**"<br /><br /> "**確率**"<br /><br /> "**差異**"<br /><br /> "**STDEV**"<br /><br /> "**サポート**"<br /><br /> "**確率分散**"<br /><br /> "**確率 STDEV**"<br /><br /> "KEY TIME"|  
|**SUPPORTED_MODELING_FLAGS**|**DBTYPE_WSTR**|アルゴリズムによってサポートされているモデリング フラグのコンマ区切りの一覧。 この列には、次の値が 1 つ以上含まれています。<br /><br /> "**MODEL_EXISTENCE_ONLY**"<br /><br /> "**リグレッサー**"<br /><br /> <br /><br /> プロバイダー固有のフラグが定義することもできることに注意してください。|  
|**SUPPORTED_SOURCE_QUERY**|**DBTYPE_WSTR**|この列は、旧バージョンとの互換性を維持するためにサポートされています。|  
|**TRAINING_COMPLEXITY**|**DBTYPE_I4**|トレーニングに要する予想時間。<br /><br /> **DM_TRAINING_COMPLEXITY_LOW**ことを示し、実行時間が比較的短く、入力に比例します。<br /><br /> **DM_TRAINING_COMPLEXITY_MEDIUM**実行時間が長い、可能性がありますが、一般に、入力に比例してであることを示します。<br /><br /> **DM_TRAINING_COMPLEXITY_HIGH**実行時間が長いと、トレーニング ケースの数に関係の指数関数的になる可能性ことを示します。|  
|**PREDICTION_COMPLEXITY**|**DBTYPE_I4**|予測に要する予想時間。<br /><br /> **DM_PREDICTION_COMPLEXITY_LOW**ことを示し、実行時間が比較的短く、入力に比例します。<br /><br /> **DM_PREDICTION_COMPLEXITY_MEDIUM**実行時間が長い、可能性がありますが、一般に、入力に比例してであることを示します。<br /><br /> **DM_PREDICTION_COMPLEXITY_HIGH**実行時間が長いと、トレーニング ケースの数に関係の指数関数的になる可能性ことを示します。|  
|**EXPECTED_QUALITY**|**DBTYPE_I4**|このアルゴリズムで生成されるモデルに予想される品質。<br /><br /> **DM_EXPECTED_QUALITY_LOW**<br /><br /> **DM_EXPECTED_QUALITY_MEDIUM**<br /><br /> **DM_EXPECTED_QUALITY_HIGH**|  
|**スケーリング**|**DBTYPE_I4**|アルゴリズムのスケーラビリティ。<br /><br /> **DM_SCALING_LOW**<br /><br /> **DM_SCALING_MEDIUM**<br /><br /> **DM_SCALING_HIGH**|  
|**ALLOW_INCREMENTAL_INSERT**|**DBTYPE_BOOL**|アルゴリズムが増分トレーニング (パターンを完全に再検出するのではなく、新しい事実データに基づいて検出済みパターンを更新する) をサポートしているかどうかを示すブール値。|  
|**ALLOW_PMML_INITIALIZATION**|**DBTYPE_BOOL**|PMML 2.1 文字列に基づいてマイニング モデルを作成できるかどうかを示すブール値。<br /><br /> 場合**TRUE**、マイニング アルゴリズムは PMML 2.1 コンテンツからの初期化をサポートします。|  
|**コントロール**|**DBTYPE_I4**|トレーニングが中断された場合にサービスによって提供されるサポート。<br /><br /> **DM_CONTROL_NONE**モデルのトレーニング開始後に、アルゴリズムを取り消すことはできませんを示します。<br /><br /> **DM_CONTROL_CANCEL**モデルのトレーニング開始がトレーニングを再開するを再起動する必要がありますが、アルゴリズムをキャンセルできることを示します。<br /><br /> **DM_CONTROL_SUSPENDRESUME**結果は、トレーニングが完了するまでは使用できませんが、アルゴリズムを取り消すし、いつでも再開ことを示します。<br /><br /> **DM_CONTROL_SUSPENDWITHRESULT**アルゴリズムを取り消すし、いつでも再開され、インクリメンタル結果を取得できることを示します。|  
|**ALLOW_DUPLICATE_KEY**|**DBTYPE_BOOL**|ケースに重複キーを含めることができるかどうかを示すブール値。<br /><br /> 場合**VARIANT_TRUE**、重複するキーを格納する場合は許可されています。|  
|**VIEWER_TYPE**|**DBTYPE_WSTR**|このモデルに推奨されるビューアー。|  
|**HELP_FILE**|**DBTYPE_WSTR**|(省略可) このサービスのマニュアルが含まれているファイルの名前。|  
|**HELP_CONTEXT**|**DBTYPE_I4**|(省略可) このサービスのヘルプ コンテキスト ID。|  
|**MSOLAP_SUPPORTS_ANALYSIS_SERVICES_DDL**|**DBTYPE_WSTR**|サポートされている DDL のバージョン。 0 は DDL がサポートされていないことを示します。|  
|**MSOLAP_SUPPORTS_OLAP_MINING_MODELS**|**DBTYPE_BOOL**|OLAP マイニング モデルを作成できるかどうかを示すブール値。<br /><br /> 場合**TRUE**、OLAP マイニング モデルを作成することができます。 必要があります**MSOLAP_SUPPORTS_ANALYSIS_SERVICES_DDL**を 0 以外にします。|  
|**MSOLAP_SUPPORTS_DATA_MINING_DIMENSIONS**|**DBTYPE_BOOL**|データ マイニング ディメンションを作成できるかどうかを示すブール値。<br /><br /> 場合**TRUE**、データ マイニング ディメンションを作成することができます。|  
|**MSOLAP_SUPPORTS_DRILLTHROUGH**|**DBTYPE_BOOL**|サービスでドリルスルー機能がサポートされるかどうかを示すブール値。<br /><br /> 場合**TRUE**サービスがドリルスルー機能をサポートします。|  
  
## <a name="restriction-columns"></a>制限の列  
 **DMSCHEMA_MINING_SERVICES**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**SERVICE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**SERVICE_TYPE_ID**|**DBTYPE_UI4**|省略可。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング スキーマ行セット](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
