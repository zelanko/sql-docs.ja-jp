---
title: DataReader 変換先のカスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f151c3e8-3811-457d-a3d3-6158ca65a646
author: janinezhang
ms.author: janinez
ms.openlocfilehash: e5691ad8c769621bc9f16e4447d0926d69e02b96
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84915967"
---
# <a name="datareader-destination-custom-properties"></a>DataReader 変換先のカスタム プロパティ
  DataReader 変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、DataReader 変換先のカスタム プロパティを示しています。 `DataReader` を除き、すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ名|データ型|説明|  
|-------------------|---------------|-----------------|  
|DataReader|String|DataReader 変換先のクラス名。|  
|FailOnTimeout|Boolean|`ReadTimeout` が発生したときに失敗するかどうかを示します。 このプロパティの既定値は **False**です。|  
|ReadTimeout|整数|タイムアウトが発生するまでの時間 (ミリ秒単位)。 このプロパティの既定値は 30000 (30 秒) です。|  
  
 DataReader 変換先の入力および入力列には、カスタム プロパティはありません。  
  
 詳細については、「 [DataReader 変換先](datareader-destination.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [Common Properties](../common-properties.md)  
  
  
