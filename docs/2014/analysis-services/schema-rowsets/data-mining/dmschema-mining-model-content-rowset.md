---
title: DMSCHEMA_MINING_MODEL_CONTENT 行セット |Microsoft ドキュメント
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
- DMSCHEMA_MINING_MODEL_CONTENT
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_MODEL_CONTENT rowset
ms.assetid: 1e85d9e7-3b74-42ac-b94e-f52f76d8a25d
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b6eb96e8a4a277ee5b7e198fca3d96062bd6d486
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164672"
---
# <a name="dmschemaminingmodelcontent-rowset"></a>DMSCHEMA_MINING_MODEL_CONTENT 行セット
  クライアント アプリケーションでデータ マニング モデルのコンテンツを参照できるようにします。 クライアント アプリケーションは、このトピックの最後に説明する特殊なツリー操作制限を使用して、マイニング モデルのコンテンツに移動できます。  
  
## <a name="rowset-columns"></a>行セットの列  
 `DMSCHEMA_MINING_MODEL_CONTENT`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`||カタログ名。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] モデルがメンバーであるデータベースの名前を持つこの列を追加します。|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`||修飾されていないスキーマ名。 この列は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でサポートされていないため、常に `VT_NULL` が格納されます。|  
|`MODEL_NAME`|`DBTYPE_WSTR`||この行に記述されているコンテンツが関連付けられているモデルの名前。|  
|`ATTRIBUTE_NAME`|`DBTYPE_WSTR`||このノードに対応する属性の名前です。|  
|`NODE_NAME`|`DBTYPE_WSTR`||ノードの名前。 現在、この列には `NODE_UNIQUE_NAME` と同じ値が格納されていますが、将来のリリースで変更される可能性があります。|  
|`NODE_UNIQUE_NAME`|`DBTYPE_WSTR`||ノードの一意の名前。|  
|`NODE_TYPE`|`DBTYPE_I4`||ノードの型。 次のいずれかの値を生成します (サード パーティのデータ マイニング アルゴリズムを使用するとこの一覧を拡張できます)。<br /><br /> -   `DM_NODE_TYPE_CLASSIFICATION_TREE_ROOT` (`2`)<br />-   `DM_NODE_TYPE_TREE_INTERIOR` (`3`)<br />-   `DM_NODE_TYPE_TREE_DISTRIBUTION` (`4`)<br />-   `DM_NODE_TYPE_CLUSTER` (`5`)<br />-   `DM_NODE_TYPE_UNKNOWN` (`6`)<br />-   `DM_NODE_TYPE_ITEMSET` (`7`)<br />-   `DM_NODE_TYPE_ASSOCIATION_RULE` (`8`)<br />-   `DM_NODE_TYPE_NB_PREDICTABLE_ATTRIBUTE` (`9`)<br />-   `DM_NODE_TYPE_NB_INPUT_ATTRIBUTE` (`10`)<br />-   `DM_NODE_TYPE_NB_INPUT_ATTRIBUTE_STATE` (`11`)<br />-   `DM_NODE_TYPE_SEQUENCE` (`13`)<br />-   `DM_NODE_TYPE_TRANSITION` (`14`)<br />-   `DM_NODE_TYPE_TIME_SERIES` (`15`)<br />-   `DM_NODE_TYPE_TS_TREE` (`16`)<br />-   `DM_NODE_TYPE_NN_SUBNETWORK` (`17`) ニューラル ネットワーク、サブネットワーク<br />-   `DM_NODE_TYPE_NN_INPUT_LAYER` (`18`) ニューラル ネットワーク、入力層 (入力ノードの親)<br />-   **DM_NODE_TYPE_NN_HIDDEN_LAYER** (`19`) ニューラル ネットワーク、非表示層 (非表示のノードの親)<br />-   `DM_NODE_TYPE_NN_OUTPUT_LAYER` (`20`) ニューラル ネットワーク、出力層 (出力ノードの親)<br />-   `DM_NODE_TYPE_NN_INPUT_NODE` (`21`) ニューラル ネットワーク、入力ノード<br />-   `DM_NODE_TYPE_NN_HIDDEN_NODE` (`22`) ニューラル ネットワーク、非表示ノード<br />-   `DM_NODE_TYPE_NN_OUTPUT_NODE` (`23`) ニューラル ネットワーク、出力ノード<br />-   `DM_NODE_TYPE_NN_MARGINAL_STAT_NODE` (`24`) ニューラル ネットワーク、マージナル統計ノード<br />-   **DM_NODE_TYPE_REGRESSION_TREE_ROOT** (`25`)<br />-   `DM_NODE_TYPE_NB_MARGINAL_STAT_NODE` (`26`) ニューラル ネットワーク、マージナル統計ノード|  
|`NODE_GUID`|`DBTYPE_GUID`||ノードの GUID です。 この列は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でサポートされていないため、常に `NULL` が格納されます。|  
|`NODE_CAPTION`|`DBTYPE_WSTR`||ノードに関連付けられたラベルまたはキャプション。 このプロパティは、主に表示を目的としています。|  
|`CHILDREN_CARDINALITY`|`DBTYPE_UI4`||ノードの子の推定数。|  
|`PARENT_UNIQUE_NAME`|`DBTYPE_WSTR`||ノードの親の一意な名前です。 ルート レベルのノードに対しては `NULL` を返します。|  
|`NODE_DESCRIPTION`|`DBTYPE_WSTR`||ノードについてのわかりやすい説明。|  
|`NODE_RULE`|`DBTYPE_WSTR`||ノードに埋め込まれたルールの XML による記述。|  
|`MARGINAL_RULE`|`DBTYPE_WSTR`||親ノードからこのノードに移動するルールの XML による記述。|  
|`NODE_PROBABILITY`|`DBTYPE_R8`||このノードに関連付けられている確率。|  
|`MARGINAL_PROBABILITY`|`DBTYPE_R8`||親ノードからノードに到達する確率です。|  
|`NODE_DISTRIBUTION`|`DBTYPE_HCHAPTER`||ノードの確率ヒストグラムが含まれているテーブル。|  
|`NODE_SUPPORT`|`DBTYPE_R8`||このノードをサポートするケースの数。|  
|`MSOLAP_MODEL_COLUMN`|`DBTYPE_WSTR`||このノードが関連するモデル定義の列の名前。|  
|`MSOLAP_NODE_SCORE`|`DBTYPE_R8`||このノードに対して計算されたスコア。|  
|`MSOLAP_NODE_SHORT_CAPTION`|`DBTYPE_WSTR`||表示を読みやすくするために使用できるノードの短いキャプション。|  
  
