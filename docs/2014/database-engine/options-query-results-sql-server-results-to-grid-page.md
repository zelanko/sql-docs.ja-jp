---
title: オプション (クエリ結果-SQL Server の結果をグリッド ページに) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLResultsToGrid
ms.assetid: f88a0f5c-e800-473b-ae23-c3943de5ed63
caps.latest.revision: 25
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: eafa41250705c453776947a3da56c86f9e3c0f90
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165679"
---
# <a name="options-query-results-sql-server-results-to-grid-page"></a>オプション (クエリ結果-SQL Server の結果をグリッド ページ)
  このページを使用すると、クエリ結果セットをグリッド形式で表示するためのオプションを指定できます。 このオプションに加えた変更は、新規の [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] クエリにのみ適用されます。 現在のクエリのオプションを変更するには、**[クエリ]** メニューの **[クエリ オプション]** をクリックするか、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のクエリ ウィンドウを右クリックして **[クエリ オプション]** をクリックします。 **[クエリ オプション]** ダイアログ ボックスの左ペインで、**[結果]** の **[グリッド]** をクリックします。  
  
## <a name="uielement-list"></a>UI 要素の一覧  
 **結果セットにクエリを含める**  
 クエリのテキストをクエリ出力の一部として返します。  
  
 **コピーまたは結果を保存するときの列ヘッダーを含める**  
 結果をクリップボードにコピーしたりファイルに保存したりするときに列のヘッダーを含めるには、このチェック ボックスをオンにします。 保存またはコピーする結果データに列のヘッダーを含めずにデータだけを含めるには、このチェック ボックスをオフにします。  
  
 **実行後に結果を破棄します。**  
 クエリの結果が変更履歴ウィンドウに表示されないようにします。 結果は実行後すぐに破棄されます。 このオプションを指定すると、メモリを節約できます。  
  
 **結果を別のタブに表示します。**  
 クエリ ドキュメント ウィンドウの下部ではなく、新しいタブに結果セットを表示するには、このチェック ボックスをオンにします。  
  
 **クエリ実行後に 結果 タブに切り替える**  
 クエリの実行時に画面フォーカスを結果ペインに自動的に設定するには、これをクリックします。  
  
 **取得される最大文字**  
 **XML 以外のデータ**:  
  
 1 ～ 65,535 の値を入力して、各セルに表示される最大文字数を指定します。  
  
> [!NOTE]  
>  大きな文字数を指定すると、結果セット内のデータが切り捨てられたように見える場合があります。 各セルに表示される最大文字数は、フォントのサイズに依存します。 大きな結果セットが返された場合、このボックスに大きな値を指定していると、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のメモリ上での実行速度が低下したり、システムのパフォーマンスに悪影響が及んだりすることがあります。  
  
 **[XML データ]**  
  
 **[1 MB]**、 **[2 MB]**、または **[5 MB]** を選択します。 すべての文字を取得する場合は、 **[無制限]** を選択します。  
  
 **既定値にリセット**  
 このページ上のすべての値を元の既定値にリセットします。  
  
  