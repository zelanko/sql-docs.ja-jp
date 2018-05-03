---
title: Power Pivot BI セマンティック モデル接続 (.bism) |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ppvt-sharepoint
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f6387089a7950716121254c265b33e28504fa9bc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="power-pivot-bi-semantic-model-connection-bism"></a>Power Pivot BI セマンティック モデル接続 (.bism)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  BI セマンティック モデル接続 (.bism) は、Excel または Power View レポートを Analysis Services テーブル モデル データベースまたは多次元モードの Analysis Services インスタンスに接続する、移植可能な接続です。 Office データ接続 (.odc) ファイルに精通している場合は、.bism 接続ファイルの定義方法と使用方法が類似していることがわかります。  
  
 BI セマンティック モデル接続は、SharePoint 経由で作成およびアクセスされます。 BI セマンティック モデル接続を作成すると、ライブラリの BI セマンティック モデル接続でサイド リンク バー コマンドが有効になります。 サイド リンク バー コマンドは、新しい Excel ブックまたは接続ファイルを編集するためのオプションを開きます。 Reporting Services がインストールされている場合は、 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] レポートを作成するためのコマンドも表示されます。  
  
 ![スクリーン ショットの BISM サイド リンク バー コマンド](../../analysis-services/power-pivot-sharepoint/media/ssas-bism-quicklaunch.gif "スクリーン ショットの BISM サイド リンク バー コマンド")  
  
##  <a name="bkmk_prereq"></a> サポートされるデータベース  
 BI セマンティック モデル接続は、テーブル モデル データを参照します。 このデータには、次の 3 つのソースがあります。  
  
