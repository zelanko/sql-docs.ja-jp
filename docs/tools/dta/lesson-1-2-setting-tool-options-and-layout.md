---
title: ツール オプションとレイアウトを設定 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-query-tuning
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: 43e97ce0-97bc-4a27-9485-5bbeb7190b85
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 68a4c894fb4defe848b146c59b3ad159ac3da287
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="lesson-1-2---setting-tool-options-and-layout"></a>レッスン 1、2、ツールのオプションの設定とレイアウト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]使用して、フォント、起動時に表示するデータベース エンジン チューニング アドバイザーのグラフィカル ユーザー インターフェイス (GUI) を構成するオプションを設定することができ、その他のツールの機能に最もが使用する方法をサポートします。 このページの演習では、ユーザーが設定できるオプションとその設定方法について学習します。  
  
### <a name="set-the-tool-options"></a>ツール オプションの設定  
  
1.  データベース エンジン チューニング アドバイザーを起動します。 Windows の **[スタート]** ボタンをクリックし、 **[すべてのプログラム]**をポイントして、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]] をポイントし、 **[パフォーマンス ツール]**をポイントして、 **[データベース エンジン チューニング アドバイザー]**をクリックします。  
  
2.  **[ツール]** メニューの **[オプション]**をクリックします。  
  
3.  **[オプション]** ダイアログ ボックスが開き、次のオプションが表示されます。  
  
    -   **[スタートアップ時]** ボックスの一覧には、データベース エンジン チューニング アドバイザーの起動時に表示されるアイテムが示されます。 既定では、 **[新しいセッションを表示します]** が選択されています。  
  
    -   データベースの一覧と **[全般]** タブのテーブルに表示できるフォントを確認するには、 **[フォント変更]** をクリックします。このオプションで選択したフォントは、データベース エンジン チューニング アドバイザーの推奨設定グリッドおよびチューニング実行後のレポートにも使用されます。 既定ではシステム フォントが使用されます。  
  
    -   **[最近使用した項目の一覧に表示する項目数]** には、 **1** ～ **10**の値を設定できます。 このオプションでは、 **[ファイル]** メニューの **[最新のセッション]** または **[最近使ったファイル]** をクリックしたときに表示される最大項目数を設定します。 既定では **4**に設定されています。  
  
    -   **[最後のチューニング オプションを保存する]** チェック ボックスをオンにした場合、既定では、最後のチューニング セッションで指定したチューニング オプションが次のチューニング セッションで使用されます。 データベース エンジン チューニング アドバイザーの既定のチューニング オプションを使用するには、このチェック ボックスをオフにします。 既定では、このオプションはオンになっています。  
  
    -   誤ってチューニング セッションを削除しないよう、既定では **[完全にセッションを削除する前に確認する]** がオンになっています。  
  
    -   データベース エンジン チューニング アドバイザーによるワークロードの分析が完了する前に、間違ってチューニング セッションを停止しないように、既定では **[セッションの分析を停止する前に確認する]** がオンになっています。  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 2: データベース エンジン チューニング アドバイザーの使用](../../tools/dta/lesson-2-using-database-engine-tuning-advisor.md)  
  
  
  
