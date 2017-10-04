---
title: "Cron と Linux の SSIS パッケージのスケジュール |Microsoft ドキュメント"
description: "この記事では、cron サービスと Linux 上の SQL Server Integration Services パッケージをスケジュールする方法を示します。"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.date: 09/26/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 31d5fb63a9c2a4d8825aa39c6fa7e3377ddc8d91
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="schedule-sql-server-integration-services-package-execution-on-linux-with-cron"></a>スケジュール SQL Server Integration Services パッケージの cron と Linux の実行

Windows で SQL Server Integration Services (SSIS) と SQL Server を実行する場合は、SQL Server エージェントを使用して、SSIS パッケージの実行を自動化できます。 Linux に SQL Server と SSIS を実行するとただし、SQL Server エージェントのユーティリティは Linux 上のジョブのスケジュール設定を使用できません。 代わりに使用する**Cron**パッケージの実行を自動化する Linux プラットフォームで広く使用されているサービスです。

この記事では、SSIS パッケージの実行を自動化する方法を示す例を提供します。 例は、Red Hat Enterprise を実行に書き込まれました。 コードは、Ubuntu と同様に他の Linux ディストリビューションと似ています。

## <a name="prerequisites"></a>前提条件

ジョブを実行する Cron サービスを使用することができます、前に、Cron サービスがお使いのコンピューターで実行されているかどうかを確認する必要があります。

次の Cron サービスの状態を確認するコマンドを使用します。

`systemctl status crond.service`

サービスがアクティブ (つまり、実行されていない) でない場合を設定および Cron サービスを適切に構成する管理者に問い合わせてください。

## <a name="create-jobs"></a>ジョブの作成

Cron ジョブとは、指定された間隔で定期的に実行する構成可能なタスクです。 ジョブは通常、コンソール内で直接入力するか、またはシェル スクリプトとして実行コマンドと同じくらい簡単にできます。

簡単な管理とメンテナンスの目的では、ことをわかりやすい名前を持つスクリプト パッケージの実行コマンドにお勧めします。

パッケージを実行する 1 つのコマンドのみを格納するシェル スクリプトの簡単な例を次に示します。 必要に応じて、他のコマンドを追加できます。

```bash
# A simple shell script that contains a simple package execution command
# Script name: SSISpackageName.daily

/opt/ssis/bin/dtexec /F yourSSISpackageName.dtsx >> $HOME/tmp/out 2>&1
```

## <a name="schedule-jobs-with-the-cron-service"></a>Cron サービスでジョブのスケジュール

ジョブを定義した後 Cron サービスを使用して自動的に実行するようにスケジュールできます。

Cron を実行するため、ジョブを追加するには、内のジョブを追加する必要が、`crontab`ファイル。 開くには、`crontab`ファイルを追加したり、ジョブを更新できますをエディターで、次のコマンドを使用します。

`crontab -e`

既に説明したジョブを毎日午前 2 時 10 分に実行をスケジュールするには、次の行を追加、`crontab`ファイル。

```
# run SSIS package Name at 2:10AM every day
10 2 \* \* \* $/HOME/SSIS/jobs/SSISpackageName.daily
```

保存、`crontab`ファイルし、エディターを終了します。

サンプル コマンドの形式を理解するのには、次のセクションの情報を確認します。
 
## <a name="format-of-a-crontab-file"></a>Crontab ファイルの形式

次の図は、の形式に関する説明に追加されたジョブの線、`crontab`ファイル。

![Crontab ファイル内のエントリの形式の説明](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-job-definition.png)

より詳細な説明を取得する、`crontab`ファイル形式を次のコマンドを使用します。

`man 5 crontab`

この記事の内容の例を説明するのに役立つ出力の部分的な例を次に示します。

![Crontab 形式の詳細の部分的な説明](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-crontab-format.png)

