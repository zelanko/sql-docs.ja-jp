---
title: 要素 (XMLA) コマンド |Microsoft Docs
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
- Command Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.command
- Command
- urn:schemas-microsoft-com:xml-analysis#Command
- http://schemas.microsoft.com/analysisservices/2003/engine#Command
helpviewer_keywords:
- Command element
ms.assetid: 9abc14df-7cbe-46bc-ba0f-f0691c19afad
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f9b461e0ec565776ead270902cf6c01ebe7409d3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37332242"
---
# <a name="command-element-xmla"></a>Command 要素 (XMLA)
  によって実行されるコマンドが含まれています、 [Execute](../xml-elements-methods-execute.md)メソッド。  
  
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
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[実行](../xml-elements-methods-execute.md)|  
|子要素|[Alter](../xml-elements-commands/alter-element-xmla.md)、[バックアップ](../xml-elements-commands/backup-element-xmla.md)、[バッチ](../xml-elements-commands/batch-element-xmla.md)、 [BeginTransaction](../xml-elements-commands/begintransaction-element-xmla.md)、[キャンセル](../xml-elements-commands/cancel-element-xmla.md)、 [ClearCache](../xml-elements-commands/clearcache-element-xmla.md)、 [CommitTransaction](../xml-elements-commands/committransaction-element-xmla.md)、[作成](../xml-elements-commands/create-element-xmla.md)、[削除](../xml-elements-commands/delete-element-xmla.md)、 [DesignAggregations](../xml-elements-commands/designaggregations-element-xmla.md)、[ドロップ](../xml-elements-commands/drop-element-xmla.md)、[挿入](../xml-elements-commands/insert-element-xmla.md)、[ロック](../xml-elements-commands/lock-element-xmla.md)、 [MergePartitions](../xml-elements-commands/mergepartitions-element-xmla.md)、 [NotifyTableChange](../xml-elements-commands/notifytablechange-element-xmla.md)、[プロセス](../xml-elements-commands/process-element-xmla.md)、[復元](../xml-elements-commands/restore-element-xmla.md)、 [RollbackTransaction](../xml-elements-commands/rollbacktransaction-element-xmla.md)、 [SetPasswordEncryptionKey](http://msdn.microsoft.com/en-us/fb262737-f0f4-4441-985e-3b2a94d00a9e)、[ステートメント](../xml-elements-commands/statement-element-xmla.md)、 [サブスクライブ](../xml-elements-commands/subscribe-element-xmla.md)、[同期](../xml-elements-commands/synchronize-element-xmla.md)、[のロックを解除](../xml-elements-commands/unlock-element-xmla.md)、 [Update](../xml-elements-commands/update-element-xmla.md)、 [UpdateCells](../xml-elements-commands/drop-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `Command` 要素は、データ ソースにコマンドを伝えるために `Execute` メソッドによって使用されます。 XML for Analysis (XMLA) 1.1 仕様では `Statement` コマンドのみをサポートしていますが、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では多数の新しい XMLA コマンドをサポートしています。 サポートされる XMLA コマンドの詳細については[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]を参照してください[コマンド&#40;XMLA&#41;](../xml-elements-commands/xml-elements-commands.md)します。  
  
## <a name="see-also"></a>参照  
 [XML データ型&#40;XMLA&#41;](../xml-data-types/xml-data-types-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
