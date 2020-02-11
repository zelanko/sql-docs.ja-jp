---
title: '[サーバーの参照] ([ネットワーク サーバー]) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.browseservers.network.f1
ms.assetid: a59ffcd6-4b69-4c5c-9740-699ccb2183fb
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ffa52839c20a34574423e3b123da79f734fb69ee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62786691"
---
# <a name="browse-for-servers-network-servers"></a>[サーバーの参照] ([ネットワーク サーバー])
  
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コンポーネントに接続する際に、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの正確な名前がわからない場合は、 **[サーバー名]** ボックスで **[参照]** をクリックして **[サーバーの参照]** ダイアログ ボックスを開きます。  
  
 サーバー コンピューターの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser サービスによって、このダイアログ ボックスの内容が自動入力されます。 インスタンス名が一覧に表示されない場合は、次のような原因が考えられます。  
  
-   
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を実行しているコンピューターで、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Browser サービスが実行されていない。  
  
-   ファイアウォールにより、UDP ポート 1434 がブロックされている。  
  
-   
  **HideInstance** フラグが設定されている。  
  
 一覧に表示されないインスタンスに接続するには、TCP/IP ポート番号または名前付きパイプのパイプ名を含む、そのインスタンスの完全な接続文字列を入力します。  
  
## <a name="options"></a>オプション  
 **接続に使用するネットワーク内の SQL Server インスタンスを選択します**  
 ツリーに表示された [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスをクリックして、接続するサーバーを指定します。 **+** または**-** 記号でマークされたノードをクリックして、ツリービューの一部を表示または非表示にすることができます。  
  
  
