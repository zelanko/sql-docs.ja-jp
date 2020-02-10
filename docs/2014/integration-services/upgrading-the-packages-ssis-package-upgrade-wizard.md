---
title: パッケージのアップグレード (SSIS パッケージアップグレードウィザード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.upgradingpackage.f1
ms.assetid: cdb842e3-2e59-4ede-b127-be4fde46875c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 686354531b89a43cb2e9ddc669ff136ef7b87216
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66054737"
---
# <a name="upgrading-the-packages-ssis-package-upgrade-wizard"></a>[パッケージをアップグレードしています] (SSIS パッケージ アップグレード ウィザード)
  
  **[パッケージをアップグレードしています]** ページでは、パッケージのアップグレードの進行状況を表示したり、アップグレード プロセスを中断したりできます。 
  [!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ アップグレード ウィザードでは、選択したパッケージが 1 つずつアップグレードされます。  
  
 **SQL Server データベースまたはパッケージ ストアに保存されたアップグレード済みパッケージを表示するには**  
  
-   
  [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]のオブジェクト エクスプローラーで [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]のローカル インスタンスに接続し、 **[格納されたパッケージ]** ノードを展開すると、アップグレードされたパッケージが表示されます。  
  
 **SQL Server データ ツールからアップグレードされたパッケージを表示するには**  
  
-   
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーで [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のプロジェクトを開き、 **[SSIS パッケージ]** ノードを展開すると、アップグレードされたパッケージが表示されます。  
  
## <a name="options"></a>オプション  
 **メッセージウィンドウ**  
 アップグレード プロセス中に、進行状況メッセージと概要情報が表示されます。  
  
 **アクション**  
 アップグレード処理で実行されるアクションを表示します。  
  
 **状態**  
 各アクションの結果を表示します。  
  
 **Message**  
 各アクションによって生成されるエラー メッセージを表示します。  
  
 **停止**  
 パッケージのアップグレードを停止します。  
  
 **Report**  
 パッケージのアップグレード結果を含むレポートの処理を選択します。  
  
-   レポートをオンラインで表示します。  
  
-   レポートをファイルに保存します。  
  
-   レポートをクリップボードにコピーします。  
  
-   レポートを電子メール メッセージとして送信します。  
  
## <a name="see-also"></a>参照  
 [Integration Services パッケージのアップグレード](install-windows/upgrade-integration-services-packages.md)  
  
  
