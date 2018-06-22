---
title: DMSCHEMA_MINING_SERVICES 行セット |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DMSCHEMA_MINING_SERVICES
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_SERVICES rowset
ms.assetid: 4a672f2f-d637-4def-a572-c18556f83d34
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b268abe234c8df71672ca434494ee89717a15947
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070818"
---
# <a name="dmschemaminingservices-rowset"></a>DMSCHEMA_MINING_SERVICES 行セット
  プロバイダーでサポートされている各データ マイニング アルゴリズムについて記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `DMSCHEMA_MINING_SERVICES`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`||アルゴリズムの名前。 この列はプロバイダー固有のものです。|  
|`SERVICE_TYPE_ID`|`DBTYPE_UI4`||この列には、マイニング サービスについて記述したビットマップが含まれています。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] この列に、次の値のいずれかを設定します。<br /><br /> -   `DM_SERVICETYPE_CLASSIFICATION` (`1`)<br />-   `DM_SERVICETYPE_CLUSTERING` (`2`)|  
|`SERVICE_DISPLAY_NAME`|`DBTYPE_WSTR`||ローカライズ可能なアルゴリズムの表示名。|  
|`SERVICE_GUID`|`DBTYPE_GUID`||アルゴリズムの GUID。|  
|`DESCRIPTION`|`DBTYPE_WSTR`||アルゴリズムについてのわかりやすい説明。|  
|`PREDICTION_LIMIT`|`DBTYPE_UI4`||モデルおよびアルゴリズムが提供可能な予測の最大数。|  
|`SUPPORTED_DISTRIBUTION_FLAGS`|`DBTYPE_WSTR`||アルゴリズムによってサポートされている統計分布について記述したフラグのコンマ区切りの一覧。 この列には、次の値が 1 つ以上含まれています。<br /><br /> -   "`NORMAL`"<br />-   "`LOG NORMAL`"<br />-   "`UNIFORM`"|  
|`SUPPORTED_INPUT_CONTENT_TYPES`|`DBTYPE_WSTR`||アルゴリズムによってサポートされている入力コンテンツの種類について記述したフラグのコンマ区切りの一覧。 この列には、次の値が 1 つ以上含まれています。<br /><br /> -   "`KEY`"<br />-   "`DISCRETE`"<br />-   "`CONTINUOUS`"<br />-   "`DISCRETIZED`"<br />-   "`ORDERED`"<br />-"キー `SEQUENCE`"<br />-   "`CYCLICAL`"<br />-   "`PROBABILITY`"<br />-   "`VARIANCE`"<br />-   "`STDEV`"<br />-   "`SUPPORT`"<br />-   "`PROBABILITY VARIANCE`"<br />-   "`PROBABILITY STDEV`"<br />-   "`KEY TIME`"|  
|`SUPPORTED_PREDICTION_CONTENT_TYPES`|`DBTYPE_WSTR`||アルゴリズムによってサポートされている予測コンテンツの種類について記述したフラグのコンマ区切りの一覧。 この列には、次の値が 1 つ以上含まれています。<br /><br /> -   "`KEY`"<br />-   "`DISCRETE`"<br />-   "`CONTINUOUS`"<br />-   "`DISCRETIZED`"<br />-   "`ORDERED`"<br />-"キー `SEQUENCE` "<br />-   "`CYCLICAL`"<br />-   "`PROBABILITY`"<br />-   "`VARIANCE`"<br />-   "`STDEV`"<br />-   "`SUPPORT`"<br />-   "`PROBABILITY VARIANCE`"<br />-   "`PROBABILITY STDEV`"<br />-「キー時刻」|  
|`SUPPORTED_MODELING_FLAGS`|`DBTYPE_WSTR`||アルゴリズムによってサポートされているモデリング フラグのコンマ区切りの一覧。 この列には、次の値が 1 つ以上含まれています。<br /><br /> -   "`MODEL_EXISTENCE_ONLY`"<br />-   "`REGRESSOR`"<br /><br /> プロバイダー固有のフラグを定義することもできます。|  
|`SUPPORTED_SOURCE_QUERY`|`DBTYPE_WSTR`||-この列は、旧バージョンとの互換性のためサポートされています。|  
|`TRAINING_COMPLEXITY`|`DBTYPE_I4`||トレーニングに要する予想時間。<br /><br /> -   `DM_TRAINING_COMPLEXITY_LOW` 実行時間が比較的短く、入力に比例してであることを示します。<br />-   **DM_TRAINING_COMPLEXITY_MEDIUM**実行時間が長い、可能性がありますが、一般に、入力に比例してであることを示します。<br />-   **DM_TRAINING_COMPLEXITY_HIGH**実行時間が長いと、トレーニング ケースの数に関係の指数関数的になる可能性ことを示します。|  
|`PREDICTION_COMPLEXITY`|`DBTYPE_I4`||予測に要する予想時間。<br /><br /> -   **DM_PREDICTION_COMPLEXITY_LOW**ことを示し、実行時間が比較的短く、入力に比例します。<br />-   **DM_PREDICTION_COMPLEXITY_MEDIUM**実行時間が長い、可能性がありますが、一般に、入力に比例してであることを示します。<br />-   **DM_PREDICTION_COMPLEXITY_HIGH**実行時間が長いと、トレーニング ケースの数に関係の指数関数的になる可能性ことを示します。|  
|`EXPECTED_QUALITY`|`DBTYPE_I4`||このアルゴリズムで生成されるモデルに予想される品質。<br /><br /> -   `DM_EXPECTED_QUALITY_LOW`<br />-   `DM_EXPECTED_QUALITY_MEDIUM`<br />-   **DM_EXPECTED_QUALITY_HIGH**|  
|`SCALING`|`DBTYPE_I4`||アルゴリズムのスケーラビリティ。<br /><br /> -   **DM_SCALING_LOW**<br />-   `DM_SCALING_MEDIUM`<br />-   **DM_SCALING_HIGH**|  
|`ALLOW_INCREMENTAL_INSERT`|`DBTYPE_BOOL`||アルゴリズムが増分トレーニング (パターンを完全に再検出するのではなく、新しい事実データに基づいて検出済みパターンを更新する) をサポートしているかどうかを示すブール値。|  
|`ALLOW_PMML_INITIALIZATION`|`DBTYPE_BOOL`||PMML 2.1 文字列に基づいてマイニング モデルを作成できるかどうかを示すブール値。<br /><br /> `TRUE` の場合、マイニング アルゴリズムは PMML 2.1 コンテンツからの初期化をサポートします。|  
|`CONTROL`|`DBTYPE_I4`||トレーニングが中断された場合にサービスによって提供されるサポート。<br /><br /> -   `DM_CONTROL_NONE` モデルのトレーニング開始後に、アルゴリズムを取り消すことはできないことを示します。<br />-   `DM_CONTROL_CANCEL` モデルのトレーニング開始がトレーニングを再開するを再起動する必要がありますが、アルゴリズムをキャンセルできることを示します。<br />-   `DM_CONTROL_SUSPENDRESUME` 結果は、トレーニングが完了するまでは使用できませんが、アルゴリズムを取り消すし、いつでも再開を示します。<br />-   `DM_CONTROL_SUSPENDWITHRESULT` インクリメンタル結果を取得できることと、アルゴリズムを取り消すし、いつでも再開を示します。|  
|`ALLOW_DUPLICATE_KEY`|`DBTYPE_BOOL`||ケースに重複キーを含めることができるかどうかを示すブール値。<br /><br /> `VARIANT_TRUE` の場合、ケースには重複キーを含めることができます。|  
|`VIEWER_TYPE`|`DBTYPE_WSTR`||このモデルに推奨されるビューアー。|  
|`HELP_FILE`|`DBTYPE_WSTR`||(省略可) このサービスのマニュアルが含まれているファイルの名前。|  
|`HELP_CONTEXT`|`DBTYPE_I4`||(省略可) このサービスのヘルプ コンテキスト ID。|  
|`MSOLAP_SUPPORTS_ANALYSIS_SERVICES_DDL`|`DBTYPE_WSTR`||サポートされている DDL のバージョン。 0 は DDL がサポートされていないことを示します。|  
|`MSOLAP_SUPPORTS_OLAP_MINING_MODELS`|`DBTYPE_BOOL`||OLAP マイニング モデルを作成できるかどうかを示すブール値。<br /><br /> `TRUE` の場合は、OLAP マイニング モデルを作成できます。 `MSOLAP_SUPPORTS_ANALYSIS_SERVICES_DDL` をゼロ以外にする必要があります。|  
|`MSOLAP_SUPPORTS_DATA_MINING_DIMENSIONS`|`DBTYPE_BOOL`||データ マイニング ディメンションを作成できるかどうかを示すブール値。<br /><br /> `TRUE` の場合は、データ マイニング ディメンションを作成できます。|  
|`MSOLAP_SUPPORTS_DRILLTHROUGH`|`DBTYPE_BOOL`||サービスでドリルスルー機能がサポートされるかどうかを示すブール値。<br /><br /> `TRUE` の場合は、サービスでドリルスルー機能がサポートされています。|  
  
## <a name="restriction-columns"></a>制限の列  
 `DMSCHEMA_MINING_SERVICES`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`|任意。|  
|`SERVICE_TYPE_ID`|`DBTYPE_UI4`|任意。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング スキーマ行セット](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  