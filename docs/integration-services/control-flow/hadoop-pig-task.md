---
title: Hadoop Pig Task | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hadooppigtask.f1
ms.assetid: 90646316-9822-48aa-9900-295a33750780
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4991fd3ad95a633881099b9677c9db55935f6a13
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2019
ms.locfileid: "65727598"
---
# <a name="hadoop-pig-task"></a>Hadoop Pig Task

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Hadoop Pig Task は、Hadoop クラスターで Pig スクリプトを実行するために使用します。  
  
 Hadoop Pig Task を追加するには、デザイナーにドラッグ アンド ドロップします。 その後タスクをダブルクリックするか、右クリックして **[編集]** をクリックし、 **[Hadoop Pig タスク エディター]** ダイアログ ボックスを表示します。  
  
 ![[Hadoop Pig タスク エディター]](../../integration-services/control-flow/media/hadoop-pig-task.png "[Hadoop Pig タスク エディター]")  
  
## <a name="options"></a>オプション  
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
  
  
