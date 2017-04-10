---
title: "マスター データ サービスのアップグレード | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9c3543f3-3eb9-455d-a9bf-f17e9506ad21
caps.latest.revision: 31
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 30
---
# マスター データ サービスのアップグレード
  Microsoft [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]へのアップグレードには、次のシナリオがあります。  
  
-   [データベース エンジンのアップグレードを伴わないアップグレード](../../database-engine/install-windows/upgrade-master-data-services.md#noengine)  
  
-   [データベース エンジンのアップグレードを伴うアップグレード](../../database-engine/install-windows/upgrade-master-data-services.md#engine)  
  
-   [2 台のコンピューターのシナリオでのアップグレード](../../database-engine/install-windows/upgrade-master-data-services.md#twocomputer)  
  
-   [アップグレードおよびバックアップからのデータベースの復元](../../database-engine/install-windows/upgrade-master-data-services.md#restore)  
  
> [!IMPORTANT]  
>  -   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP1 リリースから CTP2 リリースへのアップグレードはサポートされていません。  
> -   アップグレードを実行する前にデータベースをバックアップしてください。  
> -   アップグレード プロセスでは、ストアド プロシージャを再作成し、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]で使用されるテーブルをアップグレードします。 これらのコンポーネントのいずれかに加えたカスタマイズは失われる場合があります。  
> -   モデル配置パッケージは作成されたエディションの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のみで使用できます。 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] で作成されたモデル配置パッケージを [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]に配置することはできません。  
> -   Data Quality Services およびマスター データ サービスを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードした後は、以前のバージョンの Excel 用マスター データ サービス アドインは機能しなくなります。 [Microsoft ダウンロード センター](http://www.microsoft.com/en-us/download/details.aspx?id=47343)から [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] の Excel 用マスター データ サービス アドインをダウンロードできます。  
  
##  <a name="fileLocation"></a> ファイルの場所  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、既定で、ファイルが *drive*:\Program Files\Microsoft SQL Server\130\Master Data Services にインストールされます。  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] では、既定で、ファイルが *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services にインストールされます。  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、既定で、ファイルが *drive*:\Program Files\Microsoft SQL Server\110\Master Data Services にインストールされます。  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] では、既定で、ファイルが *drive*:\Program Files\Microsoft SQL Server\Master Data Services にインストールされます。  
  
##  <a name="noengine"></a> データベース エンジンのアップグレードを伴わないアップグレード  
 このシナリオでは、引き続き [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] を使用して、MDS データベースをホストします。 ただし、MDS データベースのスキーマをアップグレードしてから、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web アプリケーションを作成して MDS データベースにアクセスする必要があります。 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web アプリケーションからは、MDS データベースにアクセスできなくなります。  
  
 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] と以前のバージョンの SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) を同じコンピューターにインストールできます。 ファイルは、 [ファイルの場所](#fileLocation)に示すように、異なる場所にインストールされます。  
  
 **データベース エンジンをアップグレードしないでアップグレードするには**  
  
1.  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] とその他の必要な機能をインストールします。  
  
    1.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] セットアップ ウィザードを開きます。  
  
    2.  左ペインで、 **[インストール]**をクリックします。  
  
    3.  右ペインで、**[SQL Server の新規スタンドアロン インストールを実行するか、既存のインストールに機能を追加]** をクリックします。  
  
    4.  **[機能の選択]** ページで、 **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** とその他にインストールする機能を選択します。  
  
    5.  ウィザードを完了します。  
  
