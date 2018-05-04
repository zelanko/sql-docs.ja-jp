---
title: MySQL コンソール (MySQLToSQL) for SSMA の概要 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- MySQL Console, launching console
- MySQL Console, output conventions
ms.assetid: 218d502c-059f-4d48-9aea-61e553d74303
caps.latest.revision: 23
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 9246db3826d2c5a4b4826d637acb2afb089eeaa9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="getting-started-with-ssma-for-mysql-console-mysqltosql"></a>MySQL コンソール (MySQLToSQL) for SSMA の概要
このセクションを起動し、[MySQL] コンソール アプリケーションで作業を開始する手順について説明します。 一覧表示、ここで、規則ウィンドウで使用される、一般的な SSMA コンソール出力。  
  
## <a name="launching-ssma-console"></a>SSMA コンソールを起動します。  
SSMA コンソール アプリケーションを起動するのにには、次の手順を使用します。  
  
1.  移動して**開始**を指す**すべてのプログラム**です。  
  
2.  クリックして、 **SQL Server Migration Assistant MySQL コマンド プロンプトの**ショートカットです。  
  
    SSMA コンソール メニューの使用状況を表示および`(/? Help)`、コンソール アプリケーションで作業を開始するためです。  
  
## <a name="procedure-for-using-the-ssma-console"></a>SSMA コンソールを使用する手順  
Windows システムで、コンソールを正常に起動した後、次の手順を使用して作業する可能性があります。  
  
1.  SSMA コンソールは、スクリプト ファイルを構成します。 このセクションの内容の詳細については、次を参照してください。[スクリプト ファイルの作成&#40;MySQLToSQL&#41; ](../../ssma/mysql/creating-script-files-mysqltosql.md)です。  
  
2.  [変数の値のファイルを作成する&#40;MySQLToSQL&#41;](../../ssma/mysql/creating-variable-value-files-mysqltosql.md)  
  
3.  [サーバー接続ファイルを作成する&#40;MySQLToSQL&#41;](../../ssma/mysql/creating-the-server-connection-files-mysqltosql.md)  
  
4.  [SSMA コンソールを実行する&#40;MySQLToSQL&#41; ](../../ssma/mysql/executing-the-ssma-console-mysqltosql.md)プロジェクトのニーズに基づく  
  
追加機能:  
  
1.  [パスワードをセキュリティで保護する](http://msdn.microsoft.com/en-us/4ffbc587-ea3f-49ad-bc42-a654f672325e)エクスポート/その他のウィンドウのマシンにこれをインポートし、  
  
2.  [レポートの生成](http://msdn.microsoft.com/en-us/1c0202e8-546d-4cb3-a37f-1d2e35d53839)詳細な xml を表示するには、評価/conversion とデータの移行のためのレポートを出力します。 詳細なエラー レポートを更新および同期コマンドの生成もできます。  
  
## <a name="ssma-console-output-conventions"></a>SSMA コンソール出力の表記規則  
SSMA スクリプトのコマンドとオプションを実行すると、コンソール プログラムは、コンソールのユーザーに結果とメッセージ (については、エラーなど) を表示または、必要な場合は、xml 出力ファイルにリダイレクトします。 各メッセージの種類の出力には一意の色によって表されます。 白色のテキスト メッセージがスクリプト ファイルのコマンドを示しますたとえば、緑色で 1 つと、ユーザー入力を求めるを表します。  
  
![SSMAConsoleOutput_MySQL](../../ssma/mysql/media/ssmaconsoleoutput_mysql.jpg "SSMAConsoleOutput_MySQL")  
  
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
[インストールを実行する SSMA for MySQL](http://msdn.microsoft.com/en-us/e89b45bd-59c1-4d23-8bd7-3dafc1947448)  
  
