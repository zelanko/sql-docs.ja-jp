---
title: アップグレードアドバイザーの実行 (コマンドプロンプト) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], running
- command prompt [Upgrade Advisor]
- UpgradeAdvisorWizardCmd utility
- XML formats [Upgrade Advisor]
ms.assetid: 7c83049b-9227-4723-9b7f-66288bc6bd1d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 997d637d109c04dbecb3105538f51fa6ece0518f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66092441"
---
# <a name="running-upgrade-advisor-command-prompt"></a>アップグレード アドバイザーの実行 (コマンド プロンプト)
  **UpgradeAdvisorWizardCmd**ユーティリティを使用して、コマンドプロンプトからアップグレードアドバイザーを実行します。 結果を XML 形式で受け取るか、コンマ区切り値のファイルで受け取るかを選択できます。  
  
## <a name="syntax"></a>構文  
  
```  
  
      UpgradeAdvisorWizardCmd [ -? ]  |   
    [ -ConfigFilefilename | <server_info> ]  
    [ -SqlUserlogin_id-SqlPasswordpassword ]  
    [ -CSV ]  
  
where <server_info> is any combination of the following:  
        -Serverserver_name-Instanceinstance_name-ASInstanceAS_instance_name-RSInstanceRS_instance_name  
```  
  
## <a name="arguments"></a>引数  
 **-?**  
 コマンドの構文を表示します。  
  
 **-ConfigFile** _ファイル名_  
 **UpgradeAdvisorWizardCmd**ユーティリティを実行するときに使用する設定を含む XML ファイルのパス名とファイル名を指定します。  
  
 *<server_info>*  
 分析するコンピューターとインスタンスを指定します。 構成ファイルを使用していない場合に、これらのオプションを使用します。  
  
 *<server_info>* は、次の4つの引数の任意の組み合わせにすることができます。  
  
 **-サーバー** _server_name_  
 分析するコンピューターの名前を指定します。 ローカル コンピューター (既定値) またはリモート コンピューターのどちらでも指定できます。  
  
 **-インスタンス** _instance_name_  
 分析するインスタンスの名前を指定します。 既定値はありません。 このパラメーター [!INCLUDE[ssDE](../../includes/ssde-md.md)]を指定しない場合、はスキャンされません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインスタンスの値は MSSQLSERVER です。 名前付きインスタンスの場合は、インスタンス名を使用します。  
  
 **-Asinstance**  _AS_instance_name_  
 分析する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスの名前を指定します。 既定値はありません。 この値を指定しない場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] はスキャンされません。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の既定のインスタンスの値は MSSQLServerOLAPService です。 名前付きインスタンスの場合は、インスタンス名を使用します。  
  
 **-Rsinstance**  _RS_instance_name_  
 分析する [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンスの名前を指定します。 既定値はありません。 この値を指定しない場合、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] はスキャンされません。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の既定のインスタンスの値は ReportServer です。 名前付きインスタンスの場合は、インスタンス名を使用します。  
  
 **-Sqluser** _login_id_  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合は、この値に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。アップグレード アドバイザーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへの接続にこのログインを使用します。 ログインを指定しないと、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへの接続に Windows 認証が使用されます。  
  
 **-Sqlpassword** _パスワード_  
 **-Sqluser**引数を使用する場合は、この引数を使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインのパスワードを指定します。  
  
 **-CSV**  
 標準的な XML の結果に加え、コンマ区切り値の結果を .csv ファイルに出力する場合に指定します。 結果は My Documents\\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports フォルダーに書き込まれます。  
  
## <a name="return-values"></a>戻り値  
 次の表は、 **UpgradeAdvisorWizardCmd**が返す値を示しています。  
  
|[値]|説明|  
|-----------|-----------------|  
|0|分析が正常に完了し、アップグレードの問題は見つかりませんでした。|  
|正の整数|分析が正常に完了し、アップグレードの問題が見つかりました。|  
|負の整数|分析が失敗しました。|  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のユーザー名とパスワード以外は、分析の実行に必要なすべての情報を XML 構成ファイルに出力できます。 この XML 構成ファイルはテンプレートに記述されています。 構成ファイルを使用しない場合は、既定の設定でコンピューター名とインスタンス名を指定すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにインストールされているコンポーネントすべてを分析できます。 既定の構成ファイル設定の詳細については、「要素の説明」の一覧を参照してください。  
  
## <a name="configuration-file-template"></a>構成ファイルのテンプレート  
 独自の構成ファイルを作成する場合は、次の XML をテンプレートとして使用してください。 テンプレートは必要に応じて変更できます。  
  
```xml  
<Configuration>  
    <Server> </Server>  
    <Instance></Instance>  
    <Components>  
        <SQLServer>  
            <Databases>  
                <Database></Database>  
            </Databases>  
            <TraceFiles>  
                <TraceFile></TraceFile>  
            </TraceFiles>  
            <BatchFiles>  
                <BatchFile></BatchFile>  
            </BatchFiles>  
            <BatchSeparator></BatchSeparator>  
        </SQLServer>  
        <AnalysisServices>  
            <ASInstance></ASInstance>  
            <Databases>  
                <Database></Database>  
            </Databases>  
        </AnalysisServices>  
        <ReportingServices>  
            <RSInstance></RSInstance>  
        </ReportingServices>  
        <IntegrationServices>  
            <PackagePath></PackagePath>  
        </IntegrationServices>  
    </Components>  
</Configuration>  
```  
  
## <a name="element-descriptions"></a>要素の説明  
  
