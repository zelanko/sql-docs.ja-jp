---
title: Analysis Services 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], Analysis Services
- connection managers [Integration Services], Analysis Services
- Analysis Services connection manager
ms.assetid: 9f9cadad-a1d0-4db5-98f5-df5dbbec1be4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8f8ca9ce77e151e761e2cbb1f9128a44784af8ca
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68890400"
---
# <a name="analysis-services-connection-manager"></a>Analysis Services 接続マネージャー
  接続マネージャーを使用すると[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、パッケージは、データベースを実行するサーバー、または[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]キューブとディメンションデータへのアクセスを提供するプロジェクトに接続できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でのパッケージ開発中に接続できるのは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]プロジェクトのみです。 実行時には、パッケージは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを配置したサーバーおよびデータベースに接続します。  
  
 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL 実行タスクや [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 処理タスクなどのタスクと、データ マイニング モデル トレーニング変換先などの変換先は、どちらも [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 接続マネージャーを使用します。  
  
 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データべースの詳細については、「[多次元モデル データベース &#40;SSAS&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/multidimensional-model-databases-ssas)」を参照してください。  
  
## <a name="configuration-of-the-analysis-services-connection-manager"></a>Analysis Services 接続マネージャーの構成  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]接続マネージャーをパッケージに追加すると、は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 、実行時に接続として[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]解決される接続マネージャーを作成し、接続マネージャーのプロパティを設定して、接続`Connections`マネージャーをパッケージのコレクションに追加します。 接続マネージャーの `ConnectionManagerType` プロパティは、`MSOLAP100` に設定されます。  
  
 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 接続マネージャーは、次の方法で構成できます。  
  
-   Microsoft OLE Provider for Analysis Services プロバイダーの要件を満たすように構成された、接続文字列を指定します。  
  
-   接続する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを指定します。  
  
-   
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続する場合、認証モードを指定します。  
  
-   接続マネージャーから作成される接続を、実行時に保持するかどうかを指定します。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 
  [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[Analysis Services 接続マネージャーの追加] ダイアログ ボックスの UI リファレンス](add-analysis-services-connection-manager-dialog-box-ui-reference.md)  
  
 プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。  
  
  
