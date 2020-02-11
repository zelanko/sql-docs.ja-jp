---
title: 配置プロパティを設定する (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], deploying
- publishing reports [Reporting Services]
- properties [Reporting Services], deployment
- deploying reports [Reporting Services]
ms.assetid: 18201ca0-bf4a-484f-b3a2-95d1046a6a9b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 85ddbe528734e5824c80bd5cc00a15d3b32c9bec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66099550"
---
# <a name="set-deployment-properties-reporting-services"></a>配置プロパティを設定する (Reporting Services)
  
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、レポート サーバー プロジェクトのアイテムをレポート サーバーにパブリッシュするには、レポート サーバーのほかに、必要に応じてレポートのフォルダー、および共有データ ソースを指定する必要があります。 
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] がレポートをビルド、プレビュー、および配置するために必要なプロパティと値は、レポート サーバー プロジェクトのプロジェクト構成に保存されています。 これらのプロジェクトのプロパティから成る複数の名前付きセットを作成すると、プロパティ セット間で切り替えることができるので便利です。 それぞれのプロパティのセットは、構成です。 たとえば、レポートをテスト サーバーにパブリッシュする構成や、実稼働サーバーにパブリッシュする別の構成などがあります。  
  
 プロジェクト構成でプロジェクトのプロパティのセットを作成および管理するには、構成マネージャーを使用します。 構成マネージャーは、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]の基となる [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] によってサポートされる機能です。  
  
> [!NOTE]  
>  この機能は、インストール後に Reporting Services を構成するために使用する Reporting Services 構成マネージャーと混同しないようにしてください。 詳細については、「[レポート サーバーを構成および管理する](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md) &#40;SSRS ネイティブ モード&#41;」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]では、Report Server プロジェクトまたはソリューションからレポートをパブリッシュするアクションは、 *レポートの配置*として知られています。  
  
### <a name="to-set-deployment-properties"></a>配置プロパティを設定するには  
  
1.  レポート プロジェクトを右クリックして、 **[プロパティ]** をクリックします。  
  
2.  プロジェクトの **[プロパティ ページ]** ダイアログ ボックスの **[構成]** ボックスの一覧で、編集する構成をクリックします。 一般的な構成は、 **[DebugLocal]** 、 **[Debug]** 、および **[Release]** です。  
  
    > [!NOTE]  
    >  複数の構成を使用すると、異なるレポート サーバー間または設定間ですばやく切り替えることができます。  
  
3.  [ **OutputPath** ] テキストボックスに、ローカルファイルシステムのパスを入力するか貼り付けて、レポートのビルドの検証、配置、およびプレビューで使用されるレポート定義を保存します。 このパスは、プロジェクトに使用するパス、およびプロジェクトのパスの下にある子フォルダーの相対パスとは異なる必要があります。  
  
4.  [ **ErrorLevel** ] テキストボックスに、エラーとして報告されるビルドの問題の重大度を入力します。 **ErrorLevel**の値以下の重大度レベルを持つレポート、データソース、またはその他のプロジェクトリソースをビルドするときに発生する問題は、エラーとして報告されます。それ以外の場合、問題は警告として報告されます。 エラーが発生すると、ビルド タスクが失敗する原因になります。 有効な重大度レベルは、0 ～ 4 の範囲です。 既定値は 2 です。  
  
     **ErrorLevel** を使用すると、ビルドの機密性を上げたり下げたりすることができます。 たとえば、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] レポート サーバーへの配置時に、マップを含んだレポートをビルドする場合、既定でエラーが表示され、レポートのビルドは失敗します。 **ErrorLevel** を下げると、マップがレポートから削除され、警告が表示され、レポートのビルド処理は続行されます。  
  
5.  [ **Startitem** ] ボックスの一覧で、レポートプロジェクトの実行時にプレビューウィンドウまたはブラウザーウィンドウに表示するレポートを選択します。  
  
6.  **[OverwriteDataSources]** ボックスの一覧で、共有データ ソースがパブリッシュされるたびにサーバー上の共有データ ソースを上書きする場合は、 **[True]** を選択し、サーバー上のデータ ソースを保持する場合は、 **[False]** を選択します。  
  
7.  [ **TargetServerVersion** ] ボックスの一覧で、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]また[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]はの[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]いずれかのバージョンを選択するか、[**バージョンの検出**] を選択して、 **TargetServer URL**プロパティで識別されるサーバーにインストールされているバージョンを自動的に判別します。 既定値は**SQL Server 2008 R2**です。  
  
     [OutputPath] で指定されたパスに保存されている、 **[TargetServer URL]** で指定されたレポート サーバーのビルド レポートをカスタマイズするには、 **[TargetServerVersion]** を使用します。  
  