|タグ|定義|個数|  
|---------|----------------|----------------|  
|`Configuration`|アップグレード アドバイザー構成ファイルの親要素です。|必須。構成ファイルにつき 1 個。|  
|`Server`|分析するサーバーの名前です。|省略可。構成ファイルにつき 1 個。 既定値はローカル コンピューターです。|  
|`Instance`|分析する[!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスの名前です。|省略可。構成ファイルにつき 1 個。 既定値は既定のインスタンスです。<br /><br /> サーバー上に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 要素または `IntegrationServices` 要素が存在する場合は必須。構成ファイルにつき 1 個。|  
|`Components`|分析するコンポーネントを指定する要素を含みます。|必須。構成ファイルにつき 1 個。|  
|`SQLServer`|[!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスの分析設定を含みます。|省略可。構成ファイルにつき 1 個。 指定しないと、[!INCLUDE[ssDE](../../includes/ssde-md.md)] データベースが分析されません。|  
|`Databases` 要素の `SQLServer`|分析するデータベースの一覧を含みます。|省略可能。 `SQLServer`要素ごとに1回です。 この要素が存在しない場合、インスタンスのすべてのデータベースが分析されます。|  
|`Database` 要素の `SQLServer`|分析するデータベースの名前を指定します。|必須。`Databases` 要素が存在する場合に 1 個以上。 `Database` 要素に値 "*" が含まれている場合は、インスタンスのすべてのデータベースが分析されます。 既定値はありません。|  
|`TraceFiles`|分析するトレース ファイルの一覧を含みます。|省略可能。 `SQLServer`要素ごとに1回です。|  
|`TraceFile`|分析するトレース ファイルのパスと名前を指定します。|必須。`TraceFiles` 要素が存在する場合に 1 個以上。 既定値はありません。|  
|`BatchFiles`|分析するバッチ ファイルの一覧を含みます。|省略可能。 `SQLServer`要素ごとに1回です。|  
|`BatchFile`|分析するバッチ ファイルを指定します。 複数指定することもできます。|必須。`BatchFiles` 要素が存在する場合に 1 個以上。 既定値はありません。|  
|`BatchSeparator`|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バッチ ファイルに使用されるバッチ区切り記号を指定します。|省略可能。 `SQLServer`要素ごとに1回です。 既定値は GO です。|  
|`AnalysisServices`|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の分析設定を含みます。|省略可。構成ファイルにつき 1 個。 指定しないと、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースが分析されません。|  
|`ASInstance`|の[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスの名前を指定します。|必須。`AnalysisServices` 要素につき 1 個。 既定値はありません。|  
|`Databases` 要素の `Analysis Services`|分析するデータベースの一覧を含みます。|省略可能。 `AnalysisServices`要素ごとに1回です。 この要素が存在しない場合、インスタンスのすべてのデータベースが分析されます。|  
|`Database` 要素の `AnalysisServices`|分析するデータベースの名前を指定します。|必須。`Databases` 要素が存在する場合に 1 個以上。 `Database` 要素に値 "*" が含まれている場合は、インスタンスのすべてのデータベースが分析されます。 既定値はありません。|  
|`ReportingServices`|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に対して分析を実行することを指定します。|省略可。構成ファイルにつき 1 個。 指定しなかった場合、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は分析されません。|  
|`RSInstance`|の[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]インスタンスの名前を指定します。|必須。`ReportingServices` 要素につき 1 個。 既定値はありません。|  
|`IntegrationServices`|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の分析設定を含みます。|省略可。構成ファイルにつき 1 個。 指定しなかった場合、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は分析されません。|  
|`PackagePath`|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのセットのパスを指定します。|省略可能。 `IntegrationServices`要素ごとに1回です。 この要素が存在しない場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに対して分析が行われ、外部に格納されたパッケージは分析されません。 既定値はありません。|  
  
## <a name="examples"></a>例  
  
### <a name="a-run-upgrade-advisor-using-a-configuration-file"></a>A. 構成ファイルを使用したアップグレード アドバイザーの実行  
 次の例は、分析対象を指定する構成ファイルを使用したコマンド プロンプトからのアップグレード アドバイザーの実行方法を示しています。 この例では、Windows 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続します。  
  
```  
UpgradeAdvisorWizardCmd -ConfigFile "C:\My Documents\UpgradeConfig1.xml"  
```  
  
### <a name="b-run-upgrade-advisor-using-default-configuration-settings"></a>B. 既定の構成設定を使用したアップグレード アドバイザーの実行  
 次の例は、既定の構成設定と Windows 認証を使用したコマンド プロンプトからのアップグレード アドバイザーの実行方法を示しています。  
  
```  
UpgradeAdvisorWizardCmd -Server MyServer -Instance MyInst   
```  
  
### <a name="c-run-upgrade-advisor-using-ssnoversion-authentication"></a>C. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用したアップグレード アドバイザーの実行  
 次の例は、構成ファイルを使用したコマンド プロンプトからのアップグレード アドバイザーの実行方法を示しています。 この例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続するための [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザー名とパスワードを指定します。  
  
```  
UpgradeAdvisorWizardCmd -ConfigFile "C:\My Documents\UpgradeConfig1.xml"   
    -SqlUser "MyUserName" -SqlPassword "QweRTy-55"  
```  
  
## <a name="see-also"></a>参照  
 [アップグレードに関する問題の解決](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [アップグレードアドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [アップグレードアドバイザー &#40;ユーザーインターフェイス&#41;を実行しています](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)  
  
  
