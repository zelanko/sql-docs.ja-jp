---
title: SMO 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], SMO
- SMO connection manager
- connection managers [Integration Services], SMO
ms.assetid: d273f1fb-a6a8-4f2f-a5ff-55c2e3de4723
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 85b202ed9914ce151b26d00d59ad9a84e96ef830
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52804952"
---
# <a name="smo-connection-manager"></a>SMO 接続マネージャー
  SMO 接続マネージャーを使用すると、パッケージは、SQL 管理オブジェクト (SMO) サーバーに接続できます。  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に含まれる転送タスクでは、SMO 接続マネージャーを使用します。 たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを転送するログイン転送タスクでは、SMO 接続マネージャーを使用します。  
  
 SMO 接続マネージャーをパッケージに追加すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は、実行時に SMO 接続を解決する接続マネージャーを作成し、接続マネージャーのプロパティを設定し、接続マネージャーをパッケージの `Connections` コレクションに追加します。 接続マネージャーの `ConnectionManagerType` プロパティは、`SMOServer` に設定されます。  
  
 SMO 接続マネージャーは、次の方法で構成できます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がインストールされているサーバーの名前を指定します。  
  
-   サーバーに接続する認証モードを選択します。  
  
## <a name="configuration-of-the-smo-connection-manager"></a>SMO 接続マネージャーの構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [SMO 接続マネージャー エディター](../smo-connection-manager-editor.md)」を参照してください。  
  
 プログラムによる接続マネージャーの構成の詳細については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」および「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。  
  
## <a name="see-also"></a>参照  
 [Integration Services &#40;SSIS&#41; の接続](integration-services-ssis-connections.md)  
  
  
