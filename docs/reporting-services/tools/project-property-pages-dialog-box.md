---
title: "プロジェクト プロパティ ページ ダイアログ ボックス |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- sql13.rpt.rptdesigner.projectpropertypages.general.f1
helpviewer_keywords:
- Project Property Pages dialog box
ms.assetid: 209d9e22-37fc-418f-8739-83adcf447d3f
caps.latest.revision: 35
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 659be9982440426eee0d8b5a2df8d54b4d32bbc4
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---

# <a name="project-property-pages-dialog-box"></a>[プロパティ ページ] ダイアログ ボックス

  プロジェクトのプロパティ ページを使用すると、レポート サーバー プロジェクトの配置プロパティを構成できます。 このダイアログ ボックスを開くには、**プロジェクト** メニューをクリックして*\<レポート プロジェクト名 >***プロパティ**です。  
  
 構成プロパティを定義した後は、ツール バーの **[ソリューション構成]** ボックスの一覧から構成を選択できるようになります。  

![ssrs_project_properties](../../reporting-services/reports/media/ssrs-project-properties.png)
  
## <a name="options"></a>オプション  
 **構成**  
 編集する構成を選択します。 初期状態で使用できる構成は、 **[Debug]**、 **[DebugLocal]**、および **[Release]**です。 アクティブな構成が、 **Active(Debug)**のように最初に表示されます。  
  
 複数の構成のプロパティを同時に表示するには、 **[すべての構成]** または **[複数の構成]**を選択します。  
  
 新しく構成を作成するには、ツール バーの **[構成マネージャー]** をクリックします。  
  
 **[構成マネージャー]**  
 ソリューション全体の構成を管理するか、さらに構成を追加します。 詳細については、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] のドキュメントを参照してください。  
  
 **[OutputPath]**  
 ビルドの検証、配置、およびレポートのプレビューで使用されるレポート定義の保存先のパスを入力するか、貼り付けます。 このパスは、プロジェクトに使用するパス、およびプロジェクトのパスの下にある子フォルダーの相対パスとは異なる必要があります。  
  
> [!NOTE]  
>  複数の構成を使用して、実行するタスクに応じてパスを切り替えることができます。  
  
 **[ErrorLevel]**  
 エラーとしてレポートされるビルドの問題の重大度を入力します。 **[ErrorLevel]** の値以下の重大度レベルを持つ問題は、エラーとしてレポートされます。それ以外の問題は、警告としてレポートされます。 エラーが発生すると、ビルド タスクが失敗する原因になります。 有効な重大度レベルは、0 ～ 4 の範囲です。 既定値は 2 です。  
  
 **[StartItem]**  
 プロジェクトがレポート サーバーにパブリッシュされた後に Web ブラウザーに表示されるレポート、またはローカルでプロジェクトを実行するときにプレビュー ウィンドウに表示されるレポートを選択します。 開始アイテムは、プロジェクトをビルドしても配置しない構成の場合、および **[Debug]** コマンド (**F5**) を使用する場合に必要となります。 このアイテムは、プロジェクトを配置する構成では必須です。  
  
 **[OverwriteDataSources]**  
 レポートのパブリッシュ時に、サーバー上のデータ ソースをプロジェクト内のデータ ソースで上書きする場合は、 **[True]** を選択します。 サーバー上の既存のデータ ソースを残す場合は、 **[False]** を選択します。  
  
 **[TargetServerVersion]**  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の適切なバージョンを選択するか、 **[バージョンの検出]** を選択して、 **TargetServer URL** プロパティによって識別される、サーバーにインストールされているバージョンを自動的に特定します。 既定値は**SQL Server 2016**です。  
  
 **[TargetDataSourceFolder]**  
 パブリッシュした共有データ ソースを保存するフォルダーの名前です。 フォルダーを指定しない場合、レポートと同じフォルダーにデータ ソースがパブリッシュされます。 フォルダーがレポート サーバー上に存在しない場合は、レポートのパブリッシュ時に、レポート デザイナーによってフォルダーが作成されます。  
  
 ネイティブ モードで実行されているレポート サーバーにパブリッシュする場合は、フォルダー階層の完全なパスをルートから指定します。 たとえば、「Folder1/Folder2/Folder3」のように指定します。  
  
 SharePoint 統合モードで実行されているレポート サーバーにパブリッシュする場合は、SharePoint ライブラリの URL を指定します。 たとえば、 `http:\\<servername>\<site>\Documents\MyFolder`のようにします。  
  
 **[TargetReportFolder]**  
 パブリッシュしたレポートを保存するフォルダーの名前です。 既定値は、レポート プロジェクトの名前です。 フォルダーがレポート サーバー上に存在しない場合は、レポートのパブリッシュ時に、レポート デザイナーによってフォルダーが作成されます。  
  
 ネイティブ モードで実行されているレポート サーバーにパブリッシュする場合は、フォルダー階層の完全なパスをルートから指定します。 フォルダーが別の場所に存在する場合は、フォルダーへのパスをルートから指定します。たとえば、「Folder1/Folder2/Folder3」のように指定します。  
  
 SharePoint 統合モードで実行されているレポート サーバーにパブリッシュする場合は、SharePoint ライブラリの URL を指定します。 たとえば、 `http:\\<servername>\\<site>\Documents\MyFolder`のようにします。  
  
 **[TargetServerURL]**  
 対象レポート サーバーの URL です。 レポートをパブリッシュする前に、このプロパティを有効なレポート サーバーの URL に設定する必要があります。  
  
 ネイティブ モードで実行されているレポート サーバーにパブリッシュする場合は、レポート サーバーの仮想ディレクトリの URL を指定します。 たとえば、 `http:\\<server>\reportserver`のようにします。 これは、レポート マネージャーではなく、レポート サーバーの仮想ディレクトリです。 既定では、レポート サーバーは、"reportserver" という名前の仮想ディレクトリにインストールされます。  
  
 SharePoint 統合モードで動作しているレポート サーバーにパブリッシュする場合は、SharePoint トップレベル サイトまたはサブサイトの URL を使用します。 サイトを指定しなかった場合は、既定のトップレベル サイトが使用されます。 例: 
+ `http:\\<servername>`、 
+ `http:\\<servername\<site>` 
+ `http:\\<servername>\<site>\<subsite>`をインストールしたユーザーを対象にしています。  

## <a name="next-steps"></a>次の手順

[レポートのパブリッシュ](http://msdn.microsoft.com/library/ef5a514e-e818-4041-a8b0-15835f9a046b)   
[SharePoint ライブラリへのレポートのパブリッシュ](../../reporting-services/reports/publish-a-report-to-a-sharepoint-library.md)   
[展開プロパティの設定 & #40 です。Reporting Services &#41;](../../reporting-services/tools/set-deployment-properties-reporting-services.md)   
[レポート デザイナーの F1 ヘルプ](../../reporting-services/tools/report-designer-f1-help.md)  

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)
