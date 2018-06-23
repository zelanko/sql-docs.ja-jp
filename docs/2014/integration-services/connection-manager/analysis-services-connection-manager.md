---
title: Analysis Services 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connections [Integration Services], Analysis Services
- connection managers [Integration Services], Analysis Services
- Analysis Services connection manager
ms.assetid: 9f9cadad-a1d0-4db5-98f5-df5dbbec1be4
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1055a76b227bbd965150a2372ac798b3c20ca8c9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175397"
---
# <a name="analysis-services-connection-manager"></a>Analysis Services 接続マネージャー
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 接続マネージャーを使用すると、パッケージは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを実行するサーバー、またはキューブとディメンション データへのアクセスを提供する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトに接続できます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でのパッケージ開発中に接続できるのは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]プロジェクトのみです。 実行時には、パッケージは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを配置したサーバーおよびデータベースに接続します。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL 実行タスクや [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 処理タスクなどのタスクと、データ マイニング モデル トレーニング変換先などの変換先は、どちらも [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 接続マネージャーを使用します。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データべースの詳細については、「[多次元モデル データベース &#40;SSAS&#41;](../../analysis-services/multidimensional-models/multidimensional-model-databases-ssas.md)」を参照してください。  
  
## <a name="configuration-of-the-analysis-services-connection-manager"></a>Analysis Services 接続マネージャーの構成  
 追加すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、パッケージへの接続マネージャー [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]接続として解決されるマネージャーを作成、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、実行時に接続を選択し、マネージャーのプロパティを接続を設定する接続マネージャーを追加します`Connections`パッケージのコレクション。 `ConnectionManagerType`接続マネージャーのプロパティに設定されて`MSOLAP100`です。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 接続マネージャーは、次の方法で構成できます。  
  
-   Microsoft OLE Provider for Analysis Services プロバイダーの要件を満たすように構成された、接続文字列を指定します。  
  
-   接続する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを指定します。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続する場合、認証モードを指定します。  
  
-   接続マネージャーから作成される接続を、実行時に保持するかどうかを指定します。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[Analysis Services 接続マネージャーの追加] ダイアログ ボックスの UI リファレンス](add-analysis-services-connection-manager-dialog-box-ui-reference.md)  
  
 プログラムによる接続マネージャーの構成方法の詳細については、次を参照してください。<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>と[プログラムで接続を追加する](../building-packages-programmatically/adding-connections-programmatically.md)です。  
  
  