---
title: ファイルをチェック アウト |Microsoft ドキュメント
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
- Visual Studio.SourceControl.CheckOutDialog
helpviewer_keywords:
- checking out files
ms.assetid: cc033727-51bb-4b58-a12b-8977ce61ff56
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d8b36e03ff939cb7ddbc15bdec1d41532a87d9b7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075340"
---
# <a name="check-out-files"></a>ファイルのチェックアウト
  チェックインしたファイルの編集が許可されるように [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 環境を設定していない場合、チェックインしたファイルを変更するには、まずファイルをチェックアウトする必要があります。 ファイルをチェックアウトすると、ファイルのバージョンのコピーがローカル ディスクにコピーされ、ファイルの読み取り専用の属性が解除されます。  
  
 ファイルのチェックアウトには、排他モードと共有モードがあります。 ファイルを排他モードでチェックアウトすると、チェックアウトしたユーザーがそのファイルを再びチェックインするまで、他のユーザーがそのファイルをチェックアウトすることはできません。 共有モードでファイルをチェックアウトすると、他のユーザーもそのファイルをチェックアウトして変更できます。このファイルをチェックインする場合は、必要に応じて、チェックアウトしたバージョンと、他のユーザーが作成したバージョンをマージします。  
  
 使用して、**チェック アウト**コマンドをソース管理対象のプロジェクトとファイルをチェック アウトします。 このコマンドを使用してソリューションやプロジェクトをチェックアウトすると、ソリューションまたはプロジェクト内のファイルもすべてチェックアウトされます。ただし、個々のソース コード ファイルをチェックアウトしても、そのファイルが属するプロジェクトやソリューションはチェックアウトされません。  
  
> [!NOTE]  
>  場合、 [!INCLUDE[msCoName](../includes/msconame-md.md)] 、複数のチェック アウトを許可する、プロジェクトの Visual SourceSafe データベースが構成され、排他的にチェック アウトしたファイルは、オフにする必要がある、**複数のチェック アウトを許可する**オプション、 **チェック アウト オプションの高度な**ファイルをチェックインする前に ダイアログ ボックス。 この設定を有効にするには、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を再起動する必要があります。  
  
### <a name="to-check-out-a-file"></a>ファイルをチェックアウトするには  
  
1.  ソリューション エクスプローラーで、プロジェクトまたはファイルを選択します。  
  
2.  **ファイル** メニューのをポイント**ソース管理**、クリックして**編集用にチェック アウト**です。  
  
3.  場合、**編集用にチェック アウト** ダイアログ ボックスが表示されたら、しをクリックして項目を選択**チェック アウト**です。構成した場合、[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]環境を表示しないように、**チェック アウト**ダイアログ ボックスで、ソリューション エクスプ ローラーおよび可能性のあるすべての子で選択した項目はチェック アウトします。  
  
     **チェックアウト**  
     選択されているすべての項目をチェックアウトします。  
  
     **[列]**  
     表示する列と、その表示順序を指定します。  
  
     **コメント**  
     チェックアウト操作に関連付けるコメントを指定します。  
  
     **項目のチェック アウトの場合は、チェック アウトの表示 ダイアログ ボックスをしません。**  
     チェックアウト処理時にダイアログ ボックスが表示されないようにします。  
  
     **フラット ビュー**  
     チェックアウトする項目をソース管理接続の下に一覧表示します。  
  
     **[編集]**  
     項目をチェックアウトしないで変更します。**編集**ボタンは、ある場合にのみが表示されます。[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]チェックインされているファイルの編集をサポートするように構成します。  
  
     **Name**  
     チェックアウトできる項目の名前を表示します。 選択されている項目の横にはチェック ボックスが表示されます。 特定の項目をチェックアウトしない場合は、そのチェック ボックスをオフにします。  
  
     **[オプション]**  
     ボタンの右側の矢印をクリックすると、ソース管理のプラグインに固有のチェックアウト オプションが表示されます。  
  
     **Sort**  
     表示する列の順序を並べ替えます。  
  
     **ツリー ビュー**  
     チェックアウトする項目のフォルダーおよびファイル階層を表示します。  
  
## <a name="see-also"></a>参照  
 [チェックインされているファイルを編集します。](../../2014/database-engine/edit-checked-in-files.md)   
 [自動的にファイルをチェック アウトと編集](../../2014/database-engine/automatically-check-out-files-upon-edit.md)   
 [チェック アウトを元に戻す](../../2014/database-engine/undo-checkouts.md)   
 [チェックアウトの管理](../../2014/database-engine/manage-checkouts.md)  
  
  