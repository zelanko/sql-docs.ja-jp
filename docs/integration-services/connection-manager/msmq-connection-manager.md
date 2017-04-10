---
title: "MSMQ 接続マネージャー | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "接続 [Integration Services], メッセージ キュー"
  - "接続マネージャー [Integration Services], MSMQ"
  - "MSMQ 接続マネージャー"
  - "メッセージ キュー接続 [Integration Services]"
ms.assetid: a86900e2-450e-479f-b207-e1b02361d395
caps.latest.revision: 35
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 35
---
# MSMQ 接続マネージャー
  MSMQ 接続マネージャーを使用すると、Message Queuing (MSMQ) を使用するメッセージ キューにパッケージが接続できるようになります。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に含まれるメッセージ キュー タスクでは、MSMQ 接続マネージャーを使用します。  
  
 MSMQ 接続マネージャーをパッケージに追加すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は、実行時に MSMQ 接続を解決する接続マネージャーを作成し、接続マネージャーのプロパティを設定し、接続マネージャーをパッケージの **Connections** コレクションに追加します。 接続マネージャーの **ConnectionManagerType** プロパティは、**MSMQ** に設定されます。  
  
 MSMQ 接続マネージャーは、次の方法で構成できます。  
  
-   接続文字列を指定します。  
  
-   接続するメッセージ キューのパスを指定します。  
  
 次の表に示すように、パスの形式はキューの種類によって異なります。  
  
|[キューの種類]|パスのサンプル|  
|----------------|-----------------|  
|パブリック|\<コンピューター名>\\<キュー名\>|  
|Private|\<コンピューター名>\Private$\\<キュー名\>|  
  
 ピリオド (.) を使用してローカル コンピューターを表すことができます。  
  
## MSMQ 接続マネージャーの構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「[MSMQ 接続マネージャー エディター](../../integration-services/connection-manager/msmq-connection-manager-editor.md)」を参照してください。  
  
 プログラムによる接続マネージャーの構成の詳細については、「<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>」および「[プログラムによる接続の追加](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)」を参照してください。  
  
## 参照  
 [メッセージ キュー タスク](../../integration-services/control-flow/message-queue-task.md)   
 [Integration Services (SSIS) の接続](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  