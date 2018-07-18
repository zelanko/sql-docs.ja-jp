---
title: DataReader 変換先のカスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f151c3e8-3811-457d-a3d3-6158ca65a646
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 40eac0ed658d7a09c0f570fd157432c137101340
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35330976"
---
# <a name="datareader-destination-custom-properties"></a>DataReader 変換先のカスタム プロパティ
  DataReader 変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、DataReader 変換先のカスタム プロパティを示しています。 **DataReader** を除き、すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ名|データ型|[説明]|  
|-------------------|---------------|-----------------|  
|DataReader|String|DataReader 変換先のクラス名。|  
|FailOnTimeout|ブール値|**ReadTimeout** が発生したときに失敗するかどうかを示します。 このプロパティの既定値は **False**です。|  
|ReadTimeout|Integer|タイムアウトが発生するまでの時間 (ミリ秒単位)。 このプロパティの既定値は 30000 (30 秒) です。|  
  
 DataReader 変換先の入力および入力列には、カスタム プロパティはありません。  
  
 詳細については、「 [DataReader 変換先](../../integration-services/data-flow/datareader-destination.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [Common Properties](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
