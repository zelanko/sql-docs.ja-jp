---
title: ファイルをチェックイン |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VisualStudio.SourceControl.CheckInDialog
helpviewer_keywords:
- checking in files
ms.assetid: 0657a387-8411-4406-bef9-d262a5bfa269
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cf955c5a2101ba6ffa582601cd587b27a63c1621
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178285"
---
# <a name="check-in-files"></a>ファイルのチェックイン
  ファイルのソース管理を行っている場合、修正後のファイルを他のユーザーも利用できるようにするには、そのファイルをソース管理にチェックインする必要があります。 ファイルをチェックインすると、チェックインしたバージョンがソース管理プロバイダーに書き込まれ、そのファイルの最新バージョンになります。  
  
 使用することができます、**チェックイン**コマンド ファイルをチェックインします。 このコマンドを使用してソリューションまたはプロジェクトをチェックインした場合は、そのソリューションまたはプロジェクト内にあるファイルもすべてチェックインされます。 ただし、個々のソース コード ファイルをチェックインしても、そのファイルが属するプロジェクトやソリューションはチェックインされません。  
  
### <a name="to-check-in-a-file"></a>ファイルをチェックインするには  
  
1.  ソリューション エクスプ ローラーで、チェックインするファイルを右クリックして**チェックイン**です。  
  
2.  場合、**チェックイン** ダイアログ ボックスが表示されたら、適切なオプションを選択し、クリックして**OK**です。  
  
     **チェックイン**  
     選択されている項目をすべてチェックインします。  
  
     **[列]**  
     表示する列と、その表示順序を指定します。  
  
     **コメント**  
     チェックイン操作に関連付けるコメントを追加します。  
  
     **項目のチェックイン時に、ダイアログ ボックスでチェックを表示しません。**  
     チェックインの処理中にダイアログ ボックスが表示されないようにします。  
  
     **フラット ビュー**  
     チェックインするファイルをソース管理接続の下に一覧表示します。  
  
     **Name**  
     チェックインする項目の名前を表示します。 チェック ボックスをオンの横にあるアイテムが表示されます。 特定の項目をチェックインしない場合は、そのチェック ボックスをオフにします。  
  
     **[オプション]**  
     ボタンの右側の矢印をクリックすると、ソース管理のプラグインに固有のチェックイン オプションが表示されます。  
  
     **Sort**  
     表示列の順序を並べ替えます。  
  
     **ツリー ビュー**  
     チェックインする項目のフォルダーおよびファイル階層を表示します。  
  
 チェックインしたファイルが共有チェックアウトの一部でない場合、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 環境ではそのファイルが直ちにチェックインされます。 あるいは、直ちにはチェックインされずに、他のユーザーが作成したバージョンとのマージを要求するダイアログが表示されることもあります。  
  
## <a name="see-also"></a>参照  
 [変更されたファイルの一覧を表示します。](../../2014/database-engine/view-a-list-of-modified-files.md)   
 [チェックインの管理](../../2014/database-engine/manage-checkins.md)  
  
  