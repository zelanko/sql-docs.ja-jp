---
title: "Integration Services のインストール |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Integration Services, installing
- SSIS, installing
- installing Integration Services, about installing Integration Services
- SQL Server Integration Services, installing
- Setup [Integration Services], about installing Integration Services
- installing Integration Services
- Setup [Integration Services]
ms.assetid: bd20fd3a-414b-4581-959d-ebba4ddf5a55
caps.latest.revision: 106
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3e91abac8902868dc9edefc1466fb2d25a602462
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="install-integration-services"></a>Integration Services のインストール
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]を含む任意またはすべてのコンポーネントを 1 つのセットアップ プログラムでインストールできます。 セットアップによって、他の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コンポーネントと共にまたは単独で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を 1 台のコンピューターにインストールできます。    
    
 このトピックでは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]をインストールする前に知っておく必要がある重要な注意点について説明します。 このトピックの情報を参考にして各インストール オプションを評価することにより、インストール時に適切な選択を行うことができます。    
    
## <a name="preparing-to-install-integration-services"></a>Integration Services をインストールする準備    
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]をインストールする前に、次の要件を確認してください。    
    
-   [SQL Server 2016 のインストールに必要なハードウェアおよびソフトウェア](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)    
    
-   [システム構成チェッカーの検査パラメーター](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md)    
    
-   [SQL Server インストールにおけるセキュリティの考慮事項](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)    
    
## <a name="selecting-an-integration-services-configuration"></a>Integration Services の構成の選択    
 次の構成で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] をインストールできます。    
    
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の以前のインスタンスが存在しないコンピューターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をインストールできます。    
    
-   [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] は、 [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] または [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)]の既存のインスタンスとサイド バイ サイドでインストールできます。    
    
     [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] の以前のバージョンのいずれかが既にインストールされているコンピューターで [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] にアップグレードすると、 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] は以前のバージョンに対してサイド バイ サイドでインストールされます。    
    
     [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]のアップグレードの詳細については、「 [Integration Services のアップグレード](../../integration-services/install-windows/upgrade-integration-services.md)」を参照してください。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]の旧バージョンとの互換性については、「 [Integration Services の旧バージョンとの互換性](../../integration-services/integration-services-backward-compatibility.md)」を参照してください。    
    
## <a name="installing-integration-services"></a>Integration Services のインストール    
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール要件を検討し、コンピューターがそれらの要件を満たしていることを確認したら、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]のインストールの準備は完了です。    
    
