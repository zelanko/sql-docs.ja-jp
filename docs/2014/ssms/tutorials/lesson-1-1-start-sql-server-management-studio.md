---
title: SQL Server Management Studio の起動 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 25ffaea6-0eee-4169-8dd0-1da417c28fc6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 94466dc6c069ced5b2743cbd8a14d98271303477
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63188842"
---
# <a name="start-sql-server-management-studio"></a>SQL Server Management Studio の起動
  このチュートリアルを開始する前に、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開いてみましょう。  
  
## <a name="opening-sql-server-management-studio"></a>SQL Server Management Studio を開く  
  
#### <a name="to-open-sql-server-management-studio"></a>SQL Server Management Studio を開くには  
  
1.  **開始**メニューで、**すべてのプログラム**、 をポイント[!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]、順にクリックします**SQL Server Management Studio**します。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、既定ではインストールされません。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を利用できない場合は、セットアップを実行してインストールしてください。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] は [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] では使用できません。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Express は無料でダウンロードから使用可能な[Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/?LinkID=37075&clcid=0x409)、このチュートリアルでは説明とは別のユーザー インターフェイスのあるがします。  
  
2.  **[サーバーへの接続]** ダイアログ ボックスで既定の設定を確認し、 **[接続]** をクリックします。 に接続する、**サーバー名**ボックスは、コンピューターの名前を含める必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]がインストールされています。 場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 、名前付きのインスタンス、**サーバー名**ボックス形式でインスタンス名を含める必要があります\< *computer_name* > \\ <*instance_name*>。  
  
## <a name="management-studio-components"></a>Management Studio のコンポーネント  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] では、情報は種類ごとに専用のウィンドウに表示されます。 データベース情報はオブジェクト エクスプローラーとドキュメント ウィンドウに表示されます。  
  
-   オブジェクト エクスプローラーには、サーバー上のすべてのデータベース オブジェクトがツリー形式で表示されます。 たとえば、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、および [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]のデータベースが表示されます。 オブジェクト エクスプローラーには、接続しているすべてのサーバーの情報が登録されています。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]を開くと、前回使用した設定にオブジェクト エクスプローラーを接続するかどうかをたずねられます。 [登録済みサーバー] の一覧でサーバーをダブルクリックすると、そのサーバーに接続できますが、接続するサーバーを登録する必要はありません。  
  
-   ドキュメント ウィンドウは、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]の中で最も大きな部分を占めています。 ドキュメント ウィンドウにはクエリ エディターとブラウザー ウィンドウを表示できます。 既定では [概要] ページが表示され、現在のコンピューター上にある [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続されます。  
  
## <a name="showing-additional-windows"></a>その他のウィンドウの表示  
  
#### <a name="to-show-the-registered-servers-window"></a>登録済みサーバー ウィンドウを表示するには  
  
1.  **[表示]** メニューの **[登録済みサーバー]** をクリックします。  
  
     [登録済みサーバー] ウィンドウがオブジェクト エクスプローラーの上に表示されます。 [登録済みサーバー] には、管理頻度の高いサーバーの一覧が表示されます。 この一覧にサーバーを追加したり、一覧からサーバーを削除することができます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューター上の [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]インスタンスのみが一覧に表示されます。  
  
2.  右クリックし、サーバーが表示されない場合、登録済みサーバーで**データベース エンジン**、順にクリックします**更新プログラムのローカル サーバーの登録**します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [登録済みサーバーおよびオブジェクト エクスプローラーを使用した接続](../object/object-explorer.md)  
  
  
