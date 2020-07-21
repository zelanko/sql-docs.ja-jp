---
title: MSMQ 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], message queues
- connection managers [Integration Services], MSMQ
- MSMQ connection manager
- message queue connections [Integration Services]
ms.assetid: a86900e2-450e-479f-b207-e1b02361d395
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 392b52142992baad8761ec1c25689db6726c8d67
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85438399"
---
# <a name="msmq-connection-manager"></a>MSMQ 接続マネージャー
  MSMQ 接続マネージャーを使用すると、Message Queuing (MSMQ) を使用するメッセージ キューにパッケージが接続できるようになります。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に含まれるメッセージ キュー タスクでは、MSMQ 接続マネージャーを使用します。  
  
 MSMQ 接続マネージャーをパッケージに追加すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は、実行時に MSMQ 接続を解決する接続マネージャーを作成し、接続マネージャーのプロパティを設定し、接続マネージャーをパッケージの `Connections` コレクションに追加します。 接続マネージャーの `ConnectionManagerType` プロパティは、`MSMQ` に設定されます。  
  
 MSMQ 接続マネージャーは、次の方法で構成できます。  
  
-   接続文字列を指定します。  
  
-   接続するメッセージ キューのパスを指定します。  
  
 次の表に示すように、パスの形式はキューの種類によって異なります。  
  
|[キューの種類]|パスのサンプル|  
|----------------|-----------------|  
|パブリック|\<computer name>\\<キュー名\>|  
|プライベート|\<computer name>\ プライベート $ \\<キュー名\>|  
  
 ピリオド (.) を使用してローカル コンピューターを表すことができます。  
  
## <a name="configuration-of-the-msmq-connection-manager"></a>MSMQ 接続マネージャーの構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [MSMQ 接続マネージャー エディター](../msmq-connection-manager-editor.md)」を参照してください。  
  
 プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。  
  
## <a name="see-also"></a>関連項目  
 [メッセージキュータスク](../control-flow/message-queue-task.md)   
 [Integration Services &#40;SSIS&#41; の接続](integration-services-ssis-connections.md)  
  
  
