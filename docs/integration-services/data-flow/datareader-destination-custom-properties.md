---
description: DataReader 変換先のカスタム プロパティ
title: DataReader 変換先のカスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f151c3e8-3811-457d-a3d3-6158ca65a646
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8efd821c41f7a0eaa9a19633c7719795eaa12665
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88430874"
---
# <a name="datareader-destination-custom-properties"></a>DataReader 変換先のカスタム プロパティ

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  DataReader 変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、DataReader 変換先のカスタム プロパティを示しています。 **DataReader** を除き、すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ名|データ型|説明|  
|-------------------|---------------|-----------------|  
|DataReader|String|DataReader 変換先のクラス名。|  
|FailOnTimeout|ブール型|**ReadTimeout** が発生したときに失敗するかどうかを示します。 このプロパティの既定値は **False**です。|  
|ReadTimeout|Integer|タイムアウトが発生するまでの時間 (ミリ秒単位)。 このプロパティの既定値は 30000 (30 秒) です。|  
  
 DataReader 変換先の入力および入力列には、カスタム プロパティはありません。  
  
 詳細については、「 [DataReader 変換先](../../integration-services/data-flow/datareader-destination.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [Common Properties](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
