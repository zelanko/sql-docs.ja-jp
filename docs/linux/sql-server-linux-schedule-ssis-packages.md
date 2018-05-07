---
title: Cron と Linux の SSIS パッケージのスケジュール |Microsoft ドキュメント
description: この記事では、cron サービスと Linux 上の SQL Server Integration Services (SSIS) パッケージをスケジュールする方法について説明します。
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.openlocfilehash: 0ef397f966196de6e47737f30d10cbf4d6f39eb4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="schedule-sql-server-integration-services-package-execution-on-linux-with-cron"></a>スケジュール SQL Server Integration Services パッケージの cron と Linux の実行

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Windows で SQL Server Integration Services (SSIS) と SQL Server を実行する場合は、SQL Server エージェントを使用して、SSIS パッケージの実行を自動化できます。 Linux に SQL Server と SSIS を実行するとただし、SQL Server エージェントのユーティリティは Linux 上のジョブのスケジュール設定を使用できません。 代わりは、広く使用されている Linux プラットフォームではパッケージの実行を自動化する cron サービスを使用します。

この記事では、SSIS パッケージの実行を自動化する方法を示す例を提供します。 例は、Red Hat Enterprise を実行に書き込まれます。 コードは、Ubuntu など他の Linux ディストリビューションと似ています。

## <a name="prerequisites"></a>前提条件

ジョブを実行する cron サービスを使用する前に、コンピューターで実行されているかどうかを確認します。

Cron サービスの状態を確認するには、次のコマンドを使用:`systemctl status crond.service`です。

サービスがアクティブでない場合 (つまり、実行されていない) を設定および cron サービスを適切に構成する管理者に問い合わせてください。

## <a name="create-jobs"></a>ジョブを作成します。

Cron ジョブとは、指定された間隔で定期的に実行する構成可能なタスクです。 ジョブは通常、コンソール内で直接入力するか、またはシェル スクリプトとして実行コマンドと同じくらい簡単にできます。

簡単な管理とメンテナンスの目的では、わかりやすい名前を含むスクリプトをパッケージの実行コマンドを配置することをお勧めします。

パッケージを実行するための簡単なシェル スクリプトの例を次に示します。 1 つのコマンドのみが含まれていますが、必要に応じて他のコマンドを追加することができます。

```bash
# A simple shell script that contains a simple package execution command
# Script name: SSISpackageName.daily

/opt/ssis/bin/dtexec /F yourSSISpackageName.dtsx >> $HOME/tmp/out 2>&1
```

## <a name="schedule-jobs-with-the-cron-service"></a>Cron サービスでジョブのスケジュール設定します。

ジョブを定義した後 cron サービスを使用して自動的に実行するようにスケジュールできます。

Cron を実行するため、ジョブを追加するには、crontab ファイルで、ジョブを追加します。 開くには、crontab ファイルを追加したり、ジョブを更新できますエディターで、次のコマンドを使用:`crontab -e`です。

既に説明したジョブを毎日午前 2 時 10 分に実行をスケジュールするには、crontab ファイルに次の行を追加します。

```
# run <SSIS package name> at 2:10 AM every day
10 2 \* \* \* $/HOME/SSIS/jobs/SSISpackageName.daily
```

Crontab ファイルを保存し、エディターを終了します。

サンプル コマンドの形式を理解するのには、次のセクションの情報を確認します。
 
## <a name="format-of-a-crontab-file"></a>Crontab ファイルの形式

次の図は、crontab ファイルに追加されるジョブの行の書式の説明を示します。

![Crontab ファイル内のエントリの形式の説明](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-job-definition.png)

Crontab ファイル形式のより詳細な説明を取得するには、次のコマンドを使用:`man 5 crontab`です。

この記事の内容の例を説明するのに役立つ出力の部分的な例を次に示します。

![Crontab 形式の詳細の部分的な説明](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-crontab-format.png)

## <a name="related-content-about-ssis-on-linux"></a>Linux 上の SSIS についての関連コンテンツ
-   [抽出、変換、および SSIS Linux でのデータを読み込む](sql-server-linux-migrate-ssis.md)
-   [Linux 上の SQL Server Integration Services (SSIS) のインストールします。](sql-server-linux-setup-ssis.md)
-   [Ssis conf で Linux 上の SQL Server Integration Services を構成します。](sql-server-linux-configure-ssis.md)
-   [制限事項と Linux の SSIS の既知の問題](sql-server-linux-ssis-known-issues.md)
