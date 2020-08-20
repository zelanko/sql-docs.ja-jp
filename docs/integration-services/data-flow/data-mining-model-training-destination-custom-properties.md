---
description: データ マイニング モデル トレーニング変換先のカスタム プロパティ
title: データ マイニング モデル トレーニング変換先のカスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f0a70216-fdac-44ae-af29-35f65626217c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6427b808d31c9b1938b093da2bdf14d59bec90cc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88457365"
---
# <a name="data-mining-model-training-destination-custom-properties"></a>データ マイニング モデル トレーニング変換先のカスタム プロパティ

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  データ マイニング モデル トレーニング変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、データ マイニング モデル トレーニング変換先のカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ|データ型|説明|  
|--------------|---------------|-----------------|  
|ASConnectionId|String|接続マネージャーの一意識別子。|  
|ASConnectionString|String|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトへの接続文字列。|  
|ObjectRef|String|この変換が使用するデータ マイニング構造を指定する XML タグ。|  
  
 データ マイニング モデル トレーニング変換先の入力および入力列には、カスタム プロパティはありません。  
  
 詳細については、「 [データ マイニング モデル トレーニング変換先](../../integration-services/data-flow/data-mining-model-training-destination.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [Common Properties](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
