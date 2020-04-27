---
title: チェックアウトを元に戻す |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourcControl.UndoCheckDialog
helpviewer_keywords:
- checking out files
- checkout source controls [SQL Server]
- undoing checkouts
ms.assetid: a6596b20-3aa5-4dc4-a4c5-3649f1f5a20e
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2057c78f953645c9b1a5915b9912ab99263cb005
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62773398"
---
# <a name="undo-checkouts"></a>チェックアウトの取り消し
  [**チェックアウトの取り消し**] コマンドを使用すると、既存のチェックアウトを取り消すことができます。 この機能は、ファイルを変更して保存した後に、その変更をロールバックする必要が生じた場合などに特に便利です。  
  
 [**チェックアウトの取り消しの詳細オプション**] ダイアログボックスで設定したオプションに応じて、Studio 環境では、項目の作業コピーをローカルディスクに残しておくか、ソース管理された最新のバージョンに置き換えます。 他のユーザーがソース管理システムのコンテキスト外で項目を修正した場合は、最新バージョンを取得できるとは限りません。  
  
### <a name="to-undo-a-checkout"></a>チェックアウトを元に戻すには  
  
1.  ソリューション エクスプローラーでプロジェクトを選択します。  
  
2.  [**ファイル**] メニューの [**ソース管理**] をポイントし、[**チェックアウトの取り消し**] をクリックします。  
  
3.  [**チェックアウトの取り消し**] ダイアログボックスで、適切なオプションを選択し、[**チェックアウトの取り消し**] ボタンをクリックします。  
  
     **[列]**  
     表示する列と、その表示順序を指定します。  
  
     **[平面表示]**  
     項目をソース管理接続の下に一覧表示します。  
  
     **名前**  
     チェックアウトを取り消す項目の名前を表示します。 選択した項目の横にチェックボックスが表示されます。 項目のチェックアウトを取り消さない場合は、チェック ボックスをオフにします。  
  
     **[オプション]**  
     ボタンの右側の矢印をクリックすると、ソース管理のプラグインに固有のチェックアウトの取り消しオプションが表示されます。  
  
     **基づく**  
     表示列の順序を並べ替えます。  
  
     **[ツリー表示]**  
     チェックアウトを元に戻す項目のフォルダーおよび項目階層を表示します。  
  
     **[チェックアウトの取り消し]**  
     チェックアウトを元に戻して、チェックアウトされたファイルに対する変更を破棄します。  
  
## <a name="see-also"></a>参照  
 [ファイルのチェックアウト](../../2014/database-engine/check-out-files.md)   
 [チェックアウトの管理](../../2014/database-engine/manage-checkouts.md)  
  
  
