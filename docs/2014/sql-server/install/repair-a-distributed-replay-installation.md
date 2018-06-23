---
title: 分散再生のインストールの修復 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fcd8ca8-1ceb-457d-9545-096c74e274d7
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8adf917831b33c1603b3c0c4a1e7b678900cf7dd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163801"
---
# <a name="repair-a-distributed-replay-installation"></a>分散再生のインストールの修復
  分散再生コンポーネント (コントローラーまたはクライアント) を修復すると、次の処理が行われます。  
  
1.  ディスク上に関連付けられたすべてのファイルを再インストールし、既存のファイルを置き換えます。  
  
2.  対応するサービス アカウントが削除された場合、Windows サービス アカウントを再作成します。  
  
 修復操作を利用してコンポーネントを追加または削除することはできません。 コンポーネントを追加または削除を確認するかの機能ツリーで、対応するコンポーネントをオフにして、**機能の選択**ページ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップします。  
  
### <a name="to-repair-a-failed-installation-of-distributed-replay"></a>分散再生のインストールの失敗を修復するには  
  
1.  **開始**] メニューのをクリックして**コントロール パネルの [**、順にダブルクリック**プログラム追加と削除**です。  
  
2.  選択[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]で、 **プログラムのアンインストールまたは**ウィンドウで、し、、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]ダイアログ ボックスで、をクリックして**修復**です。  
  
3.  手順に従います、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]ウィザード、および、**機能の選択** ページで、修復、およびをクリックする分散再生コンポーネントを選択して **[次へ]。** です。  
  
4.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インストール ウィザードを完了すると、選択した 分散再生の機能が修復されます。  
  
  