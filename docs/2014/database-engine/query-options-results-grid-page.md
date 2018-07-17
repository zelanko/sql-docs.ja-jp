---
title: クエリ オプション の結果 (グリッド ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.grid.f1
ms.assetid: 764bf435-3aab-4c62-b4e0-64fe020a5a95
caps.latest.revision: 18
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: ba8b1d1fb182ca0f16fe157630253b74b9580eb2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312292"
---
# <a name="query-options-results-grid-page"></a>[クエリ オプション] の [結果] ([グリッド] ページ)
  このページを使用すると、クエリ結果セットをグリッド形式で表示するためのオプションを指定できます。  
  
## <a name="options"></a>および  
 **結果セットにクエリを含める**  
 クエリのテキストを結果セットの一部として返します。  
  
 **コピーまたは結果を保存するときに、列ヘッダーを含める**  
 結果をクリップボードにコピーしたりファイルに保存したりするときに、列のヘッダー (タイトル) を含めます。 保存またはコピーされる結果データに列の見出しを含めずに、データだけ保存またはコピーするには、このチェック ボックスをオフにします。  
  
 **実行後に結果を破棄します。**  
 画面表示がクエリ結果を受け取った後にクエリ結果を破棄することによって、メモリを解放します。  
  
 **別のタブで結果を表示します。**  
 結果セットを、クエリ ドキュメント ウィンドウの下部ではなく、新しいドキュメント ウィンドウに表示します。  
  
 **クエリ実行後に [結果] タブに切り替えます**  
 画面のフォーカスを自動的に結果セットに設定します。  
  
 **最大文字数を取得**  
 **XML 以外のデータ**:  
  
 1 ～ 65,535 の値を入力して、各セルに表示される最大文字数を指定します。  
  
> [!NOTE]  
>  大きな文字数を指定すると、結果セット内のデータが切り捨てられたように見える場合があります。 各セルに表示される最大文字数は、フォントのサイズに依存します。 大きな結果セットが返された場合、このボックスに大きな値を指定していると、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のメモリ上での実行速度が低下したり、システムのパフォーマンスに悪影響が及んだりすることがあります。  
  
 **[XML データ]**  
  
 **[1 MB]**、 **[2 MB]**、または **[5 MB]** を選択します。 すべての文字を取得する場合は、 **[無制限]** を選択します。  
  
 **既定値にリセット**  
 このページ上のすべての値を元の既定値にリセットします。  
  
  
