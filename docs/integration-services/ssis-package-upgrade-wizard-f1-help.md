---
title: "SSIS パッケージ アップグレード ウィザードの F1 ヘルプ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- sql13.is.upgradewizard.ssisupgradewizard.f1
- sql13.is.upgradewizard.selectsourcelocation.f1
- sql13.is.upgradewizard.selectdestinationlocation.f1
- sql13.is.upgradewizard.selectpackagemgtoptions.f1
- sql13.is.upgradewizard.selectpackages.f1
- sql13.is.upgradewizard.completewizard.f1
- sql13.is.upgradewizard.upgradingpackage.f1
ms.assetid: 7fe886ff-1ea5-48d5-9d20-d5da36dd1cd7
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 0e9c1eccc9a14c580ba733fc3c4f63e88db92d60
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="ssis-package-upgrade-wizard-f1-help"></a>SSIS パッケージ アップグレード ウィザードの F1 ヘルプ
  以前のバージョンで作成されたパッケージをアップグレードする SSIS パッケージ アップグレード ウィザードを使用して[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の現在のリリースのパッケージ形式に[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]です。  
  
 **SSIS パッケージ アップグレード ウィザードを実行するには**  
  
-   [SSIS パッケージ アップグレード ウィザードを使用した Integration Services パッケージのアップグレード](../integration-services/install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  

## <a name="ssis-upgrade-wizard"></a>SSIS アップグレード ウィザード
  
### <a name="options"></a>オプション  
 **[次回からこのページを表示しない]**  
 次回ウィザードを起動するときに、このようこそページをスキップします。  
 
## <a name="select-source-location-page"></a>ソースの場所の選択ページ
 **[ソースの場所を選択]** ページを使用すると、パッケージのアップグレード元を指定できます。  
  
> [!NOTE]  
>  このページは、 [!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ アップグレード ウィザードを [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] またはコマンド プロンプトから実行した場合にのみ使用できます。  
  
### <a name="static-options"></a>静的オプション  
 **[パッケージ ソース]**  
 アップグレードするパッケージが格納されている場所を選択します。 このオプションには、次の表に示す値があります。  
  
|値|Description|  
|-----------|-----------------|  
|**[ファイル システム]**|アップグレードするパッケージがローカル コンピューター上のフォルダーにあることを示します。<br /><br /> パッケージをアップグレードする前に元のパッケージをウィザードでバックアップするには、元のパッケージがファイル システムに格納されている必要があります。 詳細については、方法に関するトピックを参照してください。|  
|**[SSIS パッケージ ストア]**|アップグレードするパッケージがパッケージ ストア内にあることを示します。 パッケージ ストアは、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスが管理するファイル システム フォルダーのセットで構成されます。 詳細については、「[パッケージの管理 (SSIS サービス)](../integration-services/service/package-management-ssis-service.md)」を参照してください。<br /><br /> この値を選択すると、対応する**パッケージ ソース**動的オプションが表示されます。|  
|**Microsoft SQL Server**|アップグレードするパッケージが [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の既存のインスタンス内にあることを示します。<br /><br /> この値を選択すると、対応する**パッケージ ソース**動的オプションが表示されます。|  
  
 **フォルダー**  
 アップグレードするパッケージが格納されているフォルダーの名前を入力するか、 **[参照]** をクリックしてフォルダーを指定します。  
  
 **参照**  
 アップグレードするパッケージが格納されているフォルダーを参照して指定します。  
  
### <a name="package-source-dynamic-options"></a>パッケージ ソース動的オプション  
  
#### <a name="package-source--ssis-package-store"></a>[パッケージ ソース] = [SSIS パッケージ ストア]  
 **[サーバー]**  
 アップグレードするパッケージが存在するサーバーの名前を入力するか、一覧からこのサーバーを選択します。  
  
#### <a name="package-source--microsoft-sql-server"></a>[パッケージ ソース] = [Microsoft SQL Server]  
 **[サーバー]**  
 アップグレードするパッケージが存在するサーバーの名前を入力するか、一覧からこのサーバーを選択します。  
  
 **[Windows 認証を使用する]**  
 Windows 認証を使用してサーバーに接続する場合に選択します。  
  
 **[SQL Server 認証を使用する]**  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用してサーバーに接続する場合に選択します。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用する場合は、ユーザー名とパスワードを入力する必要があります。  
  
 **ユーザー名**  
 サーバーへの接続時に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証で使用するユーザー名を入力します。  
  
 **Password**  
 サーバーへの接続時に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証で使用するパスワードを入力します。  
 
## <a name="select-destination-location-page"></a>移行先の場所の選択ページ
 **[アップグレード先の場所を選択]** ページを使用すると、アップグレードされたパッケージの保存先を指定できます。  
  
> [!NOTE]  
>  このページは、 [!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ アップグレード ウィザードを [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] またはコマンド プロンプトから実行した場合にのみ使用できます。  
 
### <a name="static-options"></a>静的オプション  
 **ソースの場所に保存します。**  
 ウィザードの **[ソースの場所を選択]** ページで指定した場所と同じ場所に、アップグレードされたパッケージを保存します。  
  
 元のパッケージがファイル システムに格納されている場合に、ウィザードでそれらのパッケージをバックアップするには、 **[ソースの場所に保存]** オプションを選択します。 詳細については、「 [SSIS パッケージ アップグレード ウィザードを使用した Integration Services パッケージのアップグレード](../integration-services/install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)」を参照してください。  
  
 **新しい変換先の場所を選択します。**  
 このページで指定したアップグレード先の場所に、アップグレードされたパッケージを保存します。  
  
 **[パッケージ ソース]**  
 アップグレード パッケージが格納される場所を指定します。 このオプションには、次の表に示す値があります。  
  
|値|Description|  
|-----------|-----------------|  
|**[ファイル システム]**|アップグレードされたパッケージをローカル コンピューター上のフォルダーに保存することを示します。|  
|**[SSIS パッケージ ストア]**|アップグレードされたパッケージを Integration Services パッケージ ストア内に保存することを示します。 パッケージ ストアは、Integration Services サービスが管理するファイル システム フォルダーのセットで構成されます。 詳細については、「[パッケージの管理 &#40;SSIS サービス&#41;](../integration-services/service/package-management-ssis-service.md)」を参照してください。<br /><br /> この値を選択すると、対応する**パッケージ ソース**動的オプションが表示されます。|  
|**Microsoft SQL Server**|アップグレードされたパッケージを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の既存のインスタンスに保存することを示します。<br /><br /> この値を選択すると、対応する **パッケージ ソース** 動的オプションが表示されます。|  
  
 **フォルダー**  
 アップグレードされたパッケージを保存するフォルダーの名前を入力するか、 **[参照]** をクリックしてフォルダーを指定します。  
  
 **参照**  
 アップグレードされたパッケージを保存するフォルダーを、参照して指定します。  
  
### <a name="package-source-dynamic-options"></a>パッケージ ソース動的オプション  
  
#### <a name="package-source--ssis-package-store"></a>[パッケージ ソース] = [SSIS パッケージ ストア]  
 **[サーバー]**  
 アップグレード パッケージを保存するサーバーの名前を入力するか、一覧からサーバーを選択します。  
  
#### <a name="package-source--microsoft-sql-server"></a>[パッケージ ソース] = [Microsoft SQL Server]  
 **[サーバー]**  
 アップグレード パッケージを保存するサーバーの名前を入力するか、一覧からこのサーバーを選択します。  
  
 **[Windows 認証を使用する]**  
 Windows 認証を使用してサーバーに接続する場合に選択します。  
  
 **[SQL Server 認証を使用する]**  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用してサーバーに接続する場合に選択します。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用する場合は、ユーザー名とパスワードを入力する必要があります。  
  
 **ユーザー名**  
 サーバーへの接続時に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証で使用するユーザー名を入力します。  
  
 **Password**  
 サーバーへの接続時に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証で使用するパスワードを入力します。  
 
## <a name="select-package-management-options-page"></a>[パッケージ管理オプションの選択] ページ
  **[パッケージ管理オプションの選択]** ページを使用すると、パッケージのアップグレードに関するオプションを指定できます。  
  
 **SSIS パッケージ アップグレード ウィザードを実行するには**  
  
-   [SSIS パッケージ アップグレード ウィザードを使用した Integration Services パッケージのアップグレード](../integration-services/install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
### <a name="options"></a>オプション  
 **[接続文字列を更新して新しいプロバイダー名を使用する]**  
 現在のリリースの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] の次のプロバイダーの名前を使用するように、接続文字列を更新します。  
  
-   OLE DB Provider for[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ アップグレード ウィザードは、接続マネージャーに格納されている接続文字列だけを更新します。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] の式言語またはスクリプト タスクのコードによって動的に構築される接続文字列は更新しません。  
  
 **アップグレード パッケージを検証します。**  
 アップグレード パッケージを検証し、検証に合格したアップグレード パッケージだけを保存します。  
  
 このオプションを選択しない場合、ウィザードでアップグレード パッケージの検証が行われません。 したがって、有効なパッケージかどうかにかかわらず、すべてのアップグレード パッケージが保存されます。 ウィザードの **[アップグレード先の場所を選択]** ページで指定したアップグレード先に、アップグレード パッケージが保存されます。  
  
 検証を行うと、アップグレード プロセスにかかる時間が長くなります。 アップグレードに成功する可能性の高い大規模なパッケージに対しては、このオプションを選択しないことをお勧めします。  
  
 **新しいパッケージ Id を作成します。**  
 アップグレード パッケージの新しいパッケージ ID を作成します。  
  
 **パッケージのアップグレードが失敗したときに、アップグレード プロセスを続行します。**  
 あるパッケージをアップグレードできなかった場合に、残りのパッケージのアップグレードを [!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ アップグレード ウィザードで続行します。  
  
 **パッケージ名の競合**  
 同じ名前のパッケージをウィザードで処理する方法を指定します。 このオプションには、次の表に示す値があります。  
  
 **既存のパッケージ ファイルを上書き**  
 既存のパッケージを同じ名前のアップグレード パッケージで置き換えます。  
  
 **アップグレード パッケージ名に数値サフィックスを追加します。**  
 アップグレード パッケージの名前に数値サフィックスを追加します。  
  
 **パッケージをアップグレードしません。**  
 そのパッケージのアップグレードを停止し、ウィザードの完了時にエラーを表示します。  
  
 ウィザードの **[アップグレード先の場所を選択]** ページで **[ソースの場所に保存]** オプションを選択した場合は、これらのオプションを使用できません。  
  
 **構成を無視します。**  
 パッケージのアップグレード中にパッケージ構成を読み込みません。 このオプションを選択すると、パッケージのアップグレードに必要な時間が短縮されます。  
  
 **元のパッケージをバックアップ**  
 ウィザードで、元のパッケージを **SSISBackupFolder** フォルダーにバックアップします。 元のパッケージとアップグレード済みパッケージが格納されるフォルダーに、 **SSISBackupFolder** サブフォルダーが作成されます。  
  
> [!NOTE]  
>  このオプションを使用できるのは、元のパッケージとアップグレード済みパッケージをファイル システム内の同一フォルダーに格納するように指定した場合だけです。  

## <a name="select-packages-page"></a>[パッケージ] ページを選択します。
  **[パッケージの選択]** ページを使用すると、アップグレードするパッケージを選択できます。 このページには、ウィザードの **[ソースの場所を選択]** ページで指定した場所に格納されているパッケージが一覧表示されます。  
  
### <a name="options"></a>オプション  
 **既存のパッケージ名**  
 アップグレードする 1 つ以上のパッケージを選択します。  
  
 **アップグレード パッケージ名**  
 アップグレード先パッケージ名を指定するか、ウィザードによって提供される既定の名前を使用します。  
  
> [!NOTE]  
>  パッケージのアップグレード後に、アップグレード先パッケージ名を変更することもできます。 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] または [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]でアップグレード済みのパッケージを開き、パッケージ名を変更します。  
  
 **Password**  
 選択したアップグレード パッケージの複号化に使用するパスワードを指定します。  
  
 **[選択項目に適用]**  
 選択したアップグレード パッケージの復号化に、指定したパスワードを適用します。  
 
## <a name="complete-the-wizard-page"></a>ウィザードのページを完了します。
  **[ウィザードの完了]** ページでは、選択したパッケージ アップグレード オプションを確認できます。 このページは、このセッションのウィザードのオプションを前に戻って変更できる、最後のウィザード ページです。  
  
### <a name="options"></a>オプション  
 **オプションの概要**  
 ウィザードで選択したアップグレード オプションを確認します。 いずれかのオプションを変更するには、 **[戻る]** をクリックして前のウィザード ページに戻ります。
 
## <a name="upgrading-the-packages-page"></a>[パッケージ] ページをアップグレードします。
  **[パッケージをアップグレードしています]** ページでは、パッケージのアップグレードの進行状況を表示したり、アップグレード プロセスを中断したりできます。 [!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ アップグレード ウィザードでは、選択したパッケージが 1 つずつアップグレードされます。  
  
### <a name="options"></a>オプション  
 **メッセージ ペイン**  
 アップグレード プロセス中に、進行状況メッセージと概要情報が表示されます。  
  
 **操作**  
 アップグレード処理で実行されるアクションを表示します。  
  
 **[状態]**  
 各アクションの結果を表示します。  
  
 **メッセージ**  
 各アクションによって生成されるエラー メッセージを表示します。  
  
 **[停止]**  
 パッケージのアップグレードを停止します。  
  
 **レポート**  
 パッケージのアップグレード結果を含むレポートの処理を選択します。  
  
-   レポートをオンラインで表示します。  
  
-   レポートをファイルに保存します。  
  
-   レポートをクリップボードにコピーします。  
  
-   レポートを電子メール メッセージとして送信します。  

## <a name="view-upgraded-packages"></a>アップグレードされたパッケージを表示します。
### <a name="view-upgraded-packages-that-were-saved-to-a-sql-server-database-or-to-the-package-store"></a>SQL Server データベースまたはパッケージ ストアに保存されたアップグレードされたパッケージを表示します。
  
[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]のオブジェクト エクスプローラーで [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]のローカル インスタンスに接続し、 **[格納されたパッケージ]** ノードを展開すると、アップグレードされたパッケージが表示されます。  
  
### <a name="view-upgraded-packages-that-were-upgraded-from-sql-server-data-tools"></a>SQL Server Data Tools からアップグレードしたアップグレードされたパッケージを表示します。  
  
[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーで [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のプロジェクトを開き、 **[SSIS パッケージ]** ノードを展開すると、アップグレードされたパッケージが表示されます。  
  
## <a name="see-also"></a>参照  
 [Integration Services パッケージのアップグレード](../integration-services/install-windows/upgrade-integration-services-packages.md)  
  
  

