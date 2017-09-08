---
title: "Machine Learning のサービスの無人インストール |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77e92b2d-5777-4c31-bf02-f931ed54a247
caps.latest.revision: 18
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: babb74aa866404853cfef83e1d30159354f385e7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="unattended-installation-of-machine-learning-services-in-database"></a>Machine Learning Services (In-database) の無人インストール

このトピックでは、SQL Server セットアップをコマンドライン引数を使用して、機械学習をサイレント モードで、データベース エンジンのインスタンスにインストールする方法について説明します。 無人インストールでは、セットアップ ウィザードの対話型機能を使用しないし、ライセンス契約 for SQL Server との machine learning のコンポーネントを含め、完全なインストールに必要なすべての引数を指定する必要があります。

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習の Services (In-database)

> [!IMPORTANT]
> 
> SQL Server 2016 および SQL Server 2017 でセットアップの終了後に、機能を有効にする追加の手順が必要です。 これらは、再構成を含めるし、インスタンスの再起動します。 必ずすべての手順を確認してください。

## <a name="prerequisites"></a>前提条件

+ Machine learning を使用する各インスタンスで、データベース エンジンをインストールする必要があります。

+ コンピューターがインターネットにアクセスを持たない場合は、コンポーネントをあらかじめ学習マシン用のインストーラーをインストールすることを確認します。 ダウンロードの場所を参照してください。[インターネットにアクセスできないマシン ラーニング コンポーネントをインストールする](../../advanced-analytics/r/installing-ml-components-without-internet-access.md)です。

+ 新しいライセンス R、Python のオープン ソース コンポーネントに関連するパラメーターがあります。 インストールする言語ごとに別個の引数を持つライセンス条項に同意する必要があります。 コマンドラインでこのパラメーターを含めないと、セットアップは失敗します。

+ プロンプトに応答することがなく、セットアップを完了するには、ライセンス、およびその他の機能をインストールする場合がありますを含め、すべての必須引数を識別することを確認します。

> [!NOTE] 
> SQL ログインをサポートする混合セキュリティ モードは、以前のリリースに必要でした。 ただし、SQL ログインを使用してデータ研究員によってソリューションの開発をサポートするために混合モード認証を有効化を検討する可能性があります。

## <a name="bkmk_NewInstall"></a>R の Machine Learning のサービスの無人インストール

次の例は、**最小**サイレントの無人実行するときにコマンドラインで指定する必要な機能が SQL Server 2017 Machine Services (In-database) のインストールします。

1. 管理者特権のコマンド プロンプトを開き、次のコマンドを実行します。

    ```  
    Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MR /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS
    ```
    
    SQL Server 2017 で R の必要なフラグに注意してください: `ADVANCEDANALYTICS`、 `SQL_INST_MR`、および`IACCEPTROPENLICENSETERMS`です。
2. サーバーを再起動します。
3. 説明に従って、インストール後の構成手順を行う[ここ](#bkmk_PostInstall)です。 SQL Server サービスをもう一度再起動が必要になります。

## <a name="OldInstall"></a>R Services (In-database) の無人インストール
 
 次の例は、**最小**サイレントの無人実行するときにコマンドラインで指定する必要な機能が SQL Server 2016 の R Services のインストールします。

1. 管理者特権のコマンド プロンプトを開き、次のコマンドを実行します。

    ```  
    Setup.exe /q /ACTION=Install /FEATURES=SQL,ADVANCEDANALYTICS /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS
    ```
    2016 R SERVICES に必要なフラグに注意してください:`ADVANCEDANALYTICS`と`IACCEPTROPENLICENSETERMS`です。
2. サーバーを再起動します。
3. 説明に従って、インストール後の構成手順を行う[ここ](#bkmk_PostInstall)です。 SQL Server サービスをもう一度再起動が必要になります。

## <a name = "bkmk_PostInstall"></a>セットアップ後に追加の手順

1.  インストールが完了したら、新しく開きます**クエリ**ウィンドウ[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、および機能を有効には、次のコマンドを実行します。
  
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
    > [!NOTE]
    >  この機能を明示的に有効にする必要がありますを再構成します。それ以外の場合、機能がインストールされている場合でも外部スクリプトを呼び出すことができません。
  
2.  再構成されたインスタンスの SQL Server サービスを再起動します。 これは自動的に再起動、関連する[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービスもします。

3. カスタム セキュリティ設定が構成されている場合や、SQL Server を使用してリモート計算コンテキストをサポートする場合は、追加の手順が必要な場合があります。 詳細については、「[Upgrade and Installation FAQ](../../advanced-analytics/r/upgrade-and-installation-faq-sql-server-r-services.md) (アップグレードとインストールに関してよく寄せられる質問)」をご覧ください。

