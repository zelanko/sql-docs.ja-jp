---
title: PowerPivot for SharePoint のインストールを確認する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 855bd055-5ad3-493f-9c5b-1f5297b2e6e2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c4ce1b1485885719bcd31cb085d43379239612d3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66079864"
---
# <a name="verify-a-powerpivot-for-sharepoint-installation"></a>PowerPivot for SharePoint インストールの確認
  SharePoint ファームにインストールした PowerPivot for SharePoint インスタンスは、SharePoint サーバーの全体管理から管理されます。 PowerPivot のサーバー コンポーネントと機能が使用可能になっているかどうかは、少なくとも、サーバーの全体管理および SharePoint サイトのページを調べれば確認できます。 インストールを完全に確認するには、SharePoint にパブリッシュでき、ライブラリからアクセスできる PowerPivot ブックが必要になります。 テストの際には、既に PowerPivot データが含まれているサンプル ブックをパブリッシュし、それを使用して SharePoint 統合が正しく構成されているかどうかを確認できます。  
  
##  <a name="verifyinstall"></a>サーバーの全体管理統合の確認  
 PowerPivot のサーバーの全体管理との統合を確認するには、次の操作を行います。  
  
1.  [スタート] メニューの [**すべてのプログラム**] をクリックし、[Microsoft Sharepoint 2010 製品] を開いて、[ **sharepoint 2010 サーバーの全体管理**] をクリックします。  
  
2.  ユーザー名とパスワードを入力し、 **[OK]** をクリックします。  
  
     サーバーの全体管理を開くたびにユーザー名とパスワードを入力せずに済むように、ブラウザーの設定を変更することもできます。 サーバーの全体管理を信頼済みサイトとして追加するには、次の操作を行います。  
  
    1.  Internet Explorer で、[ツール] メニューの [**インターネットオプション**] をクリックします。  
  
    2.  [セキュリティ] タブの **[セキュリティ設定を表示または変更するゾーンを選択してください。]** セクションで、[信頼済みサイト] をクリックし、[サイト] をクリックします。  
  
    3.  
  **[このゾーンのサイトにはすべてサーバーの確認 (https:) を必要とする]** チェック ボックスをオフにします。  
  
    4.  
  **[次の Web サイトをゾーンに追加する]** に、サイトの URL を入力し、 **[追加]** をクリックします。  
  
    5.  [**閉じる**] をクリックし、[**OK**] をクリックします。  
  
        > [!NOTE]  
        >  SharePoint のインストールに関するドキュメントには、プロキシ サーバーのエラーを解決する手順や、更新プログラムをダウンロードしてインストールできるように Internet Explorer セキュリティ強化の構成を無効にする手順も示されています。 詳細については、Microsoft Web サイトの「 **SQL Server を使用する単一サーバーを展開する (SharePoint Server 2010)** 」の「 [追加のタスクの実行](https://go.microsoft.com/fwlink/?LinkId=177754) 」を参照してください。  
  
3.  サーバーの全体管理で、[システム設定] の **[ファーム機能の管理]** をクリックします。  
  
4.  
  **[PowerPivot 統合機能]** が **[アクティブ]** になっていることを確認します。  
  
5.  サーバーの全体管理で、[システム設定] の [**サーバーのサービスの管理**] をクリックします。  
  
6.  
  **SQL Server Analysis Services** と **SQL Server PowerPivot System サービス** が開始されていることを確認します。  
  
7.  サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]** をクリックします。  
  
8.  [**既定の Powerpivot サービスアプリケーション**] をクリックして、このアプリケーションの Powerpivot 管理ダッシュボードを開きます。 最初に使用するときは、ダッシュボードの読み込みに数分かかります。  
  
     または、[**既定の PowerPivot サービスアプリケーション**] の横にある空白部分をクリックして行を選択し、[**プロパティ**] をクリックして、このサービスアプリケーションの構成設定を表示します。 構成設定とアプリケーション プロパティの両方を修正して、サーバーの構成を変更できます。 これらの設定の詳細については、「[サーバーの全体管理での PowerPivot サービスアプリケーションの作成と構成](../../power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md)」を参照してください。  
  
