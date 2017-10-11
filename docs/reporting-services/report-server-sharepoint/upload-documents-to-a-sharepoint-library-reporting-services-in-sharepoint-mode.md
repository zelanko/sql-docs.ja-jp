---
title: "ドキュメントを SharePoint ライブラリに追加する (Reporting Services の SharePoint モード) にアップロード |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/25/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: d938f068ecf2d0c2a2b920fda9f7c414649f069d
ms.contentlocale: ja-jp
ms.lasthandoff: 10/06/2017

---
# <a name="upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode"></a>ドキュメントを SharePoint ライブラリに追加する (Reporting Services の SharePoint モード) にアップロードします。

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

レポート定義やレポート モデルを SharePoint ライブラリにアップロードすることができます。 レポート サーバー アイテムをアップロードするときには、ライブラリまたはライブラリ内のフォルダーを選択する必要があります。 レポート サーバー アイテムを一覧やページにアップロードすることはできません。  

> [!NOTE]
> SQL Server 2016 より後に、SharePoint と reporting Services の統合を使用できなくします。

 データ ソース (.rds) ファイルをアップロードすることはできません。 ただし、.rds ファイルをデザイン ツール (レポート デザイナーなど) から SharePoint ライブラリにパブリッシュすることはできます。 パブリッシュ時に、ソリューション内の元の .rds ファイルから新しい .rsds ファイルが作成されます。 SharePoint ライブラリに新しい .rsds ファイルを作成して、その新しい接続が使用されるように、アップロードしたレポートやモデルのデータ ソース接続プロパティを設定することもできます。  
  
> [!NOTE]  
>  SharePoint モードのレポート サーバーを構成する必要があり、SharePoint 製品のインスタンスが Reporting Services アドインをプログラム ファイルを格納して、SharePoint サイトからレポート サーバー アイテムへのアクセスを提供する必要があります。  
  
 ドキュメントをライブラリにアップロードするには、サイト レベルの "アイテムの追加" 権限が必要です。 既定のセキュリティ設定を使用している場合、この権限は、フル コントロール レベルの権限を持つ **所有者** グループおよび投稿レベルの権限を持つ **メンバー** グループのメンバーに与えられます。  
  
## <a name="add-a-report-definition-or-report-model-to-a-library"></a>ライブラリにレポート定義またはレポート モデルを追加します。
  
1.  ライブラリまたはライブラリ内のフォルダーを開きます。 まだライブラリが開いていない場合は、サイド リンク バーでライブラリの名前をクリックします。 ライブラリの名前が表示されていない場合は、 **[すべてのサイト コンテンツの表示]**をクリックし、ライブラリの名前をクリックします。  
  
2.  **[アップロード]** メニューの **[ドキュメントのアップロード]**をクリックします。  
  
3.  1 つのレポート ファイルまたはレポート モデル ファイルをアップロードするには、レポート定義 (.rdl) ファイルまたはレポート モデル (.smdl) ファイルを選択し、 **[OK]**をクリックします。  
  
     レポート定義で共有データ ソース (.rsds) ファイルを使用して接続情報を外部データ ソースに格納している場合は、.rdl ファイルと .rsds ファイルを同時にアップロードできます。 これには、 **[複数のドキュメントのアップロード]**をクリックし、両方のファイルを指定して、 **[OK]**をクリックします。  
  
 共有データ ソース、レポート モデル、またはサブレポートへの参照が含まれているレポートをアップロードすると、ファイルのアップロード時にレポート内で参照が破損します。 参照をリセットする方法の詳細については、次を参照してください。[作成および共有データ ソースの管理 & #40 です。Reporting Services の SharePoint モード &#41; と統合](http://msdn.microsoft.com/library/2d3428e4-a810-4e66-a287-ff18e57fad76).  
  
 レポートをアップロードした場合は、そのレポートを開くとレポートがオンデマンドで実行されて、データ ソースからライブ データが取得されます。 スケジュールに基づいたデータ取得や、キャッシュされたデータの使用が行われるようにレポートを構成することもできます。 詳細については、次を参照してください。[処理オプションの設定 & #40 です。Reporting Services の SharePoint モード &#41; と統合](../../reporting-services/report-server-sharepoint/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md).  
  
 レポートにパラメーターを含めると、ユーザーがデータをフィルター選択できるようになります。 パラメーターは、特定の値を使用するように構成したり、表示方法を変更したりすることができます。 詳細については、次を参照してください。 [パラメーターの設定でパブリッシュされたレポートと #40 です。Reporting Services の SharePoint モード &#41; と統合](../../reporting-services/report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).  
  
## <a name="see-also"></a>参照

 [SharePoint ライブラリへのレポートのパブリッシュ](../../reporting-services/reports/publish-a-report-to-a-sharepoint-library.md)   
 [SharePoint ライブラリに共有データ ソースをパブリッシュします。](../../reporting-services/reports/publish-a-shared-data-source-to-a-sharepoint-library.md)   
 [SharePoint サイトのレポート サーバー アイテムに対する権限の付与](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)