> [!NOTE]    
>  以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールすると、既定で Users グループの全ユーザーが [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスにアクセスできました。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]をインストールした場合、ユーザーは [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスにアクセスできません。 このサービスは既定で保護されます。 特定のユーザーに対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Server Integration Services 13.0 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] へのアクセスを許可するには、 **管理者が**をインストールした後で DCOM 構成ツール (Dcomcnfg.exe) を実行する必要があります。    
>     
>  アクセス許可を付与する方法については、次を参照してください。 [Integration Services サービス & #40 です。SSIS サービス &#41;](../../integration-services/service/integration-services-service-ssis-service.md).    
    
 セットアップ ウィザードを使用して [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]をインストールする場合は、一連のページを使用してコンポーネントとオプションを指定します。 セットアップ ウィザードのページのうち、選択するオプションによって [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]のインストールに影響するページのみを次の表に示します。    
    
|ページ|推奨事項|    
|----------|---------------------|    
|**機能の選択**|**サービスをインストールしてデザイン環境外部でパッケージを実行するには、** [Integration Services] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] を選択します。<br /><br /> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]の完全インストール (パッケージの開発と管理に必要なツールやドキュメントを含んだインストール) を実行するには、 **[Integration Services]** と次の **[共有機能]**の両方を選択します。<br /><br /> -<br />                    **[[SQL Server Data Tools]]** : パッケージをデザインするためのツールをインストールします。<br /><br /> -<br />                    **[管理ツール - 完全]** : パッケージを管理するための [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] をインストールします。<br /><br /> -<br />                    **[クライアント ツール SDK]** : [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プログラミング用にマネージ アセンブリをインストールします。<br /><br /> 多くのデータ ウェアハウジング ソリューションでは、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  など、その他の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントもインストールする必要があります。<br /><br /> **64 ビット コンピューターでのインストール**   64 ビット コンピューターでは、**[Integration Services]** を選択すると、64 ビットのランタイムとツールのみがインストールされます。 パッケージを 32 ビット モードで実行する必要がある場合は、追加のオプションを選択して 32 ビットのランタイムとツールもインストールする必要があります。<br /><br /> -64 ビット コンピューターで x86 オペレーティング システムを実行している場合は、 **[SQL Server Data Tools]** または **[管理ツール - 完全]**を選択します。<br /><br /> -64 ビット コンピューターで [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)] オペレーティング システムを実行している場合は、 **[管理ツール - 完全]**を選択します。<br /><br /> **ETL 専用のサーバーでのインストール** ETL (抽出、変換、読み込み) プロセス専用のサーバーを使用するには、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインストール時に [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]のローカル インスタンスをインストールすることをお勧めします。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は、通常、パッケージを [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに格納し、このパッケージのスケジュールを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントに依存して設定します。 ETL サーバーに [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスが存在しない場合は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスが存在するサーバーからパッケージのスケジュール設定や実行を行う必要があります。 つまり、パッケージは、ETL サーバーではなく、パッケージが開始されたサーバーで実行されます。 その結果、専用の ETL サーバーのリソースは意図したとおりに使用されません。 さらに、他のサーバーのリソースが実行中の ETL プロセスによって使用される場合もあります。<br /><br /> <br /><br /> 注: セットアップ ウィザードの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [機能の選択] **ページでインストールの選択をした** コンポーネントによっては、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コンポーネントのサブセットの一部がインストールされます。 これらのコンポーネントを使用して一部のタスクを実行することは可能ですが、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のすべての機能は使用できません。 たとえば、 **[データベース エンジン サービス]** オプションを選択すると、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] インポートおよびエクスポート ウィザードに必要な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントがインストールされます。 **[SQL Server Data Tools]** オプションを選択すると、パッケージのデザインに必要な [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コンポーネントはインストールされますが、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスはインストールされないので、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]外でパッケージを実行することはできません。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]を完全にインストールするには、 **[機能の選択]** ページで **[Integration Services]** を選択する必要があります。|    
|**インスタンスの構成**|**[インスタンスの構成]** ページで行う選択は、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] または [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスに影響しません。<br /><br /> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスのインスタンスは 1 台のコンピューターに 1 つだけインストールできます。 サービスに接続するには、コンピューター名を使用します。<br /><br /> 既定では、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスは、 **と同時にインストールされるデータベース エンジンのインスタンスの** msdb [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]データベースに格納されているパッケージを管理するように構成されます。 データベース エンジンのインスタンスが [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]と同時にインストールされない場合、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスは、 **の既定のローカル インスタンスの** msdb [!INCLUDE[ssDE](../../includes/ssde-md.md)]データベースに格納されているパッケージを管理するように構成されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の名前付きインスタンスまたはリモート インスタンス、あるいは [!INCLUDE[ssDE](../../includes/ssde-md.md)]の複数のインスタンスに格納されているパッケージを管理するには、構成ファイルを変更する必要があります。 この構成ファイルを変更する方法の詳細については、次を参照してください。 [Integration Services サービス & #40 です。SSIS サービス &#41;](../../integration-services/service/integration-services-service-ssis-service.md).|    
|**[サーバーの構成]**|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] [サーバーの構成] **ページの** [サービス アカウント] **タブで、** サービスの設定を確認します。<br /><br /> Windows 7 または Windows Server 2008 R2 がインストールされている場合、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスは、NT Services\MsDtsServer130 にある仮想アカウントを使用して実行するように登録されており、 **[スタートアップの種類]** は **[自動]**になっています。  仮想アカウントのパスワードを入力する必要はありません。 Microsoft Vista または Windows Server 2008 がインストールされている場合、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスは、ネットワーク サービス ビルトイン アカウントを使用して実行するように登録されており、 **[スタートアップの種類]** は **[自動]**になっています。 ネットワーク サービス ビルトイン アカウントのパスワードを入力する必要はありません。|    
    
 既定では、新規インストールで、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] はパッケージの実行に関連するイベントをアプリケーション イベント ログに記録しないように構成されます。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のデータ コレクター機能を使用すると、この設定により、大量のイベント ログ エントリは生成されません。 ログに記録されないイベントは、EventID 12288 の "パッケージが起動されました。" や EventID 12289 の "パッケージが正常に完了しました。" です。 これらのイベントをアプリケーション イベント ログに記録するには、レジストリを編集用に開きます。 次に、レジストリ内で HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\SSIS ノードを見つけ、LogPackageExecutionToEventLog 設定の DWORD 値を 0 から 1 に変更します。    
    
## <a name="understanding-the-integration-services-service"></a>Integration Services サービスについて    
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスがインストールされます。    
    
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] [機能の選択] **ページで** [Integration Services] **オプションを選択すると、** サービスがインストールされます。 **[サーバーの構成]** ページで既定の設定をそのまま使用すると、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスが有効になり、その **[スタートアップの種類]** が **[自動]**になります。    
    
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスのインスタンスは 1 台のコンピューターに 1 つだけインストールできます。 このサービスは、データベース エンジンの特定のインスタンスに固有ではありません。 サービスに接続するには、サービスが実行されているコンピューターの名前を使用します。    
    
## <a name="installing-integration-services-on-64-bit-computers"></a>64 ビット コンピューターへの Integration Services のインストール    
    
### <a name="integration-services-features-installed-on-64-bit-computers"></a>64 ビット コンピューターにインストールされる Integration Services 機能    
 セットアップにより、選択したセットアップ オプションに基づいてさまざまな [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 機能がインストールされます。    
    
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールし、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] をインストールするように選択した場合、使用可能な 64 ビットの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 機能とツールがすべてインストールされます。    
    
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のデザイン時機能が必要な場合は、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]もインストールする必要があります。    
    
-   特定のパッケージを 32 ビット モードで実行するために 32 ビット版の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ランタイムおよびツールが必要な場合は、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]もインストールする必要があります。    
    
 64 ビット バージョンの機能は、 **Program Files** ディレクトリに格納されます。32 ビット バージョンの機能は、 **Program Files (x86)** ディレクトリに別個にインストールされます。 この動作は [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に固有の動作ではありません。    
    
> [!IMPORTANT]    
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] パッケージの 32 ビット開発環境である [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は、[!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)] 64 ビット オペレーティング システムではサポートされていないので、[!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)] サーバーにはインストールされません。    
    
  
