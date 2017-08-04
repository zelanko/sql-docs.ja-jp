---
title: "ODBC 接続マネージャー |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connections [Integration Services], ODBC
- ODBC connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], ODBC
ms.assetid: e8c77aa7-6772-485e-918e-cef9eeb18c58
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a136e71727d1a0b729f7014448dd97d81a7af89d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="odbc-connection-manager"></a>ODBC 接続マネージャー
  ODBC 接続マネージャーを使用すると、パッケージは Open Database Connectivity (ODBC) の仕様を使用して、さまざまなデータベース管理システムに接続できます。  
  
 ODBC 接続をパッケージに追加して接続マネージャーのプロパティを設定すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は接続マネージャーを作成し、パッケージの **Connections** コレクションに追加します。 接続マネージャーは、実行時に物理 ODBC 接続として解決されます。  
  
 接続マネージャーの **ConnectionManagerType** プロパティは、 **ODBC**に設定されます。  
  
 ODBC 接続マネージャーは、次の方法で構成できます。  
  
-   ユーザーまたはシステム データ ソースの名前を参照する、接続文字列を指定します。  
  
-   接続先のサーバーを指定します。  
  
-   接続を実行時に保持するかどうかを示します。  
  
## <a name="configuration-of-the-odbc-connection-manager"></a>ODBC 接続マネージャーの構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [ODBC 接続マネージャーの UI リファレンス](../../integration-services/connection-manager/odbc-connection-manager-ui-reference.md)  
  
 プログラムによる接続マネージャーの構成の詳細については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」および「 [プログラムによる接続の追加](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)に設定されます。  
  
## <a name="see-also"></a>参照  
 [Integration Services &#40;SSIS&#41; の接続](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  
