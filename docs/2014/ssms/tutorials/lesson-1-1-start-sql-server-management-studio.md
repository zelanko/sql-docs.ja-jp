---
title: SQL Server Management Studio の起動 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 25ffaea6-0eee-4169-8dd0-1da417c28fc6
caps.latest.revision: 43
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2f928645fb89757b2284628d0400847cf5f3a1f2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071794"
---
# <a name="start-sql-server-management-studio"></a>SQL Server Management Studio の起動
  このチュートリアルを開始する前に、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開いてみましょう。  
  
## <a name="opening-sql-server-management-studio"></a>SQL Server Management Studio を開く  
  
#### <a name="to-open-sql-server-management-studio"></a>SQL Server Management Studio を開くには  
  
1.  **開始** メニューのをポイント**すべてのプログラム**、 をポイント[!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]、クリックして**SQL Server Management Studio**です。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、既定ではインストールされません。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を利用できない場合は、セットアップを実行してインストールしてください。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] は [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] では使用できません。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Express は無料でダウンロードから使用可能な[Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=37075&clcid=0x409)がこのチュートリアルの説明とは別のユーザー インターフェイスがします。  
  
2.  **[サーバーへの接続]** ダイアログ ボックスで既定の設定を確認し、 **[接続]** をクリックします。 接続する場合、**サーバー名**ボックスは、コンピューターの名前を含める必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]がインストールされています。 場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 、名前付きインスタンス、**サーバー名**ボックスでは、形式でインスタンス名を含める必要があります\< *computer_name* > \\ <*instance_name*>。  
  
## <a name="management-studio-components"></a>Management Studio のコンポーネント  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] では、情報は種類ごとに専用のウィンドウに表示されます。 データベース情報はオブジェクト エクスプローラーとドキュメント ウィンドウに表示されます。  
  
-   オブジェクト エクスプローラーには、サーバー上のすべてのデータベース オブジェクトがツリー形式で表示されます。 たとえば、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、および [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]のデータベースが表示されます。 オブジェクト エクスプローラーには、接続しているすべてのサーバーの情報が登録されています。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]を開くと、前回使用した設定にオブジェクト エクスプローラーを接続するかどうかをたずねられます。 [登録済みサーバー] の一覧でサーバーをダブルクリックすると、そのサーバーに接続できますが、接続するサーバーを登録する必要はありません。  
  
-   ドキュメント ウィンドウは、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]の中で最も大きな部分を占めています。 ドキュメント ウィンドウにはクエリ エディターとブラウザー ウィンドウを表示できます。 既定では [概要] ページが表示され、現在のコンピューター上にある [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続されます。  
  
## <a name="showing-additional-windows"></a>その他のウィンドウの表示  
  
#### <a name="to-show-the-registered-servers-window"></a>登録済みサーバー ウィンドウを表示するには  
  
1.  **[表示]** メニューの **[登録済みサーバー]** をクリックします。  
  
     [登録済みサーバー] ウィンドウがオブジェクト エクスプローラーの上に表示されます。 [登録済みサーバー] には、管理頻度の高いサーバーの一覧が表示されます。 この一覧にサーバーを追加したり、一覧からサーバーを削除することができます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューター上の [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]インスタンスのみが一覧に表示されます。  
  
2.  サーバーが表示されない場合、登録済みサーバーを右クリックし**データベース エンジン**、順にクリック**更新ローカル サーバーの登録**です。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [登録済みサーバーおよびオブジェクト エクスプローラーを使用した接続](../object/object-explorer.md)  
  
  