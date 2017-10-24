---
title: "Analysis Services のインストール |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 04/11/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd6ac80d-b735-4e3e-a024-489f1409ad33
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 084223d83c3786610dbce145f27a4c18a6409769
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="install-sql-server-analysis-services"></a>SQL Server Analysis Services をインストールします。
  SQL Server Analysis Services は、表形式モデル、多次元キューブ、およびレポート、スプレッドシート、およびダッシュ_ボードからアクセスできるデータ マイニング モデルをホストする分析データベース サーバーです。  
  
 Analysis Services は、複数のインスタンスが 1 台のコンピューターに複数のコピーをインストールまたは新しいバージョンと古いバージョンを同時に実行できます。 インストールしたすべてのインスタンスは、セットアップ時に決定される 3 つのモード: 多次元およびデータ マイニング、表形式、または SharePoint のいずれかで実行されます。 複数のモードを使用する場合は、それぞれに個別のインスタンスが必要です。  
  
 特定のモードでサーバーをインストールすると、そのモードに準拠しているホスト ソリューションを使用できます。 たとえば、ネットワーク上で表形式モデルのデータにアクセスする場合は、表形式モードのサーバーが必要です。  
  
## <a name="get-tools-and-designers"></a>ツールとデザイナーの取得  
 SQL Server セットアップでは、ソリューション デザインまたはサーバー管理に使用されるモデル デザイナーまたは管理ツールがインストールされなくなりました。 このリリースでは、ツールには次のリンクから入手できる個別のインストールが用意されています。  
  
-   [SQL Server Management Studio (SSMS) のダウンロード](../../../ssms/download-sql-server-management-studio-ssms.md)  
  
-   [SQL Server Data Tools (SSDT) のダウンロード](../../../ssdt/download-sql-server-data-tools-ssdt.md)  
  
 SSMS および SSDT が Analysis Services インスタンスとデータを操作する必要があります。 ツールは、どこにでもインストールできますが、接続を試行する前に、サーバー上のポートを構成することを確認します。 詳細については、「 [Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) 」を参照してください。  
  
## <a name="install-using-a-wizard"></a>ウィザードを使用したインストール  
 Analysis Services をインストールする場合に使用する SQL Server インストール ウィザードのページを次の一覧に示します。  
  
1.  セットアップの機能ツリーで **[Analysis Services]** をクリックします。  
  
     ![セットアップの機能ツリーを示す Analsyis Services](../../../analysis-services/instances/install-windows/media/ssas-setupas.gif "Analsyis Services を示すセットアップの機能ツリー")  
  
2.  Analysis Services の構成 ページで、モードを選択します。 表形式モードでは、既定値です。  
  
     ![Analysis Services 構成オプションのセットアップ ページ](../../../analysis-services/instances/install-windows/media/ssas-setupasconfig.png "Analysis Services 構成オプションのセットアップ ページ")  
  
  表形式モードでは、表形式モデルの既定のストレージです、xVelocity メモリ内分析エンジン (VertiPaq) を使用します。 サーバーに表形式モデルを配置した後は、メモリ バインド ストレージする代わりに DirectQuery ディスク ストレージを使用する表形式ソリューションを選択的に構成できます。  
 
 多次元およびデータ マイニング モードとして使用する MOLAP、既定のストレージの Analysis Services に配置されたモデルです。 サーバーへの展開後、Analysis Services 多次元データベースにクエリ データを格納する代わりに、リレーショナル データベースに対してクエリを直接実行する場合は、ROLAP を使用するようにソリューションを構成できます。  
  

  
 既定以外のストレージ モードを使用する場合は、優れたパフォーマンスを実現するようにメモリ管理および IO 設定を調整できます。 詳細については、「 [Analysis Services のサーバー プロパティ](../../../analysis-services/server-properties/server-properties-in-analysis-services.md) 」をご覧ください。  
  
## <a name="command-line-setup"></a>コマンド ライン セットアップ  
 SQL Server セットアップにはサーバー モードを指定するパラメーター (**ASSERVERMODE**) があります。 次の例は、Analysis Services を表形式サーバー モードでインストールするコマンド ライン セットアップを示しています。  
  
```  
  
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /FEATURES=AS /ASSERVERMODE=TABULAR /INSTANCENAME=ASTabular /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 **INSTANCENAME** は 17 文字未満にする必要があります。  
  
 プレースホルダー アカウント値はすべて、有効なアカウントおよびパスワードに置き換える必要があります。  
  
 **ASSERVERMODE** では、大文字と小文字が区別されます。  値はすべて大文字で指定する必要があります。 次の表に、 **ASSERVERMODE**の有効な値を示します。  
  
|値|説明|  
|-----------|-----------------|  
|TABULAR|これが既定値です。 設定しない場合**ASSERVERMODE**、表形式モードでは、サーバーをインストールします。|
|MULTIDIMENSIONAL|この値は省略可能です。|  
|POWERPIVOT|この値は省略可能です。 実際には、 **ROLE** パラメーターを設定した場合、サーバー モードは自動的に 1 に設定され、SharePoint のインストール時に **の** ASSERVERMODE [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] が省略可能になります。 詳細については、「 [コマンド プロンプトからの Power Pivot のインストール](http://msdn.microsoft.com/en-us/7f1f2b28-c9f5-49ad-934b-02f2fa6b9328)」を参照してください。|  
  
  
## <a name="see-also"></a>参照  
 [Analysis Services インスタンスのサーバー モードの決定](../../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [テーブル モデリング (SSAS テーブル)](https://msdn.microsoft.com/library/hh212945(v=sql.110).aspx)  
  
  

