---
title: "パッケージのプロパティ ダイアログ ボックス |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/26/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ssis.ssms.ispackageprop.general.f1
- sql13.ssis.ssms.packageproperties.f1
ms.assetid: a70acbf4-5f5c-4606-8ce4-8eb3684233de
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 07d44a56b531bc2e933480559a2f6d3d2457578e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/21/2017

---
# <a name="package-properties-dialog-box"></a>[パッケージのプロパティ] ダイアログ ボックス
  **[パッケージのプロパティ]** ダイアログ ボックスでは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに格納されているパッケージのプロパティを表示できます。  
  
 詳細については、「[Integration Services &#40;SSIS&#41; Packages](/sql-docs/docs/integration-services/integration-services-ssis-packages)」(Integration Services &#40;SSIS&#41; のパッケージ) を参照してください。  
  
 **目的に合ったトピックをクリックしてください**  
  
-   [[パッケージのプロパティ] ダイアログ ボックスを開く](#open_dialog)  
  
-   [オプションの構成](#options)  
  
##  <a name="open_dialog"></a> [パッケージのプロパティ] ダイアログ ボックスを開く  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]から [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに接続します。  
  
     SSISDB データベースをホストする [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続されます。  
  
2.  オブジェクト エクスプローラーで、ツリーを展開して、 **[Integration Services カタログ]** ノードを表示します。  
  
3.  **[SSISDB]** ノードを展開します。  
  
4.  プロパティを表示するパッケージが格納されているフォルダーを展開します。  
  
5.  パッケージを右クリックし、 **[プロパティ]**をクリックします。  
  
##  <a name="options"></a> オプションの構成  
 **[全般]** ページでは、選択されているパッケージのプロパティを表示できます。  
  
 **[全般]** ページに表示されるすべてのプロパティは読み取り専用です。  
  
 **名前**  
 パッケージの名前が表示されます。  
  
 **[Identifier]**  
 パッケージ ID を一覧表示します。  
  
 **エントリ ポイント**  
 値 **True** は、パッケージが直接起動されることを示します。 値 **False** は、パッケージ実行タスクを使用して、パッケージが別のパッケージによって起動されることを示します。 既定値は **True**です。  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で親パッケージと子パッケージの両方に対してこのプロパティを設定するには、ソリューション エクスプローラーでパッケージを右クリックし、 **[エントリ ポイント パッケージ]**をクリックします。  
  
 **Description**  
 省略可能なパッケージの説明が表示されます。  
  
  

