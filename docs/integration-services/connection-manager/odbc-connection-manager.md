---
title: "ODBC 接続マネージャー |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.odbcconnection.f1
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
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 8397673c7ed9dfe8ae02871f9077ed7286e49863
ms.openlocfilehash: f3e331efe9c6a297ef8d9dc342fb07c83ddafc03
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

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
  
 プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)に設定されます。  
  
## <a name="odbc-connection-manager-ui-reference"></a>ODBC 接続マネージャーの UI リファレンス
  **[ODBC の接続マネージャーの構成]** ダイアログ ボックスを使用すると、接続を ODBC データ ソースに追加できます。  
  
 ODBC 接続マネージャーの詳細については、「 [ODBC Connection Manager](../../integration-services/connection-manager/odbc-connection-manager.md)」を参照してください。  
  
### <a name="options"></a>オプション  
 **[データ接続]**  
 既存の ODBC 接続マネージャーを一覧から選択します。  
  
 **[データ接続のプロパティ]**  
 選択されている ODBC 接続マネージャーのプロパティと値を表示します。  
  
 **新規**  
 **[接続マネージャー]** ダイアログ ボックスを使用して ODBC 接続マネージャーを作成します。 このダイアログ ボックスでは、必要に応じて新しい ODBC データ ソースを作成することもできます。  
  
 **Del**  
 接続を選択し、 **[削除]** ボタンを使用して削除します。  
## <a name="see-also"></a>参照  
 [Integration Services &#40;SSIS&#41; の接続](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  