2.  MDS データベース スキーマをアップグレードします。  
  
    1.  [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] バージョンの [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]を開きます。  
  
        > [!IMPORTANT]  
        >  MDS データベース スキーマをアップグレードするには、MDS データベースの作成時に指定した管理者アカウントでログインする必要があります。 MDS データベースの mdm.tblUser で、このユーザーは **1** の **ID**値を持ちます。  
  
    2.  左ペインで **[データベース構成]**をクリックします。  
  
    3.  右ペインで、 **[データベースの選択]** をクリックし、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] のデータベース インスタンスの情報を指定します。  
  
    4.  **[データベースのアップグレード]** をクリックして、 **データベースのアップグレード ウィザード**を起動します。 詳細については、「[データベースのアップグレード ウィザード  &#40;Master Data Services 構成マネージャー&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md)」を参照してください。  
  
3.  Web アプリケーションを作成します。  
  
    1.  [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] バージョンの [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]を開きます。  
  
    2.  左ペインで **[Web の構成]**をクリックします。  
  
    3.  右ペインで、 **[Web サイト]** ボックスの一覧から次のいずれかのオプションを選択します。  
  
        -   **[既定の Web サイト]**。その後、 **[アプリケーションの作成]**をクリックします。  
  
        -   **[新しいサイトの作成]**。 Web サイトを作成すると、新しい Web アプリケーションが自動的に作成されます。  
  
        > [!IMPORTANT]  
        >  以前のバージョンの SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) から取得した既存の MDS Web アプリケーションを、マスター データ サービス構成マネージャーの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンで選択できます。 既存の Web アプリケーションを選択することはできません。代わりに MDS に対応する [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] Web アプリケーションを作成する必要があります。 それ以外の場合は、アップグレード後の MDS データベースに Web アプリケーションを関連付けようとすると、ページに関連付けられた構成データが無効であるため、要求したページにアクセスできないことを示すエラーが返されます。  
        >   
        >  既存の ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) Web アプリケーションと同じ名前 (別名) を、MDS Web アプリケーションに使用する場合は、まず Web アプリケーションおよびそれに関連付けられているアプリケーション プールを IIS から削除し、次にマスター データ サービス構成マネージャーの [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] バージョンを使用して同じ名前の Web アプリケーションを作成します。 Web アプリケーションとアプリケーション プールを IIS から削除する方法については、「[Remove an Application (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=323537)」 (アプリケーションを削除する (IIS 7))、および「[Remove an Application Pool (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=323538) 」(アプリケーション プールを削除する (IIS 7)) を参照してください。  
  
4.  新しい Web アプリケーションをアップグレード後の MDS データベースに関連付けます。  
  
    1.  **[アプリケーションとデータベースの関連付け]** セクションで、 **[選択]**をクリックします。  
  
    2.  MDS データベースを選択します。  
  
    3.  **[適用]**をクリックします。  
  
##  <a name="engine"></a> データベース エンジンのアップグレードを伴うアップグレード  
 このシナリオでは、データベース エンジンと [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] アプリケーションの両方を、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]にアップグレードします。  
  
 **データベース エンジンをアップグレードしてアップグレードするには**  
  
1.  **[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] の場合のみ**: **[コントロール パネル]** > **[プログラムと機能]** の順に開き、Microsoft [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] をアンインストールします。  
  
2.  データベース エンジンを [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] にアップグレードします。 詳細については、「 [Choose a Database Engine Upgrade Method](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md)」を参照してください。  
  
3.  「 [データベース エンジンのアップグレードを伴わないアップグレード](#noengine) 」のすべての手順を完了します。  
  
##  <a name="twocomputer"></a> 2 台のコンピューターのシナリオでのアップグレード  
 このシナリオでは、SQL Server が 2 台のコンピューターにインストールされているシステムをアップグレードします。1 台は [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]、もう 1 台は [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]がインストールされています。  
  
 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] がインストールされている場合は、引き続き [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] を使用して、1 台のコンピューターで MDS データベースをホストします。 ただし、MDS データベースのスキーマをアップグレードしてから、 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] Web アプリケーションを使用して MDS データベースにアクセスする必要があります。 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web アプリケーションからは、MDS データベースにアクセスできなくなります。  
  
 **2 台のコンピューターのシナリオでアップグレードするには**  
  
-   「 [データベース エンジンのアップグレードを伴わないアップグレード](#noengine)」のすべての手順を完了します。  
  
##  <a name="restore"></a> アップグレードおよびバックアップからのデータベースの復元  
 このシナリオでは、1 台の同じコンピューターまたは 2 台の異なるコンピューターに、 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] が、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] と共にインストールされています。 アップグレードの前に、 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] リリースより前のバージョンでデータベースがバックアップされており、そのデータベースを復元する必要があります。  
  
 **バックアップからのデータベースを復元してアップグレードするには**  
  
1.  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] とその他の必要な機能をインストールします。  
  
    1.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] セットアップ ウィザードを開きます。  
  
    2.  左ペインで、 **[インストール]**をクリックします。  
  
    3.  右ペインで、**[SQL Server の新規スタンドアロン インストールを実行するか、既存のインストールに機能を追加]** をクリックします。  
  
    4.  **[機能の選択]** ページで、 **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** とその他にインストールする機能を選択します。  
  
    5.  ウィザードを完了します。  
  
2.  バックアップされたデータベースを復元します。  
  
3.  MDS データベース スキーマをアップグレートして、Web アプリケーションを作成し、新しい Web アプリケーションとアップグレードされた MDS データベースを関連付けます。 手順については、「[データベース エンジンのアップグレードを伴わないアップグレード](#noengine)」の手順 2 ～ 4 を参照してください。  
  
## トラブルシューティング  
 **問題:**  [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)][!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションを開くと、“クライアントのバージョンが、データベースのバージョンと互換性がない” ことを示すエラー メッセージが表示される。  
  
 **解決方法:** この問題は、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] のマスター データ マネージャー Web アプリケーションが [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] マスター データ サービスにアップグレードされたデータベースにアクセスしようとするときに発生します。 代わりに、 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] Web アプリケーションを使用する必要があります。  
  
 この問題はまた、MDS データベース スキーマをアップグレードするときに、IIS で **MDS アプリケーション プール** を停止および再起動しなかった場合にも発生する可能性があります。 その場合は、 **MDS アプリケーション プール** を再起動して問題を解決します。  
  
## 参照  
 [マスター データ サービスのインストール](../../master-data-services/install-windows/install-master-data-services.md)  
  
  