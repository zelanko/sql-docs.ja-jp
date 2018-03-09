---
title: "Oracle コンソール (OracleToSQL) for SSMA の概要 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Oracle Console, Console Output Conventions
- Oracle Console, Launching Console
ms.assetid: 667a5e4a-6848-4973-a72d-1287f64718ac
caps.latest.revision: "31"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: f73c9250dd75d3beb5ec16cdb70fb3a4f7c57b20
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="getting-started-with-ssma--for-oracle-console-oracletosql"></a>Oracle コンソール (OracleToSQL) for SSMA の概要
このセクションを起動し、[Oracle] コンソール アプリケーションで作業を開始する手順について説明します。 一覧表示、ここで、規則ウィンドウで使用される、一般的な SSMA コンソール出力。  
  
## <a name="launching-ssma-console"></a>SSMA コンソールを起動します。  
SSMA コンソール アプリケーションを起動するのにには、次の手順を使用します。  
  
1.  移動して**開始**を指す**すべてのプログラム**です。  
  
2.  クリックして、  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant Oracle コマンド プロンプトの**ショートカットです。  
  
    SSMA コンソール メニューの使用状況を表示および`(/? Help)`、コンソール アプリケーションで作業を開始するためです。  
  
## <a name="procedure-for-using-the-ssma-console"></a>SSMA コンソールを使用する手順  
Windows システムで、コンソールを正常に起動した後、次の手順を使用して作業する可能性があります。  
  
1.  SSMA コンソールは、スクリプト ファイルを構成します。 このセクションの内容の詳細については、次を参照してください。[スクリプト ファイルの作成 &#40;OracleToSQL&#41;](../../ssma/oracle/creating-script-files-oracletosql.md)です。  
  
2.  [変数値ファイル &#40;OracleToSQL&#41; の作成](../../ssma/oracle/creating-variable-value-files-oracletosql.md)  
  
3.  [サーバーの接続ファイル &#40;OracleToSQL&#41; の作成](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)  
  
4.  [SSMA コンソール &#40;OracleToSQL&#41; の実行](../../ssma/oracle/executing-the-ssma-console-oracletosql.md)プロジェクトのニーズに基づく  
  
追加機能:  
  
1.  [パスワードを指定して](http://msdn.microsoft.com/en-us/8c7d9f8e-06bb-476c-bbd2-15b61d5bba3c)エクスポート/その他のウィンドウのマシンにこれをインポートし、  
  
2.  [レポートの生成](http://msdn.microsoft.com/en-us/ccad6262-01e1-447a-bd2b-c105154c80ce)詳細な xml を表示するには、評価/conversion とデータの移行のためのレポートを出力します。 詳細なエラー レポートを更新および同期コマンドの生成もできます。  
  
## <a name="ssma-console-output-conventions"></a>SSMA コンソール出力の表記規則  
SSMA スクリプトのコマンドとオプションを実行すると、コンソール プログラムは、コンソールのユーザーに結果とメッセージ (については、エラーなど) を表示または、必要な場合は、xml 出力ファイルにリダイレクトします。 各メッセージの種類の出力には一意の色によって表されます。 白色のテキスト メッセージがスクリプト ファイルのコマンドを示しますたとえば、緑色で 1 つと、ユーザー入力を求めるを表します。  
  
![Ssmaconsoleoutput_oracle](../../ssma/db2/media/ssmaconsoleoutput_oracle.jpg "ssmaconsoleoutput_oracle")  
  
次の表に、コンソール出力の色の解釈:  
  
|色|Description|  
|---------|---------------|  
|[赤]|実行中に致命的なエラー|  
|灰色|日付と時刻スタンプをユーザーにメッセージ|  
|White|スクリプト ファイルのコマンド、メッセージの種類|  
|黄|警告|  
|[緑]|ユーザー入力を求める|  
|シアン|開始、終了日と操作の結果|  
  
## <a name="see-also"></a>参照  
[インストールを実行する SSMA for Oracle](http://msdn.microsoft.com/en-us/9211013a-ab24-4c52-9b26-87994b35e502)  
  
