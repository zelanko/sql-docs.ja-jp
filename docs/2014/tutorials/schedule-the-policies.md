---
title: ポリシーのスケジュール設定 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59417a54-55f1-4468-ba41-368aa852c2d4
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 99c6e3a4eacfea76ff16ea266d38f2087c088f33
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075635"
---
# <a name="schedule-the-policies"></a>ポリシーのスケジュール設定
  ここでは、前の作業でインポートしたベスト プラクティス ポリシーをスケジュールします。  
  
### <a name="to-schedule-the-best-practices-policies"></a>ベスト プラクティス ポリシーをスケジュールするには  
  
1.  オブジェクト エクスプ ローラーで、**管理**、展開**ポリシーの管理**、展開**ポリシー**ベスト プラクティス ポリシーを右クリックし、クリックして**プロパティ**です。  
  
    > [!NOTE]  
    >  代わりに、ベスト プラクティスに関連付けられているポリシーを簡単に確認し、最高の並べ替えにプラクティスのカテゴリを展開して**管理**、展開**ポリシーの管理**をクリックして**ポリシー**です。 **[表示]** メニューの **[オブジェクト エクスプローラーの詳細]** をクリックします。 **オブジェクト エクスプ ローラーの詳細** ウィンドウで、をクリックして、**カテゴリ**見出しをカテゴリで、ポリシーを並べ替えます。 ベスト プラクティス ポリシーがあるプレフィックス**マイクロソフトのベスト プラクティス**です。 構成、およびをクリックするポリシーを右クリックして**プロパティ**です。  
  
2.  **全般**のページ、**ポリシーを開く** ダイアログ ボックスで、**評価モード**一覧で、をクリックして**スケジュールで**です。  
  
3.  横に、**スケジュール**ボックスで、をクリックして**Pick**既存のスケジュールを指定するか、をクリックする**新規**新しいスケジュールを作成します。  
  
4.  選択することができます、スケジュールを構成した後、**有効**スケジュールされたポリシーを有効にする ページの上部にあるチェック ボックスをオンします。  
  
5.  スケジュールするポリシーごとに、手順 1. ～ 4. を繰り返します。  
  
    > [!NOTE]  
    >  スケジュールされたポリシーが実行された後に評価結果を表示するには、対象インスタンスのポリシー履歴ログを開きます。 ログを開くを右クリックして**ポリシーの管理**、クリックして**履歴を表示する**です。  
  
## <a name="summary"></a>まとめ  
 スケジュールしたポリシーを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の単一インスタンス上で実行するよう構成しました。 スケジュールしたポリシーを複数のインスタンスに配置するには、このチュートリアルの次の作業に進みます。  
  
## <a name="next-steps"></a>次の手順  
 [スケジュールされたポリシーの複数インスタンスへの配置](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
  