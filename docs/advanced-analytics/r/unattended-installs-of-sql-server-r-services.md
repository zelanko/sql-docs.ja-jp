---
title: "Machine Learning のサービスの無人インストール |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/31/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77e92b2d-5777-4c31-bf02-f931ed54a247
caps.latest.revision: "18"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: c58bbb4a7277b37c9ef479b79ba4809a02218908
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="unattended-installation-of-machine-learning-services-in-database"></a>Machine Learning Services (In-database) の無人インストール

この記事では、SQL Server セットアップをコマンドライン引数を使用して、機械学習のコンポーネントをインストールする方法について説明します。

無人インストールは、意味ことがありませんセットアップ ウィザードの対話型機能を使用してでライセンス契約 for SQL Server との machine learning のコンポーネントを含め、完全なインストールに必要なすべての引数を指定する代わりに、コマンドラインまたは通常はクワイエット モードで、スクリプトの一部として。

+ [SQL Server 2016 R サービス](#bkmk_OldInstall)
+ [サービスの学習の SQL Server 2017 マシン](#bkmk_NewInstall)R、Python と
+ [Microsoft R サーバーまたは Machine Learning サーバー](../r/install-microsoft-r-server-from-the-command-line.md)

**適用されます SQL Server 2017 Machine Learning Services (In-database)、SQL Server 2016 R サービス。**

## <a name="prerequisites"></a>前提条件

+ Machine learning を使用する各インスタンスで、データベース エンジンをインストールする必要があります。

+ コンピューターがインターネットにアクセスを持たない場合は、コンポーネントをあらかじめ学習マシン用のインストーラーをダウンロードすることを確認します。 参照してください[インターネットにアクセスできないマシン ラーニング コンポーネントをインストールする](../r/installing-ml-components-without-internet-access.md)です。

+ R、Python のオープン ソース コンポーネントの各パラメーターをライセンス別があります。 SQL Server 2016 のみ R; をサポートしていますSQL Server 2017 には、R、Python の両方がサポートしています。 インストールする各言語のライセンス条項に同意する必要があります。 コマンドラインでこのパラメーターが含まれていない場合、セットアップが失敗します。

+ プロンプトに応答することがなく、セットアップを完了するには、ライセンス、およびその他の機能をインストールする場合がありますを含め、すべての必須引数を識別することを確認します。

+ **Mixed**早期のリリースで SQL ログインをサポートするセキュリティ モードが必要でした。 必要なくなりましたが、データ サイエンティストは、SQL ログインを使用してソリューションの開発をサポートするために混合モード認証を有効にするを検討する可能性があります。

> [!IMPORTANT]
> 
> セットアップの終了後に、機能を有効にする、追加の手順が必要です。 これらは、再構成を含めるし、インスタンスの再起動します。 確認して [インストール後の手順] セクションのすべての項目を確認するアクションを決定する (#bkmk_PostInstall) が必要にセットアップが完了した後。

## <a name="bkmk_NewInstall"></a>SQL Server 2017 のコマンド ライン インストール

次の例、**最小**機能に必要です。

> [!IMPORTANT]
> 必ず、管理者特権のコマンド プロンプトからのすべてのコマンドを実行してください。
> 
> インストールが完了したら、追加の手順が必要です。 参照してください[ここ](#bkmk_PostInstall)です。 
> 構成が完了したら、SQL Server サービスをもう一度再起動が必要になります。

### <a name="install-r-only"></a>R のインストールのみ

次の例では、追加の R 言語で、サイレントの無人実行に必要な引数が SQL Server 2017 Machine Services (In-database) のインストールを示します。

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MR /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS
```

SQL Server 2017 で R の必要なフラグを注意してください。

+ `ADVANCEDANALYTICS`
+ `SQL_INST_MR`
+ `IACCEPTROPENLICENSETERMS`」をご覧ください。

### <a name="install-python-only"></a>Python のインストールのみ

次の例は、追加 Python 言語で、サイレントの無人実行に必要な引数が SQL Server 2017 Machine Services (In-database) のインストールを示しています。

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTPYTHONOPENLICENSETERMS
```

SQL Server 2017 の Python のために必要なフラグを注意してください。

+ `ADVANCEDANALYTICS`
+ `SQL_INST_MPY`
+ `IACCEPTPYTHONOPENLICENSETERMS`

### <a name="install-both-r-and-python-on-a-named-instance"></a>名前付きインスタンスに R、Python の両方をインストールします。

次の例、サイレントの無人実行に必要な引数が SQL Server 2017 Machine Services (In-database) のインストール、名前付きインスタンスにします。 R、Python の両方の言語が追加されます。

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MR, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER.ServerName /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONOPENLICENSETERMS
```

## <a name="OldInstall"></a>SQL Server 2016 用コマンド ライン インストール
 
次の例では、追加の R 言語で、サイレントの無人実行に必要な引数が SQL Server 2016 のインストールを示します。

```
Setup.exe /q /ACTION=Install /FEATURES=SQL,ADVANCEDANALYTICS /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS
```

2016 R Services に必要なフラグを注意してください。

+ `ADVANCEDANALYTICS`
+ `IACCEPTROPENLICENSETERMS`

## <a name = "bkmk_PostInstall"></a>セットアップ後に追加の手順

SQL Server セットアップが完了したら、インストールしたバージョンに関係なく、次の手順を実行する必要があります。 machine learning の機能は、既定で無効になってし、明示的に有効にする必要があります。

1.  インストールが完了したら、新しく開きます**クエリ**ウィンドウ[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、および機能を有効には、次のコマンドを実行します。
  
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
    > [!NOTE]
    >  この機能を明示的に有効にする必要がありますを再構成します。それ以外の場合、機能がインストールされている場合でも外部スクリプトを呼び出すことができません。
  
2.  再構成されたインスタンスの SQL Server サービスを再起動します。 これは自動的に再起動、関連する[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービスもします。

> [!IMPORTANT]
> 
> カスタム セキュリティ構成がある場合、または使用する SQL Server コンピューティング コンテキストとしてリモート クライアントから R または Python コードを実行するときに、追加の手順が必要があります。 
> 
> 詳細については、次を参照してください。[アップグレードとインストールに関する FAQ](../../advanced-analytics/r/upgrade-and-installation-faq-sql-server-r-services.md)です。
