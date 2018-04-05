---
title: DMSCHEMA_MINING_MODEL_CONTENT 行セット |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DMSCHEMA_MINING_MODEL_CONTENT
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DMSCHEMA_MINING_MODEL_CONTENT rowset
ms.assetid: 1e85d9e7-3b74-42ac-b94e-f52f76d8a25d
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 23410bac137e67e81e6e7b302f81c5cfd5db8b71
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="dmschemaminingmodelcontent-rowset"></a>DMSCHEMA_MINING_MODEL_CONTENT 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]により、クライアント アプリケーションは、データ マイニング モデルのコンテンツを参照します。 クライアント アプリケーションは、このトピックの最後に説明する特殊なツリー操作制限を使用して、マイニング モデルのコンテンツに移動できます。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DMSCHEMA_MINING_MODEL_CONTENT**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**||カタログ名。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]モデルがメンバーであるデータベースの名前を持つこの列に設定します。|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**||修飾されていないスキーマ名。 は、この列はサポートされていない[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 常に含まれている**VT_**です。|  
|**MODEL_NAME**|**DBTYPE_WSTR**||この行に記述されているコンテンツが関連付けられているモデルの名前。|  
|**ATTRIBUTE_NAME**|**DBTYPE_WSTR**||このノードに対応する属性の名前です。|  
|**NODE_NAME**|**DBTYPE_WSTR**||ノードの名前。 現在、この列と同じ値を含む**NODE_UNIQUE_NAME**可能性があります将来のリリース変更、します。|  
|**NODE_UNIQUE_NAME**|**DBTYPE_WSTR**||ノードの一意の名前。|  
|**NODE_TYPE**|**DBTYPE_I4**||ノードの型。 次のいずれかの値を生成します (サード パーティのデータ マイニング アルゴリズムを使用するとこの一覧を拡張できます)。<br /><br /> **DM_NODE_TYPE_CLASSIFICATION_TREE_ROOT** (**2**)<br /><br /> **DM_NODE_TYPE_TREE_INTERIOR** (**3**)<br /><br /> **DM_NODE_TYPE_TREE_DISTRIBUTION** (**4**)<br /><br /> **DM_NODE_TYPE_CLUSTER** (**5**)<br /><br /> **DM_NODE_TYPE_UNKNOWN** (**6**)<br /><br /> **DM_NODE_TYPE_ITEMSET** (**7**)<br /><br /> **DM_NODE_TYPE_ASSOCIATION_RULE** (**8**)<br /><br /> **DM_NODE_TYPE_NB_PREDICTABLE_ATTRIBUTE** (**9**)<br /><br /> **DM_NODE_TYPE_NB_INPUT_ATTRIBUTE** (**10**)<br /><br /> **DM_NODE_TYPE_NB_INPUT_ATTRIBUTE_STATE** (**11**)<br /><br /> **DM_NODE_TYPE_SEQUENCE** (**13**)<br /><br /> **DM_NODE_TYPE_TRANSITION** (**14**)<br /><br /> **DM_NODE_TYPE_TIME_SERIES** (**15**)<br /><br /> **DM_NODE_TYPE_TS_TREE** (**16**)<br /><br /> **DM_NODE_TYPE_NN_SUBNETWORK** (**17**) ニューラル ネットワーク、サブネットワーク<br /><br /> **DM_NODE_TYPE_NN_INPUT_LAYER** (**18**) ニューラル ネットワーク、入力層 (入力ノードの親)<br /><br /> **DM_NODE_TYPE_NN_HIDDEN_LAYER** (**19**) ニューラル ネットワーク、非表示層 (非表示のノードの親)<br /><br /> **DM_NODE_TYPE_NN_OUTPUT_LAYER** (**20**) ニューラル ネットワーク、出力層 (出力ノードの親)<br /><br /> **DM_NODE_TYPE_NN_INPUT_NODE** (**21**) ニューラル ネットワーク、入力ノード<br /><br /> **DM_NODE_TYPE_NN_HIDDEN_NODE** (**22**) ニューラル ネットワーク、非表示ノード<br /><br /> **DM_NODE_TYPE_NN_OUTPUT_NODE** (**23**) ニューラル ネットワーク、出力ノード<br /><br /> **DM_NODE_TYPE_NN_MARGINAL_STAT_NODE** (**24**) ニューラル ネットワーク、マージナル統計ノード<br /><br /> **DM_NODE_TYPE_REGRESSION_TREE_ROOT** (**25**)<br /><br /> **DM_NODE_TYPE_NB_MARGINAL_STAT_NODE** (**26**) ニューラル ネットワーク、マージナル統計ノード|  
|**NODE_GUID**|**DBTYPE_GUID 型**||ノードの GUID です。 は、この列はサポートされていない[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 常に含まれている**NULL**です。|  
|**NODE_CAPTION**|**DBTYPE_WSTR**||ノードに関連付けられたラベルまたはキャプション。 このプロパティは、主に表示を目的としています。|  
|**CHILDREN_CARDINALITY**|**DBTYPE_UI4**||ノードの子の推定数。|  
|**PARENT_UNIQUE_NAME**|**DBTYPE_WSTR**||ノードの親の一意な名前です。 **NULL**のルート レベルのすべてのノードが返されます。|  
|**NODE_DESCRIPTION**|**DBTYPE_WSTR**||ノードについてのわかりやすい説明。|  
|**NODE_RULE**|**DBTYPE_WSTR**||ノードに埋め込まれたルールの XML による記述。|  
|**MARGINAL_RULE**|**DBTYPE_WSTR**||親ノードからこのノードに移動するルールの XML による記述。|  
|**NODE_PROBABILITY**|**DBTYPE_R8**||このノードに関連付けられている確率。|  
|**MARGINAL_PROBABILITY**|**DBTYPE_R8**||親ノードからノードに到達する確率です。|  
|**NODE_DISTRIBUTION**|**DBTYPE_HCHAPTER**||ノードの確率ヒストグラムが含まれているテーブル。|  
|**NODE_SUPPORT**|**DBTYPE_R8**||このノードをサポートするケースの数。|  
|**MSOLAP_MODEL_COLUMN**|**DBTYPE_WSTR**||このノードが関連するモデル定義の列の名前。|  
|**MSOLAP_NODE_SCORE**|**DBTYPE_R8**||このノードに対して計算されたスコア。|  
|**MSOLAP_NODE_SHORT_CAPTION**|**DBTYPE_WSTR**||表示を読みやすくするために使用できるノードの短いキャプション。|  
  
## <a name="restriction-columns"></a>制限の列  
 **DMSCHEMA_MINING_MODEL_CONTENT**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**|省略可。|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|省略可。|  
|**MODEL_NAME**|**DBTYPE_WSTR**|省略可。|  
|**ATTRIBUTE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**NODE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**NODE_UNIQUE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**NODE_TYPE**|**DBTYPE_I4**|省略可。|  
|**NODE_GUID**|**DBTYPE_WSTR**|省略可。|  
|**NODE_CAPTION**|**DBTYPE_WSTR**|省略可。|  
|**TREE_OPERATION**|**DBTYPE_UI4**|省略可。 下の詳しい説明を参照してください。|  
  
 制限、 **TREE_OPERATION**の特定の列には、 **DMSCHEMA_MINING_MODEL_CONTENT**行セットです。 代わりに、ツリー演算子を指定します。 コンシューマーが指定できます、 **NODE_UNIQUE_NAME**制限とツリー演算子 (**先祖**、**子**、**兄弟**、 **親**、**子孫**、 **SELF**) を要求されたメンバーのセットを取得します。 **SELF**演算子には、返される行の一覧で、ノード自体の行が含まれています。 次の表に、定数のビットマップ定義を構成する、 **TREE_OPERATION**制限します。 論理を使用して結合できます**または**演算子。  
  
|定数|値|  
|--------------|-----------|  
|**DMTREEOP_ANCESTORS**|**0x00000020**|  
|**DMTREEOP_CHILDREN**|**0x00000001**|  
|**DMTREEOP_SIBLINGS**|**0x00000002**|  
|**DMTREEOP_PARENT**|**0x00000004**|  
|**DMTREEOP_SELF**|**0x00000008**|  
|**DMTREEOP_DESCENDANTS**|**0x00000010**|  
  
## <a name="see-also"></a>参照  
 [データ マイニング スキーマ行セット](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
