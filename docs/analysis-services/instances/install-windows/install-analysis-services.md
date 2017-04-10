---
title: "Analysis Services のインストール | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cd6ac80d-b735-4e3e-a024-489f1409ad33
caps.latest.revision: 20
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 19
---
# Analysis Services のインストール
  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は、レポート、スプレッドシート、およびダッシュ ボードからアクセスできる、そのホストの表形式モデル、多次元キューブ、およびデータ マイニング モデルをホストする分析データベース サーバーです。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は複数インスタンスです。つまり、1 台のコンピューターに [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] の複数のコピーをインストールしたり、新旧のバージョンを並列に実行したりできます。 インストールしたすべてのインスタンスは、セットアップ時に決定される 3 つのモード: 多次元およびデータ マイニング、表形式、または SharePoint のいずれかで実行されます。 複数のモードを使用する場合は、それぞれに個別のインスタンスが必要です。  
  
 特定のモードでサーバーをインストールすると、そのモードに準拠しているホスト ソリューションを使用できます。 たとえば、ネットワーク上で表形式モデルのデータにアクセスする場合は、表形式モードのサーバーが必要です。  
  
## ツールとデザイナーの取得  
 SQL Server セットアップでは、ソリューション デザインまたはサーバー管理に使用されるモデル デザイナーまたは管理ツールがインストールされなくなりました。 このリリースでは、ツールには次のリンクから入手できる個別のインストールが用意されています。  
  
-   [SQL Server Management Studio for SQL Server 2016 のダウンロード](https://msdn.microsoft.com/en-US/library/mt238290.aspx)  
  
-   [SQL Server Data Tools for SQL Server 2016 のダウンロード](https://msdn.microsoft.com/en-US/library/mt204009.aspx)  
  
 Analysis Services インスタンスおよびデータを操作するには、Management Studio と SQL Server Data Tools の両方が必要です。 ツールは任意の場所にインストールできますが、接続を試行する前に、サーバーでポートを構成してください。 詳細については、「 [Configure the Windows Firewall to Allow Analysis Services Access](../../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) 」を参照してください。  
  
## ウィザードを使用したインストール  
 Analysis Services をインストールする場合に使用する SQL Server インストール ウィザードのページを次の一覧に示します。  
  
1.  セットアップの機能ツリーで **[Analysis Services]** をクリックします。  
  
     ![Setup feature tree showing Analsyis Services](../../../analysis-services/instances/install-windows/media/ssas-setupas.gif "Setup feature tree showing Analsyis Services")  
  
2.  表形式のインスタンスが必要な場合は、[Analysis Services の構成] ページで **[表形式モード]** を選択します。 それ以外の場合、既定値は **[多次元およびデータ マイニング モード]**になります。  
  
     ![Setup page with Analysis Services config options](../../../analysis-services/instances/install-windows/media/ssas-setupasconfig.png "Setup page with Analysis Services config options")  
  
 多次元およびデータ マイニング モードでは、Analysis Services に配置されたモデルの既定のストレージとして MOLAP が使用されます。 サーバーへの展開後、Analysis Services 多次元データベースにクエリ データを格納する代わりに、リレーショナル データベースに対してクエリを直接実行する場合は、ROLAP を使用するようにソリューションを構成できます。  
  
 表形式モードでは xVelocity メモリ内分析エンジン (VertiPaq) を使用します。このエンジンは Analysis Services に配置するテーブル モデルの既定のストレージです。 サーバーにテーブル モデル ソリューションを配置すると、表形式ソリューションを構成する際に、メモリ負荷の高いストレージの代わりに DirectQuery ディスク ストレージを使用することもできます。  
  
 既定以外のストレージ モードを使用する場合は、優れたパフォーマンスを実現するようにメモリ管理および IO 設定を調整できます。 詳細については、「[Analysis Services のサーバー プロパティ](../../../analysis-services/server-properties/server-properties-in-analysis-services.md) 」をご覧ください。  
  
## コマンド ライン セットアップ  
 SQL Server セットアップにはサーバー モードを指定するパラメーター (**ASSERVERMODE**) があります。 次の例は、Analysis Services を表形式サーバー モードでインストールするコマンド ライン セットアップを示しています。  
  
```  
  
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /FEATURES=AS /ASSERVERMODE=TABULAR /INSTANCENAME=ASTabular /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 **INSTANCENAME** は 17 文字未満にする必要があります。  
  
 プレースホルダー アカウント値はすべて、有効なアカウントおよびパスワードに置き換える必要があります。  
  
 **ASSERVERMODE** では、大文字と小文字が区別されます。  値はすべて大文字で指定する必要があります。 次の表に、 **ASSERVERMODE**の有効な値を示します。  
  
|値|説明|  
|-----------|-----------------|  
|MULTIDIMENSIONAL|これが既定値です。 **ASSERVERMODE**を設定しない場合、サーバーは多次元サーバー モードでインストールされます。|  
|POWERPIVOT|この値は省略可能です。 実際には、**ROLE** パラメーターを設定した場合、サーバー モードは自動的に 1 に設定され、SharePoint のインストール時に [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] の **ASSERVERMODE** が省略可能になります。 詳細については、「 [コマンド プロンプトからの Power Pivot のインストール](http://msdn.microsoft.com/ja-jp/7f1f2b28-c9f5-49ad-934b-02f2fa6b9328)」を参照してください。|  
|TABULAR|コマンド ライン セットアップを使用して Analysis Services を表形式モードでインストールする場合、この値は必須です。|  
  
## 参照  
 [Analysis Services インスタンスのサーバー モードの決定](../../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [メモリ内の表形式データベースを SQL Server Management Studio &#40;SSMS&#41; での DirectQuery に変換する](../Topic/Convert%20an%20in-memory%20Tabular%20Database%20to%20DirectQuery%20in%20SQL%20Server%20Management%20Studio%20\(SSMS\).md)   
 [テーブル モデリング &#40;SSAS&#41;](../Topic/Tabular%20Modeling%20\(SSAS\).md)  
  
  