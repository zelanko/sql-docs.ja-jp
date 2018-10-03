---
title: Cron で Linux 上の SSIS パッケージのスケジュール |Microsoft Docs
description: この記事では、cron サービスで Linux 上の SQL Server Integration Services (SSIS) パッケージをスケジュールする方法について説明します。
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: bfc30c25d93581ee36f88c075416dbfebf59aea1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47753500"
---
# <a name="schedule-sql-server-integration-services-package-execution-on-linux-with-cron"></a>スケジュールの SQL Server Integration Services パッケージ cron を使用した Linux 上の実行

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server Integration Services (SSIS) と SQL Server を Windows で実行するときに、SQL Server エージェントを使用して SSIS パッケージの実行を自動化できます。 SSIS の SQL Server on Linux を実行すると、SQL Server エージェントのユーティリティは Linux 上のジョブをスケジュールする使用できません。 代わりに、パッケージの実行を自動化する Linux プラットフォームで広く使用されている cron サービスを使用します。

この記事では、SSIS パッケージの実行を自動化する方法を示す例を示します。 Red Hat Enterprise 上で実行する例が書き込まれます。 コードは、Ubuntu など、他の Linux ディストリビューションと似ています。

## <a name="prerequisites"></a>前提条件

ジョブを実行する cron サービスを使用する前に、コンピューターで実行されているかどうかを確認します。

Cron サービスの状態を確認するには、次のコマンドを使用:`systemctl status crond.service`します。

サービスがアクティブでない場合 (つまり、実行されていない)、設定して、cron サービスを適切に構成する管理者に問い合わせてください。

## <a name="create-jobs"></a>ジョブを作成します。

Cron ジョブは、指定された間隔で定期的に実行する構成可能なタスクです。 ジョブは通常、コンソールで直接入力するか、またはシェル スクリプトとして実行コマンドと同じくらい簡単にできます。

容易な管理とメンテナンスの目的では、わかりやすい名前を含むスクリプトをパッケージの実行コマンドを配置することをお勧めします。

パッケージを実行するための簡単なシェル スクリプトの例を次に示します。 1 つのコマンドのみが含まれていますが、必要に応じてその他のコマンドを追加することができます。

```bash
# A simple shell script that contains a simple package execution command
# Script name: SSISpackageName.daily

/opt/ssis/bin/dtexec /F yourSSISpackageName.dtsx >> $HOME/tmp/out 2>&1
```

## <a name="schedule-jobs-with-the-cron-service"></a>Cron サービス ジョブのスケジュール設定します。

ジョブを定義した後は、cron サービスを使用して自動的に実行するようをスケジュールできます。

実行する cron ジョブを追加するには、ジョブを crontab ファイルに追加します。 Crontab ファイルを追加またはジョブを更新することができます、エディターで開くには、次のコマンドを使用:`crontab -e`します。

2時 10分 AM に毎日実行する前に説明したジョブをスケジュールするには、crontab ファイルに、次の行を追加します。

```
# run <SSIS package name> at 2:10 AM every day
10 2 \* \* \* $/HOME/SSIS/jobs/SSISpackageName.daily
```

Crontab のファイルを保存し、エディターを終了します。

サンプル コマンドの形式を理解するには、次のセクションの情報を確認します。
 
## <a name="format-of-a-crontab-file"></a>Crontab のファイルの形式

次の図は、crontab ファイルに追加されるジョブの行の形式に関する説明を示します。

![Crontab ファイル内のエントリの形式の説明](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-job-definition.png)

Crontab のファイル形式の詳細な説明を取得するには、次のコマンドを使用:`man 5 crontab`します。

出力例では、この記事で説明するための部分的な例を次に示します。

![Crontab の形式の詳細な部分の説明](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-crontab-format.png)

## <a name="related-content-about-ssis-on-linux"></a>Linux 上の SSIS に関する関連コンテンツ
-   [抽出、変換、および SSIS Linux でのデータを読み込む](sql-server-linux-migrate-ssis.md)
-   [Linux 上の SQL Server Integration Services (SSIS) のインストールします。](sql-server-linux-setup-ssis.md)
-   [Ssis conf で Linux 上の SQL Server Integration Services を構成します。](sql-server-linux-configure-ssis.md)
-   [制限事項と Linux での SSIS の既知の問題](sql-server-linux-ssis-known-issues.md)
