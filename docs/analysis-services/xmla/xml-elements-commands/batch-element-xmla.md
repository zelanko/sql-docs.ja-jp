---
title: "バッチ要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Batch Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Batch
- microsoft.xml.analysis.batch
- http://schemas.microsoft.com/analysisservices/2003/engine#Batch
helpviewer_keywords: Batch command
ms.assetid: 818f3212-9605-4e34-8623-1154d9fae1f0
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f30483f7b8ff16b7fcc0d4a5656d57b3c1c871a1
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="batch-element-xmla"></a>Batch 要素 (XMLA)
  1 つまたは複数の XML for Analysis (XMLA) コマンドとして実行バッチ操作では、順番またはのインスタンスに同時に[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <Batch Transaction="Boolean" ProcessAffectedObjects="Boolean">  
      <Bindings>...</Bindings>  
      <DataSource>...</DataSource>  
      <DataSourceView>...</DataSourceView>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <Parallel>...</Parallel>  
      <!-- One or more XMLA commands -->  
   </Batch>  
</Command>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子要素|[バインド](../../../analysis-services/xmla/xml-elements-properties/bindings-element-xmla.md)、[データソース](../../../analysis-services/xmla/xml-elements-properties/datasource-element-xmla.md)、 [DataSourceView](../../../analysis-services/xmla/xml-elements-properties/datasourceview-element-xmla.md)、 [ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)、[並列](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md)<br /><br /> 1 つ以上の次の XMLA コマンド: [Alter](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)、[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)、 [BeginTransaction](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)、 [ClearCache](../../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md)、 [CommitTransaction](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)、[作成](../../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)、[削除](../../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md)、 [DesignAggregations](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md)、[ドロップ](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)、 [挿入](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)、[ロック](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)、 [MergePartitions](../../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)、 [NotifyTableChange](../../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md)、[プロセス](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)、 [復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)、 [RollbackTransaction](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)、 [SetPasswordEncryptionKey](http://msdn.microsoft.com/en-us/fb262737-f0f4-4441-985e-3b2a94d00a9e)、[ステートメント](../../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)、 [をサブスクライブ](../../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md)、[同期](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)、[のロックを解除](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)、[更新](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)、 [UpdateCells](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|Description|  
|---------------|-----------------|  
|ProcessAffectedObjects|(省略可能な**ブール**属性) を再処理を必要とするすべてのオブジェクトを処理するかどうかを示します。<br /><br /> 場合は true に設定する、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスに含まれるオブジェクトを処理した結果を再処理を必要とする任意のオブジェクトを処理する、**バッチ**コマンド。<br /><br /> 場合設定**false**、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスに含まれるオブジェクトだけを処理する、**バッチ**コマンド。|  
|トランザクション|(省略可能な**ブール**属性) に、コマンドが含まれているかどうかを示す、**バッチ**コマンドは、単一のトランザクションまたは個々 のトランザクションとして扱われます。<br /><br /> 場合、true に、すべてに含まれるコマンドのセット、**バッチ**コマンドは、単一のトランザクションと見なされます。 いずれかのコマンドが失敗した、失敗したコマンドの前に実行されるコマンドはロールバック、および**バッチ**後続のコマンドを実行することがなくコマンドを停止します。<br /><br /> 場合に設定**false**、**バッチ**コマンドは、すべてのコマンドを実行しようとし、正常に完了した各コマンドの結果をコミットします。|  
  
## <a name="remarks"></a>解説  
  
> [!WARNING]  
>  バッチ操作内でのコマンド/実行/ステートメントは現在サポートされません。  
  
 XMLA におけるバッチ操作の実行の詳細については、次を参照してください。[バッチ操作の実行 &#40;です。XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/performing-batch-operations-xmla.md).  
  
## <a name="see-also"></a>参照  
 [コマンドと #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
