---
title: "Python Machine Learning Services (In-database) の無人インストール |Microsoft ドキュメント"
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
caps.latest.revision: 1
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9b9156a3dc9dec21187eec8dc0b5a44059fb5e31
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="unattended-installation-of-python-machine-learning-services-in-database"></a>Python Machine Learning Services (In-database) の無人インストール

このトピックでは、Machine Learning のサービスと、Python、quiet モードを使用して、SQL Server データベース エンジンをインストールする SQL Server 2017 セットアップ時にコマンドライン引数を使用する方法について説明します。

> [!NOTE]
> Python 用および SQL Server 用のライセンス契約のコマンドライン引数を含める忘れないでください。

## <a name="prerequisites"></a>前提条件

インストール プロセスを始める前に、次の要件を確認してください。

+ SQL Server 2017 データベース エンジンとは無関係に Python サービスをインストールすることはできません。 SQL データベース エンジンの機能を含める必要があります。
+ オフライン インストールを実行する場合は場合、は、Python の必須コンポーネントを事前にダウンロードして、ローカル フォルダーにコピーする必要があります。 ダウンロードの場所を参照してください。 [Machine Learning Components without Internet Access をインストールする](../../advanced-analytics/r-services/installing-ml-components-without-internet-access.md)です。
+ 新しいパラメーターがある*/IACCEPTPYTHONLICENSETERMS*、Continuum Analytics によって提供される Python コンポーネントを使用してライセンス条項に同意したことを示すです。 コマンドラインでこのパラメーターを含めないと、セットアップは失敗します。
+ プロンプトに応答することがなくセットアップを完了するには Python と SQL Server のライセンス、および他の機能をインストールする場合がありますを含め、すべての必須引数を識別することを確認します。
+  混合モード認証は、SQL Server 2016 の一部のプレリリース バージョンで必要でした。 データ科学者の開発と SQL ログインを使用してリモートでソリューションのテストの場所のシナリオで役に立ちますが、必須ではありません。

## <a name="perform-an-unattended-installation-of-python-machine-learning-services-in-database"></a>Python Machine Learning Services (In-database) の無人インストールを実行します。

次の例は、**最小**既定のインスタンスでの Python とデータベース エンジンのサイレントの無人インストールを実行するときに、コマンドラインで指定する機能に必要です。

> [!NOTE]
> この機能には、SQL Server 2017 が必要です。 Python は、SQL Server の以前のバージョンではサポートされていません。

1. 管理者特権のコマンド プロンプトを開き、次のコマンドを実行します。

    ```  
    Setup.exe /q /ACTION=Install /FEATURES=SQL,ADVANCEDANALYTICS, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTPYTHONLICENSETERMS
    ```

    > [!NOTE]
    > 
    > Python のための新しいセットアップ フラグがある:`SQL_INST_MPY`と`IACCEPTPYTHONLICENSETERMS`

2. 指示に従って、サーバーを再起動します。
3. 説明に従って、インストール後の構成手順を行う[ここ](#bkmk_PostInstall)です。 SQL Server サービスをもう一度再起動が必要になります。

## <a name = "bkmk_PostInstall"></a>インストール後の手順

1.  インストールが完了したら、新しく開きます**クエリ**ウィンドウ[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、および機能を有効には、次のコマンドを実行します。

    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
    > [!NOTE]
    >  この機能を明示的に有効にする必要がありますを再構成します。それ以外の場合、機能がインストールされている場合でも外部スクリプトを呼び出すことができません。
  
3.  再構成されたインスタンスの SQL Server サービスを再起動します。 これは自動的に再起動、関連する[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービスもします。

3. カスタム セキュリティ設定が構成されている場合や、SQL Server を使用してリモート計算コンテキストをサポートする場合は、追加の手順が必要な場合があります。 詳細については、次を参照してください。 [machine learning のセットアップに関するトラブルシューティング](../machine-learning-troubleshooting-faq.md)です。