-   表形式サーバー モードのスタンドアロン Analysis Services インスタンスで実行されている表形式モデル データベース。 スタンドアロン Analysis Services インスタンスは、ファーム外部に配置されます。 ファーム外部のデータ ソースにアクセスするには、追加の権限が必要です。追加の権限については、「 [テーブル モデル データベースへの BI セマンティック モデル接続の作成](../../analysis-services/power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)」を参照してください。  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブック。 Excel ブックに埋め込まれた [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データベースが、スタンドアロン Analysis Services 表形式モード サーバーで実行されるテーブル モデル データベースに相当します。 既に [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel と [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint を使用している場合は、SharePoint ライブラリ内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックを参照する BI セマンティック モデル接続を定義し、既存の [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] データを使用して [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] レポートを作成できます。  SQL Server 2008 R2 または [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] バージョンの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel で作成されたブックを使用できます。  
  
-   Analysis Services インスタンス上の多次元データ モデル。  
  
 データ ソースの比較については、コミュニティ コンテンツ「 [Understanding the SQL Server 2012 BI Semantic Model (BISM)](http://www.mssqltips.com/sqlservertip/2818/understanding-the-sql-server-2012-bi-semantic-model-bism/)」 (SQL Server 2012 BI セマンティック モデル (BISM) について) を参照してください。  
  
## <a name="understanding-the-connection-sequence-for-bi-semantic-connections"></a>BI セマンティック接続の接続シーケンスについて  
 このセクションでは、さまざまなクライアント アプリケーション (Excel デスクトップ アプリケーション、SharePoint の Power View レポート クライアントなど) と SharePoint ファーム内または外のテーブル モデル データベースとの接続動作について説明します。  
  
 テーブル モデル データベースへのすべての接続は、データを要求しているユーザーの資格情報を使用して作成されます。 ただし、その接続のしくみは、接続がファーム内接続、シングルホップ接続、ダブルホップ接続のいずれであるかと、Kerberos が有効かどうかによって異なります。 SharePoint とバックエンド データ ソースとの認証接続の詳細については、「 [ダブルホップ認証: NTLM では失敗し、Kerberos では成功する理由](http://go.microsoft.com/fwlink/?LinkId=237137)」を参照してください。  
  
 **Excel からネットワーク上の表形式データへの接続**  
  
 Excel ユーザーがデータ ソースとして BI セマンティック モデル接続を指定すると、.bism ファイル内の接続情報がクライアント アプリケーションにダウンロードされ、そのアプリケーションが Analysis Services 上のテーブル モデル データベースに独自の直接要求を発行します。 .bism 接続にアクセスするには、Excel ユーザーは .bism 接続ファイルに対する読み取り権限を持つ SharePoint ユーザーである必要があります。 接続情報がダウンロードされると、その後のすべての接続は SharePoint をバイパスし、Excel からバックエンド テーブル モデル データベースに直接送られるようになります。  
  
 次の図は、この接続シーケンスを示しています。 .bism 接続の要求で始まり、クライアントに接続情報がダウンロードされて、最後にデータベースへのシングルホップ接続が行われます。 接続は、Analysis Services データベースに対する読み取り権限を持つ Excel ユーザーの Windows 資格情報を使用して作成されます。 シングルホップであるため、Kerberos が有効になっていても、このシナリオでは必要とされません。  
  
 ![Excel からテーブル モデル データベースへの接続](../../analysis-services/power-pivot-sharepoint/media/ssas-powerpivotbismconnection-1.gif "Excel からテーブル モデル データベースへの接続")  
  
 **Power View からネットワーク上の表形式データへの接続**  
  
 SharePoint ユーザーがドキュメント ライブラリ内の BI セマンティック接続をクリックすると、Power View (インストールされている場合) が直ちに起動され、テーブル モデル データベースへの接続を開きます。  
  
 Power View とテーブル モデル データベースとの接続は、ダブルホップ認証シーケンスに従って行われ、ユーザーの ID はクライアントから SharePoint に送られてから、SharePoint からファーム外で実行されるバックエンド Analysis Services テーブル モデル データベースに送られます。 接続要求を処理する ADOMD.NET クライアント ライブラリは常に、最初の試行で Kerberos を利用しようとします。 Kerberos が構成されていると、テーブル モデル データベースへの接続に対してユーザー ID の権限が借用され、接続は成功します。  
  
 Kerberos が構成されておらず、要求が失敗した場合は、Reporting Services が 2 度目の試行を行います。 このシナリオでは、クライアント ライブラリが Reporting Services のサービス ID と NTLM 認証を使用して、Analysis Services に接続します。 Power View ユーザーの ID は、 **effectiveusername** パラメーターを使用して、接続文字列で渡されます。  
  
 Analysis Services インスタンス上のシステム管理者ロールのメンバーだけが、 **effectiveusername** パラメーターを使用して接続を作成し、サーバー インスタンスの他のユーザーの権限を借用する権限を持っています。 そのため、Reporting Services 共有サービスの実行アカウントは、Analysis Services インスタンスに対する管理権限を持っている必要があります。  サービス アカウントに管理権限を付与する手順は、このトピックの「 [テーブル モデル データベースへの BI セマンティック モデル接続の作成](../../analysis-services/power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)」に示されています。  
  
 次の図は、各接続に同じ Windows ユーザー ID を使用する接続シーケンスを示しています。 Analysis Services への最後の接続では、Reporting Services サービス アプリケーション ID で接続が作成され、 **effectiveusername**を使用して Windows ユーザー ID が渡されています。  
  
 ![表形式 db に対する借用の接続](../../analysis-services/power-pivot-sharepoint/media/ssas-powerpivotbismconnection-2.gif "表形式 db に対する借用の接続")  
  
 **Power View から SharePoint の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データへの接続**  
  
 SharePoint ユーザーが、同じファーム内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックに解決される BI セマンティック接続をクリックすると、SharePoint 環境のコンテキスト内で接続が行われます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションは、接続要求を処理し、同じコンピューター上の Analysis Services インスタンスに転送します。 Analysis Services インスタンスは、ブックから [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを抽出して読み込みます。 その後のすべての接続は、ファーム内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションによって管理されます。  
  
 このシナリオでは、すべての接続が同じファーム内で行われるため、Kerberos または制約付き委任は必要とされません。  
  
##  <a name="bkmk_rel"></a> 関連タスク  
 [BI セマンティック モデル接続のコンテンツ タイプのライブラリへの追加 (Power Pivot for SharePoint)](../../analysis-services/power-pivot-sharepoint/add-bi-semantic-model-connection-content-type-to-library.md)  
  
 [Power Pivot ブックへの BI セマンティック モデル接続の作成](../../analysis-services/power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-power-pivot-workbook.md)  
  
 [テーブル モデル データベースへの BI セマンティック モデル接続の作成](../../analysis-services/power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)  
  
 [Excel または Reporting Services での BI セマンティック モデル接続の使用](../../analysis-services/power-pivot-sharepoint/use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md)  
  
## <a name="see-also"></a>参照  
 [Analysis Services インスタンスのサーバー モードの決定](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Analysis Services への接続](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  