## <a name="restriction-columns"></a>制限の列  
 `DMSCHEMA_MINING_MODEL_CONTENT`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`|任意。|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`|任意。|  
|`MODEL_NAME`|`DBTYPE_WSTR`|任意。|  
|`ATTRIBUTE_NAME`|`DBTYPE_WSTR`|任意。|  
|`NODE_NAME`|`DBTYPE_WSTR`|任意。|  
|`NODE_UNIQUE_NAME`|`DBTYPE_WSTR`|任意。|  
|`NODE_TYPE`|`DBTYPE_I4`|任意。|  
|`NODE_GUID`|`DBTYPE_WSTR`|任意。|  
|`NODE_CAPTION`|`DBTYPE_WSTR`|任意。|  
|`TREE_OPERATION`|`DBTYPE_UI4`|任意。 下の詳しい説明を参照してください。|  
  
 制限 `TREE_OPERATION` は、`DMSCHEMA_MINING_MODEL_CONTENT` 行セットの特定の列に対するものではなく、ツリー演算子を指定するものです。 コンシューマーは、`NODE_UNIQUE_NAME` 制限とツリー演算子 (`ANCESTORS`、`CHILDREN`、`SIBLINGS`、`PARENT`、`DESCENDANTS`、`SELF`) を指定することにより、要求されたメンバーのセットを取得できます。 `SELF` 演算子を使用すると、返される一連の行にノード自体の行が含まれます。 次の表では、`TREE_OPERATION` 制限のビットマップ定義を構成する定数について説明します。 これらは論理 `OR` 演算子を使用して組み合わせることができます。  
  
|定数|値|  
|--------------|-----------|  
|**DMTREEOP_ANCESTORS**|`0x00000020`|  
|**DMTREEOP_CHILDREN**|`0x00000001`|  
|**DMTREEOP_SIBLINGS**|`0x00000002`|  
|**DMTREEOP_PARENT**|`0x00000004`|  
|**DMTREEOP_SELF**|`0x00000008`|  
|**DMTREEOP_DESCENDANTS**|`0x00000010`|  
  
## <a name="see-also"></a>参照  
 [データ マイニング スキーマ行セット](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  