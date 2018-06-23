---
title: バッチ要素 (XMLA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Batch Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Batch
- microsoft.xml.analysis.batch
- http://schemas.microsoft.com/analysisservices/2003/engine#Batch
helpviewer_keywords:
- Batch command
ms.assetid: 818f3212-9605-4e34-8623-1154d9fae1f0
caps.latest.revision: 14
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 76fcd68ca71db298bc66dc63a3fa20c394c196c8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176698"
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
|親要素|[Command](../xml-elements-properties/command-element-xmla.md)|  
|子要素|[バインド](../xml-elements-properties/bindings-element-xmla.md)、[データソース](../xml-elements-properties/source-element-xmla.md)、 [DataSourceView](../xml-elements-properties/datasourceview-element-xmla.md)、 [ErrorConfiguration](../../scripting/objects/errorconfiguration-element-assl.md)、[並列](../xml-elements-properties/parallel-element-xmla.md)<br /><br /> One or more of the following XMLA commands: [Alter](alter-element-xmla.md), [Backup](backup-element-xmla.md), [BeginTransaction](begintransaction-element-xmla.md), [ClearCache](clearcache-element-xmla.md), [CommitTransaction](committransaction-element-xmla.md), [Create](create-element-xmla.md), [Delete](delete-element-xmla.md), [DesignAggregations](designaggregations-element-xmla.md), [Drop](drop-element-xmla.md), [Insert](insert-element-xmla.md), [Lock](lock-element-xmla.md), [MergePartitions](mergepartitions-element-xmla.md), [NotifyTableChange](notifytablechange-element-xmla.md), [Process](process-element-xmla.md), [Restore](restore-element-xmla.md), [RollbackTransaction](rollbacktransaction-element-xmla.md), [SetPasswordEncryptionKey](http://msdn.microsoft.com/en-us/fb262737-f0f4-4441-985e-3b2a94d00a9e), [Statement](statement-element-xmla.md), [Subscribe](subscribe-element-xmla.md), [Synchronize](synchronize-element-xmla.md), [Unlock](unlock-element-xmla.md), [Update](update-element-xmla.md), [UpdateCells](drop-element-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|ProcessAffectedObjects|省略可能で、`Boolean` 型の属性。再処理が必要なすべてのオブジェクトを処理するかどうかを示します。<br /><br /> true に設定されている場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスは、`Batch` コマンドに含まれるオブジェクトを処理した結果として再処理が必要になったすべてのオブジェクトを処理します。<br /><br /> `false` に設定されている場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスは、`Batch` コマンドに含まれるオブジェクトだけを処理します。|  
|トランザクション|省略可能で、`Boolean` 型の属性。`Batch` コマンドに含まれるコマンドが単一のトランザクションとして扱われるか、それぞれ別個のトランザクションとして扱われるかを示します。<br /><br /> true に設定されている場合、`Batch` コマンドに含まれるすべてのコマンドは単一のトランザクションと見なされます。 いずれかのコマンドが失敗した場合、失敗したコマンドより前に実行されたコマンドはロールバックされ、後続のコマンドを実行せずに `Batch` コマンドが停止します。<br /><br /> `false` に設定されている場合、`Batch` コマンドはすべてのコマンドの実行を試行し、正常に完了したコマンドの結果をそれぞれコミットします。|  
  
## <a name="remarks"></a>コメント  
  
> [!WARNING]  
>  バッチ操作内でのコマンド/実行/ステートメントは現在サポートされません。  
  
 XMLA におけるバッチ操作の実行の詳細については、次を参照してください。[バッチ操作の実行&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/performing-batch-operations-xmla.md)です。  
  
## <a name="see-also"></a>参照  
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  