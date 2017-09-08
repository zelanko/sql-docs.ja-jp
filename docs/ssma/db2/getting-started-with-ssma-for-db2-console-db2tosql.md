---
title: "DB2 コンソール (DB2ToSQL) for SSMA の概要 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: f245c017-023e-4880-8721-8908d339525e
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 24c96c6e76d89d271d80e3be51c8c27d62dbd6b3
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="getting-started-with-ssma--for-db2-console-db2tosql"></a>DB2 コンソール (DB2ToSQL) for SSMA の概要
このセクションを起動し、DB2 のコンソール アプリケーションで作業を開始する手順について説明します。 一覧表示、ここで、規則ウィンドウで使用される、一般的な SSMA コンソール出力。  
  
## <a name="launching-ssma-console"></a>SSMA コンソールを起動します。  
SSMA コンソール アプリケーションを起動するのにには、次の手順を使用します。  
  
1.  移動して**開始**を指す**すべてのプログラム**です。  
  
2.  クリックして、  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant DB2 コマンド プロンプトの**ショートカットです。  
  
    SSMA コンソール メニューの使用状況を表示および`(/? Help)`、コンソール アプリケーションで作業を開始するためです。  
  
## <a name="procedure-for-using-the-ssma-console"></a>SSMA コンソールを使用する手順  
Windows システムで、コンソールを正常に起動した後、次の手順を使用して作業する可能性があります。  
  
1.  SSMA コンソールは、スクリプト ファイルを構成します。 このセクションの内容の詳細については、次を参照してください。[スクリプト ファイルの作成 (&) #40";"DB2ToSQL"&"#41;](../../ssma/db2/creating-script-files-db2tosql.md)です。  
  
2.  [変数値ファイル (&) #40";"DB2ToSQL"&"#41; の作成](../../ssma/db2/creating-variable-value-files-db2tosql.md)  
  
3.  [サーバーの接続ファイル (&) #40";"DB2ToSQL"&"#41; の作成](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)  
  
4.  [SSMA コンソール (&) #40";"DB2ToSQL"&"#41; の実行](../../ssma/db2/executing-the-ssma-console-db2tosql.md)プロジェクトのニーズに基づく  
  
追加機能:  
  
1.  [パスワードを管理する](http://msdn.microsoft.com/en-us/56d546e3-8747-4169-aace-693302667e94)エクスポート/その他のウィンドウのマシンにこれをインポートし、  
  
2.  [レポートの生成](http://msdn.microsoft.com/en-us/69ef5fd9-190d-4c58-8199-b3f77d5e1883)詳細な xml を表示するには、評価/conversion とデータの移行のためのレポートを出力します。 詳細なエラー レポートを更新および同期コマンドの生成もできます。  
  
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
[SSMA の DB2 のインストール](http://msdn.microsoft.com/en-us/79fbe8ea-471b-407a-be2a-4100d9b57c61)  
  

