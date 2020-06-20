---
title: WMI 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], WMI
- connection managers [Integration Services], WMI
- WMI connection manager [Integration Services]
ms.assetid: fbfa4ba7-3d0d-4d6b-94ad-50741a88d03d
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 29ddc30f89621e9b4875a57c191a81ef3f10784d
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84920273"
---
# <a name="wmi-connection-manager"></a>WMI 接続マネージャー
  WMI 接続マネージャーを使用すると、パッケージは Windows Management Instrumentation (WMI) を使用して、企業環境の情報を管理できます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に含まれる Web サービス タスクでは、WMI 接続マネージャーが使用されます。  
  
 WMI 接続マネージャーをパッケージに追加すると、は、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 実行時に wmi 接続を解決する接続マネージャーを作成し、接続マネージャーのプロパティを設定して、接続マネージャーをパッケージのコレクションに追加し `Connections` ます。 接続マネージャーの `ConnectionManagerType` プロパティは、`WMI` に設定されます。  
  
## <a name="configuration-of-the-wmi-connection-manager"></a>WMI 接続マネージャーの構成  
 WMI 接続マネージャーは、次の方法で構成できます。  
  
-   サーバーの名前を指定します。  
  
-   サーバー上の名前空間を指定します。  
  
-   サーバーに接続する認証モードを選択します。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティについては、「 [[WMI 接続マネージャー エディター]](../wmi-connection-manager-editor.md)」を参照してください。  
  
 プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。  
  
## <a name="see-also"></a>参照  
 [Web サービスタスク](../control-flow/web-service-task.md)   
 [Integration Services &#40;SSIS&#41; の接続](integration-services-ssis-connections.md)  
  
  
