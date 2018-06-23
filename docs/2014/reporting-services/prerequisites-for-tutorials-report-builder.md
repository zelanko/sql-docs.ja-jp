---
title: チュートリアルの前提条件 (レポート ビルダー) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b8346a6-f4f4-4ad3-bc98-8f2be342ef2d
caps.latest.revision: 8
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 5326d5e91521e90f7596e3dd0647cb273078fd82
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177922"
---
# <a name="prerequisites-for-tutorials-report-builder"></a>チュートリアルの前提条件 (レポート ビルダー)
  レポート ビルダー チュートリアルでは、レポート サーバー上またはレポート サーバーと統合されている SharePoint サイト上でレポートを表示および保存できることを前提としています。 すべてのチュートリアルでは、データを取得するために、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]のインスタンスで処理される必要があるリテラル クエリを使用します。  
  
 レポート サーバーやサイト、またはデータ ソースにアクセスできない場合は、オフラインのレポートを作成することによってレポート ビルダーについて学習できます。 「[チュートリアル: オフラインでのクイック グラフ レポートの作成 &#40;レポート ビルダー&#41;](report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md)」を参照してください。  
  
## <a name="requirements"></a>要件  
 レポート ビルダーのチュートリアルを完了するには、次の条件を満たしている必要があります。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] レポート ビルダーへのアクセス。 レポート ビルダーを実行するには、スタンドアロン バージョンまたは ClickOnce バージョンのレポート ビルダーを使用します。ClickOnce バージョンは、レポート マネージャーまたは SharePoint サイトから利用できます。 最初の手順のみをレポート ビルダーを開く方法は ClickOnce バージョン。  
  
     レポート マネージャーを使用する レポート マネージャーを開き、をクリックして**レポート ビルダー**です。 既定では、レポート マネージャーの URL は http://\<*servername*>/reports です。  
  
     SharePoint サイトを使用する場合は、サイトに移動し、[ドキュメント] タブ、[新しいドキュメント] の順にクリックして、ドロップダウン リストの [レポート ビルダー レポート] をクリックします。 たとえば、http://\<servername >/サイト/mySite/レポートします。 SharePoint 管理者は、各ドキュメント ライブラリのレポート ビルダー レポート機能を有効にする必要があります。  
  
-   URL、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]レポート サーバーまたは SharePoint サイトと統合された、[!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]レポート サーバー。 レポート、共有データ ソース、共有データセット、レポート パーツ、およびモデルを保存および表示する権限が必要です。 既定では、レポート サーバーの URL は http://\<servername >/reportserver です。 既定では、SharePoint サイトの URL は http://\<sitename > または http://\<サーバー >]、[サイトです。  
  
-   名前、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]インスタンスと任意のデータベースに読み取り専用アクセスのための十分な資格情報。 チュートリアルのデータセット クエリでは、リテラル データを使用します。ただし、各クエリは、レポート データセットに必要なメタデータを返すように、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] インスタンスで処理される必要があります。 たとえば、`data source=<servername>` という接続文字列では、サーバーしか指定されていません。 この場合は、そのサーバーにアクセスする権限を付与したシステム管理者によって割り当てられた既定のデータベースに対する読み取りアクセス権が必要です。 `data source=<servername>;initial catalog=<database>`という接続文字列のように、データベースを指定することもできます。  
  
-   マップを含むチュートリアルの場合は、Bing マップの背景をサポートするようにレポート サーバーが構成されている必要があります。 詳細については、次を参照してください。[マップ レポートのサポートの計画](plan-for-map-report-support.md)で[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]ドキュメント[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][オンライン ブック](http://go.microsoft.com/fwlink/?LinkId=154888)msdn.microsoft.com の「します。  
  
-   このチュートリアルでは、[チュートリアル: を作成する詳細レポートとメイン レポート&#40;レポート ビルダー&#41;](tutorial-creating-drillthrough-and-main-reports-report-builder.md)、Contoso ビジネス インテリジェンス デモ データセットを使用します。 このデータセットは、ContosoDW データ ウェアハウスと Contoso_Retail オンライン分析処理 (OLAP) データベースで構成されています。 このチュートリアルで作成するレポートは、Contoso Sales キューブからレポート データを取得します。 Contoso_Retail OLAP データベースは、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=191575)からダウンロードできます。 ダウンロードする必要があるファイルは、ContosoBIdemoABF.exe だけです。 このファイルに OLAP データベースが含まれています。  
  
     もう一方のファイル (ContosoBIdemoBAK.exe) は、ContosoDW データ ウェアハウスのファイルです。ContosoDW データ ウェアハウスは、このチュートリアルでは使用しません。  
  
     上述の Web サイトには、ContosoRetail.abf バックアップ ファイルを抽出して Contoso_Retail OLAP データベースを復元する手順の説明も含まれています。  
  
     OLAP データベースをインストールする [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスへのアクセス権が必要です。  
  
 レポート サーバー管理者が与える必要がある、レポート サーバーに必要なアクセス許可を構成する[!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]フォルダーの場所、およびレポート ビルダーの既定のオプションを構成します。 詳細については、次を参照してください。[インストール、アンインストール、およびレポート ビルダーのサポート](install-uninstall-and-report-builder-support.md)です。  
  
## <a name="see-also"></a>参照  
 [チュートリアル&#40;レポート ビルダー&#41;](report-builder-tutorials.md)  
  
  