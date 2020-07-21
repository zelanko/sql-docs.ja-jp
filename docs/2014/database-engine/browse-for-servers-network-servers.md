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
ms.openlocfilehash: 0ba5e4e5dd6d9a6541a98e0cb30229d7335bac24
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936083"
---
# <a name="browse-for-servers-network-servers"></a>[サーバーの参照] ([ネットワーク サーバー])
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コンポーネントに接続する際に、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの正確な名前がわからない場合は、**[サーバー名]** ボックスで **[参照]** をクリックして **[サーバーの参照]** ダイアログ ボックスを開きます。  
  
 サーバー コンピューターの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser サービスによって、このダイアログ ボックスの内容が自動入力されます。 インスタンス名が一覧に表示されない場合は、次のような原因が考えられます。  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を実行しているコンピューターで、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Browser サービスが実行されていない。  
  
-   ファイアウォールにより、UDP ポート 1434 がブロックされている。  
  
-   **HideInstance** フラグが設定されている。  
  
 一覧に表示されないインスタンスに接続するには、TCP/IP ポート番号または名前付きパイプのパイプ名を含む、そのインスタンスの完全な接続文字列を入力します。  
  
## <a name="options"></a>オプション  
 **[接続に使用する、ネットワーク内の SQL Server インスタンスを選択します]**  
 ツリーに表示された [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスをクリックして、接続するサーバーを指定します。 または記号でマークされたノードをクリックして、ツリービューの一部を表示または非表示にすることができ **+** **-** ます。  
  
  