8.  **[TargetDataSourceFolder]** ボックスに、パブリッシュした共有データ ソースを配置するレポート サーバー上のフォルダーを入力します。 **[TargetDataSourceFolder]** の既定値は [データ ソース] です。 この値を空にした場合は、 **[TargetReportFolder]** で指定した場所にデータ ソースがパブリッシュされます。  
  
9. **[TargetReportFolder]** ボックスに、パブリッシュしたレポートを配置するレポート サーバー上のフォルダーを入力します。 [ **Targetreportfolder** ] の既定値は、レポートプロジェクトの名前です。  
  
    > [!NOTE]  
    >  ネイティブ モードで実行されているレポート サーバー上のフォルダーにレポートをパブリッシュするには、そのフォルダーに対する **パブリッシュ** 権限が必要です。 パブリッシュ権限は、ロールの割り当てを使用し、パブリッシュ操作を含むロールにユーザー アカウントをマップすることによって設定します。 詳細については、「 [ロールの割り当てを作成および管理する](../security/create-and-manage-role-assignments.md)」を参照してください。 SharePoint 統合モードで実行されているレポート サーバーの場合は、SharePoint サイトへの **メンバー** 権限または **所有者** 権限が必要です。 詳細については、「 [レポート サーバー アイテムの SharePoint サイトおよびリスト権限のリファレンス](../security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)」を参照してください。  
  
10. **[TargetServerURL]** ボックスに、対象レポート サーバーの URL を入力します。 レポートをパブリッシュする前に、このプロパティを有効なレポート サーバーの URL に設定する必要があります。 ネイティブ モードで実行されているレポート サーバーにパブリッシュする場合は、レポート サーバーの仮想ディレクトリの URL を指定します (たとえば、http: *//server/reportserver* 、または https: *//server/reportserver*)。 これは、レポート マネージャーではなく、レポート サーバーの仮想ディレクトリです。  
  
     SharePoint 統合モードで動作しているレポート サーバーにパブリッシュする場合は、SharePoint トップレベル サイトまたはサブサイトの URL を使用します。 サイトを指定しなかった場合は、既定のトップレベル サイト (http://*servername*、http://*servername*/*site* 、http://*servername*/*site*/*subsite*など) が使用されます。  
  
### <a name="to-set-configuration-manager-properties"></a>構成マネージャーのプロパティを設定するには  
  
1.  レポート プロジェクトを右クリックして、 **[プロパティ]** をクリックします。  
  
2.  プロジェクトの **[プロパティ ページ]** ダイアログ ボックスで、 **[構成マネージャー]** をクリックします。  
  
3.  **[構成マネージャー]** ダイアログ ボックスで、編集する構成を選択します。 現在アクティブな構成は **[アクティブ] (***\<configuration>***)** と表示されます。  
  
4.  ソリューションのプロジェクトごとに、 **[プロジェクトのコンテキスト]** で、 **[ビルド]** または **[配置]** をオンまたはオフにします。  
  
    > [!NOTE]  
    >  **[ビルド]** をオンにした場合、レポート デザイナーにより、レポート プロジェクトがビルドされ、プレビュー前またはレポート サーバーにパブリッシュする前にエラーが確認されます。 **[配置]** をオンにした場合、配置プロパティで定義されている方法で、レポート デザイナーによってレポート サーバーにレポートがパブリッシュされます。 **[配置]** をオフにした場合、レポート デザイナーにより、ローカルのプレビュー ウィンドウに **[StartItem]** プロパティで指定したレポートが表示されます。  
  
## <a name="see-also"></a>参照  
 [データソースとレポートのパブリッシュ](../reports/publishing-data-sources-and-reports.md)   
 [レポートのプレビュー](../reports/previewing-reports.md)   
 [レポートデザイナーの F1 ヘルプ](report-designer-f1-help.md)   
 [SharePoint モードのレポート サーバー上のパブリッシュされたレポート アイテムの URL の例 &#40;SSRS&#41;](url-examples-for-items-on-a-report-server-sharepoint-mode.md)   
 [[プロパティ ページ] ダイアログ ボックス](project-property-pages-dialog-box.md)   
 [レポート サーバーへのレポートのパブリッシュ](../reports/publishing-reports-to-a-report-server.md)  
  
  
