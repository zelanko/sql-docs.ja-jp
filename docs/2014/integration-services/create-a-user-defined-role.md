---
title: ユーザー定義のロールを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c4128993-2333-48c7-84b1-e51cdcea393d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cfb4e2004cab7e1b1a2d097d57ef3b8a66eba508
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437909"
---
# <a name="create-a-user-defined-role"></a>ユーザー定義ロールを作成する
    
### <a name="to-create-a-user-defined-role"></a>ユーザー定義ロールを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開きます。  
  
2.  **[表示]** メニューの **[オブジェクト エクスプローラー]** をクリックします。  
  
3.  オブジェクト エクスプローラー ツール バーで **[接続]** をクリックし、 **[データベース エンジン]** をクリックします。  
  
4.  **[サーバーへの接続]** ダイアログ ボックスで、サーバー名を指定し、認証モードを選択します。 ピリオド (.)、(local)、または `localhost` を使用すると、ローカル サーバーを指定できます。  
  
5.  **[Connect]** をクリックします。  
  
6.  [データベース]、[システム データベース]、[msdb]、[セキュリティ]、[ロール] を順に展開します。  
  
7.  [ロール] ノードの [データベース ロール] を右クリックし、 **[新しいデータベース ロール]** をクリックします。  
  
8.  [全般] ページでロール名を指定します。必要に応じて、所有者および所有されているスキーマを指定し、ロール メンバーを追加します。  
  
9. 必要に応じて、 **[権限]** をクリックし、オブジェクトの権限を構成します。  
  
10. 必要に応じて、 **[拡張プロパティ]** をクリックし、任意の拡張プロパティを構成します。  
  
11. **[OK]** をクリックします。  
  
  
