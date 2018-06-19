---
title: Hadoop Pig Task | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hadooppigtask.f1
ms.assetid: 90646316-9822-48aa-9900-295a33750780
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4027f5762330f694e24058d9b9583d57fa6e0fbd
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35410594"
---
# <a name="hadoop-pig-task"></a>Hadoop Pig Task
  Hadoop Pig Task は、Hadoop クラスターで Pig スクリプトを実行するために使用します。  
  
 Hadoop Pig Task を追加するには、デザイナーにドラッグ アンド ドロップします。 その後タスクをダブルクリックするか、右クリックして **[編集]** をクリックし、 **[Hadoop Pig タスク エディター]** ダイアログ ボックスを表示します。  
  
 ![[Hadoop Pig タスク エディター]](../../integration-services/control-flow/media/hadoop-pig-task.png "[Hadoop Pig タスク エディター]")  
  
## <a name="options"></a>および  
 **[Hadoop Pig Task Editor]** (Hadoop Pig Task エディター) ダイアログ ボックスで、次のオプションを構成します。  
  
|フィールド|[説明]|  
|-----------|-----------------|  
|**Hadoop 接続**|既存の Hadoop 接続マネージャーを指定するか、新しい Hadoop 接続マネージャーを作成します。 この接続マネージャーは、WebHCat サービスがホストされる場所を示します。|  
|**[SourceType]**|クエリのソースの種類を指定します。 使用できる値は、 **ScriptFile** と **DirectInput**です。|  
|**[InlineScript]**|**[SourceType]** の値が **DirectInput**の場合は、Pig スクリプトを指定します。|  
|**[HadoopScriptFilePath]**|**[SourceType]** の値が **ScriptFile**の場合は、Hadoop 上のスクリプト ファイルのパスを指定します。|  
|**[TimeoutInMinutes]**|タイムアウト値を分単位で指定します。 タイムアウトが経過するまでに完了していない場合、Hadoop ジョブが停止します。 Hadoop ジョブを非同期的に実行するようにスケジュールを設定するには、0 を指定します。|  
  
## <a name="see-also"></a>参照  
 [Hadoop 接続マネージャー](../../integration-services/connection-manager/hadoop-connection-manager.md)  
  
  
