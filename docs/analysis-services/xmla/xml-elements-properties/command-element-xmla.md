---
title: "コマンド要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Command Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.command
- Command
- urn:schemas-microsoft-com:xml-analysis#Command
- http://schemas.microsoft.com/analysisservices/2003/engine#Command
helpviewer_keywords: Command element
ms.assetid: 9abc14df-7cbe-46bc-ba0f-f0691c19afad
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 02e6829ab10ddb85bde8e36889a1f6cfe0760cb3
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="command-element-xmla"></a>Command 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]によって実行されるコマンドを含む、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Execute>  
   ...  
   <Command>  
      <Alter>...</Alter>  
      <!-- or -->  
      <Backup>...</Backup>  
      <!-- or -->  
      <Batch>...</Batch>  
      <!-- or -->  
      <BeginTransaction>...</BeginTransaction>  
      <!-- or -->  
      <Cancel>...</Cancel>  
      <!-- or -->  
      <ClearCache>...</ClearCache>  
      <!-- or -->  
      <CommitTransaction>...</CommitTransaction>  
      <!-- or -->  
      <Create>...</Create>  
      <!-- or -->  
      <Delete>...</Delete>  
      <!-- or -->  
      <DesignAggregations>...</DesignAggregations>  
      <!-- or -->  
      <Drop>...</Drop>  
      <!-- or -->  
      <Insert>...</Insert>  
      <!-- or -->  
      <Lock>...</Lock>  
      <!-- or -->  
      <MergePartitions>...</MergePartitions>  
      <!-- or -->  
      <NotifyTableChange>...</NotifyTableChange>  
      <!-- or -->  
      <Process>...</Process>  
      <!-- or -->  
      <Restore>...</Restore>  
      <!-- or -->  
      <RollbackTransaction>...</RollbackTransaction>  
      <!-- or -->  
      <SetPasswordEncryptionKey>...</SetPasswordEncryptionKey>  
      <!-- or -->  
      <Statement>...</Statement>  
      <!-- or -->  
      <Subscribe>...</Subscribe>  
      <!-- or -->  
      <Synchronize>...</Synchronize>  
      <!-- or -->  
      <Unlock>...</Unlock>  
      <!-- or -->  
      <Update>...</Update>  
      <!-- or -->  
      <UpdateCells>...</UpdateCells>  
   </Command>  
   ...  
</Execute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|基数|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[実行](../../../analysis-services/xmla/xml-elements-methods-execute.md)|  
|子要素|[Alter](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)、[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)、[バッチ](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)、 [BeginTransaction](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)、[キャンセル](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)、 [ClearCache](../../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md)、 [CommitTransaction](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)、[作成](../../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)、[削除](../../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md)、 [DesignAggregations](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md)、 [をドロップ](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)、[挿入](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)、[ロック](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)、 [MergePartitions](../../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)、 [NotifyTableChange](../../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md)、[プロセス](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)、[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)、 [RollbackTransaction](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)、 [SetPasswordEncryptionKey](http://msdn.microsoft.com/en-us/fb262737-f0f4-4441-985e-3b2a94d00a9e)、[ステートメント](../../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)、 [サブスクライブ](../../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md)、[同期](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)、[のロックを解除](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)、[更新](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)、 [UpdateCells](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 **コマンド**要素を使用して、 **Execute**データ ソースにコマンドをリレー メソッドです。 XML をのみ Analysis (XMLA) 1.1 仕様をサポートしているときに、**ステートメント**コマンド、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]多くの新しい XMLA コマンドをサポートしています。 サポートされる XMLA コマンドの詳細については[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]を参照してください[コマンド &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md).  
  
## <a name="see-also"></a>参照  
 [XML データ型 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
