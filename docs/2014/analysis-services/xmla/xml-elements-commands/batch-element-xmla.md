---
title: バッチ要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d402c1f6c35370a506ed57c43b8fbc05d0b6bef7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178142"
---
# <a name="batch-element-xmla"></a>Batch 要素 (XMLA)
  実行します 1 つまたは複数の XML for Analysis (XMLA) コマンド、バッチ操作として順次またはのインスタンスに同時に[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。  
  
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
|子要素|[バインド](../xml-elements-properties/bindings-element-xmla.md)、 [DataSource](../xml-elements-properties/source-element-xmla.md)、 [DataSourceView](../xml-elements-properties/datasourceview-element-xmla.md)、 [ErrorConfiguration](../../scripting/objects/errorconfiguration-element-assl.md)、[並列](../xml-elements-properties/parallel-element-xmla.md)<br /><br /> 1 つ以上の次の XMLA コマンド: [Alter](alter-element-xmla.md)、[バックアップ](backup-element-xmla.md)、 [BeginTransaction](begintransaction-element-xmla.md)、 [ClearCache](clearcache-element-xmla.md)、 [CommitTransaction](committransaction-element-xmla.md)、[作成](create-element-xmla.md)、[削除](delete-element-xmla.md)、 [DesignAggregations](designaggregations-element-xmla.md)、[ドロップ](drop-element-xmla.md)、 [挿入](insert-element-xmla.md)、[ロック](lock-element-xmla.md)、 [MergePartitions](mergepartitions-element-xmla.md)、 [NotifyTableChange](notifytablechange-element-xmla.md)、[プロセス](process-element-xmla.md)、 [復元](restore-element-xmla.md)、 [RollbackTransaction](rollbacktransaction-element-xmla.md)、 [SetPasswordEncryptionKey](http://msdn.microsoft.com/en-us/fb262737-f0f4-4441-985e-3b2a94d00a9e)、[ステートメント](statement-element-xmla.md)、[サブスクライブ](subscribe-element-xmla.md)、[同期](synchronize-element-xmla.md)、[のロックを解除](unlock-element-xmla.md)、 [Update](update-element-xmla.md)、 [UpdateCells](drop-element-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|ProcessAffectedObjects|省略可能で、`Boolean` 型の属性。再処理が必要なすべてのオブジェクトを処理するかどうかを示します。<br /><br /> true に設定されている場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスは、`Batch` コマンドに含まれるオブジェクトを処理した結果として再処理が必要になったすべてのオブジェクトを処理します。<br /><br /> `false` に設定されている場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスは、`Batch` コマンドに含まれるオブジェクトだけを処理します。|  
|トランザクション|省略可能で、`Boolean` 型の属性。`Batch` コマンドに含まれるコマンドが単一のトランザクションとして扱われるか、それぞれ別個のトランザクションとして扱われるかを示します。<br /><br /> true に設定されている場合、`Batch` コマンドに含まれるすべてのコマンドは単一のトランザクションと見なされます。 いずれかのコマンドが失敗した場合、失敗したコマンドより前に実行されたコマンドはロールバックされ、後続のコマンドを実行せずに `Batch` コマンドが停止します。<br /><br /> `false` に設定されている場合、`Batch` コマンドはすべてのコマンドの実行を試行し、正常に完了したコマンドの結果をそれぞれコミットします。|  
  
## <a name="remarks"></a>コメント  
  
> [!WARNING]  
>  バッチ操作内でのコマンド/実行/ステートメントは現在サポートされません。  
  
 XMLA におけるバッチ操作の実行の詳細については、次を参照してください。[バッチ操作の実行&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/performing-batch-operations-xmla.md)します。  
  
## <a name="see-also"></a>参照  
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  
