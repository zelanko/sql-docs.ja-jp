---
title: "TuningOptions 要素 (DTA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- TuningOptions element
ms.assetid: 58a22ba1-8e03-411f-bd46-85e4540f217a
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c8fcdfd21cdbc923bc92e06aca42c7495f5d35e9
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="tuningoptions-element-dta"></a>TuningOptions 要素 (DTA)
  特定のチューニング セッションのチューニング オプションが含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|省略可。 使用する場合は、 **DTAInput** 要素につき 1 回使用できます。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[DTAInput 要素 &#40;DTA&#41;](../../tools/dta/dtainput-element-dta.md)|  
|**子要素**|**ReportSet** 要素。 詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](http://go.microsoft.com/fwlink/?linkid=43100)を参照してください。<br /><br /> **TuningLogTable** 要素。 詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](http://go.microsoft.com/fwlink/?linkid=43100)を参照してください。<br /><br /> **NumberOfEvents** 要素。 詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](http://go.microsoft.com/fwlink/?linkid=43100)を参照してください。<br /><br /> [TuningTimeInMin 要素 &#40;DTA&#41;](../../tools/dta/tuningtimeinmin-element-dta.md)<br /><br /> [StorageBoundInMB 要素 &#40;DTA&#41;](../../tools/dta/storageboundinmb-element-dta.md)<br /><br /> **MaxKeyColumnsInIndex** 要素。 詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](http://go.microsoft.com/fwlink/?linkid=43100)を参照してください。<br /><br /> **MaxColumnsInIndex** 要素。 詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](http://go.microsoft.com/fwlink/?linkid=43100)を参照してください。<br /><br /> **MinPercentageImprovement** 要素。 詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](http://go.microsoft.com/fwlink/?linkid=43100)を参照してください。<br /><br /> [TestServer 要素 &#40;DTA&#41;](../../tools/dta/testserver-element-dta.md)<br /><br /> [FeatureSet 要素 &#40;DTA&#41;](../../tools/dta/featureset-element-dta.md)<br /><br /> [Partitioning 要素 &#40;DTA&#41;](../../tools/dta/partitioning-element-dta.md)<br /><br /> [DropOnlyMode 要素 &#40;DTA&#41;](../../tools/dta/droponlymode-element-dta.md)<br /><br /> [KeepExisting 要素 &#40;DTA&#41;](../../tools/dta/keepexisting-element-dta.md)<br /><br /> [OnlineIndexOperation 要素 &#40;DTA&#41;](../../tools/dta/onlineindexoperation-element-dta.md)<br /><br /> [DatabaseToConnect 要素 &#40;DTA&#41;](../../tools/dta/databasetoconnect-element-dta.md)<br /><br /> **IgnoreConstantsInWorkload** 要素。 詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](http://go.microsoft.com/fwlink/?linkid=43100)を参照してください。<br /><br /> **RetainShellDB** 要素。 詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](http://go.microsoft.com/fwlink/?linkid=43100)を参照してください。|  
  
## <a name="example"></a>例  
 **TuningOptions** 要素の例については、「[XML 入力ファイルのサンプル &#40;DTA&#41;](../../tools/dta/xml-input-file-samples-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  

