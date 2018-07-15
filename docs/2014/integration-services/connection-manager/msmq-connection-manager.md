---
title: MSMQ 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], message queues
- connection managers [Integration Services], MSMQ
- MSMQ connection manager
- message queue connections [Integration Services]
ms.assetid: a86900e2-450e-479f-b207-e1b02361d395
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f9be09df9ab705d45dfdeee7caebfeb556a7a669
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37306122"
---
# <a name="msmq-connection-manager"></a>MSMQ 接続マネージャー
  MSMQ 接続マネージャーを使用すると、Message Queuing (MSMQ) を使用するメッセージ キューにパッケージが接続できるようになります。  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に含まれるメッセージ キュー タスクでは、MSMQ 接続マネージャーを使用します。  
  
 MSMQ 接続マネージャーをパッケージに追加すると[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]接続マネージャーの実行時に MSMQ 接続を解決するには、接続マネージャーのプロパティを設定、接続マネージャーを追加する作成、`Connections`コレクションに、パッケージです。 `ConnectionManagerType`接続マネージャーのプロパティに設定されて`MSMQ`します。  
  
 MSMQ 接続マネージャーは、次の方法で構成できます。  
  
-   接続文字列を指定します。  
  
-   接続するメッセージ キューのパスを指定します。  
  
 次の表に示すように、パスの形式はキューの種類によって異なります。  
  
|[キューの種類]|パスのサンプル|  
|----------------|-----------------|  
|パブリック|\<コンピューター名>\\<キュー名\>|  
|Private|\<コンピューター名>\Private$\\<キュー名\>|  
  
 ピリオド (.) を使用してローカル コンピューターを表すことができます。  
  
## <a name="configuration-of-the-msmq-connection-manager"></a>MSMQ 接続マネージャーの構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [MSMQ 接続マネージャー エディター](../msmq-connection-manager-editor.md)」を参照してください。  
  
 プログラムによる接続マネージャーの構成方法の詳細については、次を参照してください。<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>と[プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)します。  
  
## <a name="see-also"></a>参照  
 [メッセージ キュー タスク](../control-flow/message-queue-task.md)   
 [Integration Services &#40;SSIS&#41;接続](integration-services-ssis-connections.md)  
  
  