## <a name="verify-integration-at-the-site-level"></a>サイト レベルでの統合の確認  
 PowerPivot の SharePoint サイトとの統合を確認するには、次の操作を行います。  
  
1.  ブラウザーで、作成した Web アプリケーションを開きます。 既定値を使用した場合は、URL\<アドレスに> コンピューター名を指定できます。  
  
2.  PowerPivot データ アクセス機能と PowerPivot データ処理機能がアプリケーションで使用可能になっていることを確認します。 そのためには、PowerPivot によって提供されるライブラリ テンプレートがあるかどうかを確認します。  
  
    1.  [サイトの操作] の [**その他のオプション**] をクリックします。  
  
    2.  ライブラリでは、[**データフィードライブラリ**] と [ **PowerPivot ギャラリー**] が表示されます。 これらのライブラリ テンプレートは PowerPivot 機能によって提供されるものであり、PowerPivot 機能が正しく統合されている場合に [ライブラリ] に表示されます。  
  
## <a name="verify-data-access-on-the-server"></a>サーバーでのデータ アクセスの確認  
 サーバーで PowerPivot データ アクセスを確認するには、次の操作を行います。  
  
1.  Reporting Services チュートリアルに付属しているピクニックデータサンプルを[ダウンロード](https://go.microsoft.com/fwlink/?LinkID=219108)します。 このダウンロードに含まれるサンプル ブックを使用して、PowerPivot データのアクセスを確認します。 ファイルを解凍します。  
  
2.  Excel ブック (.xlsx) を Shared Documents にアップロードします。 ブックに埋め込み PowerPivot データが含まれます。  
  
3.  ドキュメントをクリックしてライブラリから開きます。  
  
4.  ブックの上部にあるスライサーまたはフィルターをクリックします。 このブックのスライサーは、月、色、および種類です。 スライサーをクリックすると PowerPivot クエリが開始され、サーバーが動作することを確認できます。 サーバーは PowerPivot データをバックグラウンドで読み込んで結果を返します。  
  
5.  ライブラリに戻ります。 ブックの右側にある下矢印を選択して、 **[Power View の起動]** をクリックします。 この手順により、Reporting Services で [!INCLUDE[ssCrescent](../../../includes/sscrescent-md.md)] 機能が動作することを確認します。 Reporting Services をインストールしていない場合は、この手順は省略します。  
  
     次の手順で、Management Studio のサーバーに接続して、データの読み込みとキャッシュが行われたことを確認します。  
  
6.  [スタート] メニューの [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] プログラム グループから SQL Server Management Studio を起動します。 このツールがサーバーにインストールされていない場合は、以降の手順はスキップし、最後の手順でキャッシュされたファイルがあるかどうかを確認します。  
  
7.  [サーバーの種類] で **[Analysis Services]** を選択します。  
  
8.  [サーバー名] に、「 ** \<サーバー名>** を入力します。ここ** \<** で、サーバー名>は PowerPivot for SharePoint インストールされているコンピューターの名前です。  
  
9. 
  **[接続]** をクリックします。 これにより、Analysis Services サーバーが使用可能であることを確認します。  
  
10. オブジェクトエクスプローラーでは、[**データベース**] をクリックして、読み込まれている PowerPivot データファイルの一覧を表示できます。  
  
11. コンピューターのファイル システムのフォルダーで、ファイルがディスクにキャッシュされているかどうかを確認します。 キャッシュされたファイルが存在していれば、配置が機能していることの確認になります。 ファイルキャッシュを表示するには、ドライブ\<>: 「」を参照してください。POWERPIVOT\OLAP\Backup\Sandboxes\Default PowerPivot サービスアプリケーションフォルダー。 キャッシュされた各データベースは、名前が一意になるように、GUID ベースの名前付け規則を使用してそれぞれのフォルダーに格納されます。  
  
  
