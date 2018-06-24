---
title: データ マイニング モデル トレーニング変換先のカスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f0a70216-fdac-44ae-af29-35f65626217c
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 17b2b721a5c90009fabca15864b62e71e0677251
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075547"
---
# <a name="data-mining-model-training-destination-custom-properties"></a>データ マイニング モデル トレーニング変換先のカスタム プロパティ
  データ マイニング モデル トレーニング変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、データ マイニング モデル トレーニング変換先のカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ|データ型|説明|  
|--------------|---------------|-----------------|  
|ASConnectionId|String|接続マネージャーの一意識別子。|  
|ASConnectionString|String|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトへの接続文字列。|  
|ObjectRef|String|この変換が使用するデータ マイニング構造を指定する XML タグ。|  
  
 データ マイニング モデル トレーニング変換先の入力および入力列には、カスタム プロパティはありません。  
  
 詳細については、「 [データ マイニング モデル トレーニング変換先](data-mining-model-training-destination.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Common Properties](../common-properties.md)  
  
  