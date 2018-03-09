---
title: "DataReader 変換先のカスタム プロパティ | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f151c3e8-3811-457d-a3d3-6158ca65a646
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e7f29a5c88b4cb4e8d090336a8d59072a25cfeb8
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="datareader-destination-custom-properties"></a>DataReader 変換先のカスタム プロパティ
  DataReader 変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、DataReader 変換先のカスタム プロパティを示しています。 **DataReader** を除き、すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ名|データ型|Description|  
|-------------------|---------------|-----------------|  
|DataReader|String|DataReader 変換先のクラス名。|  
|FailOnTimeout|ブール値|**ReadTimeout** が発生したときに失敗するかどうかを示します。 このプロパティの既定値は **False**です。|  
|ReadTimeout|Integer|タイムアウトが発生するまでの時間 (ミリ秒単位)。 このプロパティの既定値は 30000 (30 秒) です。|  
  
 DataReader 変換先の入力および入力列には、カスタム プロパティはありません。  
  
 詳細については、「 [DataReader 変換先](../../integration-services/data-flow/datareader-destination.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [Common Properties](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
