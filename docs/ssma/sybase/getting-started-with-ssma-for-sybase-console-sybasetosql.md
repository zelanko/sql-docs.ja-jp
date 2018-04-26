---
title: Sybase コンソール (SybaseToSQL) for SSMA の概要 |Microsoft ドキュメント
ms.custom: ''
ms.date: 09/30/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Sybase Console,Launching SSMA Console
- Sybase Console,Output Conventions
- Sybase Console,Procedure for Using Console
ms.assetid: 43219dbe-bcfa-427d-9242-f07b1455f15f
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d9ee7bbb1805f6476317386490ca5c3d71865472
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="getting-started-with-the-ssma-for-sybase-console-sybasetosql"></a>Sybase コンソール (SybaseToSQL) for SSMA の概要
このセクションを起動して、SSMA for Sybase コンソール アプリケーションの使用を開始するための手順について説明します。 記載されている表記規則ウィンドウで使用される、一般的な SSMA コンソール出力。  
  
## <a name="launching-the-ssma-console"></a>SSMA コンソールを起動します。  
SSMA コンソール アプリケーションを起動するのにには、次の手順を使用します。  
  
1.  開始に移動し、すべてのプログラム をポイントします。  
  
2.  クリックして、 **SQL Server Migration Assistant Sybase コマンド プロンプトの**ショートカットです。  
  
    SSMA コンソール メニューの使用状況を表示および`(/? Help)`、コンソール アプリケーションで作業を開始するためです。  
  
## <a name="using-the-ssma-console"></a>SSMA コンソールの使用  
Windows システムで、コンソールを正常に起動した後は、作業を次の手順を使用できます。  
  
1.  SSMA コンソールは、スクリプト ファイルを構成します。 このセクションの内容の詳細については、次を参照してください。[スクリプト ファイルの作成&#40;SybaseToSQL&#41;](../../ssma/sybase/creating-script-files-sybasetosql.md)です。  
  
2.  [変数の値のファイルを作成する&#40;SybaseToSQL&#41;](../../ssma/sybase/creating-variable-value-files-sybasetosql.md)  
  
3.  [サーバー接続ファイルを作成する&#40;SybaseToSQL&#41;](../../ssma/sybase/creating-the-server-connection-files-sybasetosql.md)  
  
4.  [SSMA コンソールを実行する&#40;SybaseToSQL&#41; ](../../ssma/sybase/executing-the-ssma-console-sybasetosql.md)プロジェクトのニーズに基づいています。 
  
追加機能:  
  
1.  [パスワードを指定して](http://msdn.microsoft.com/en-us/9b6a70f9-6840-4140-a059-bb7bd7ccc67c)エクスポート/インポートして、他のウィンドウのコンピューターにします。  
  
2.  [レポートの生成](http://msdn.microsoft.com/en-us/19278f6a-6d58-4867-9d71-c6228040466e)詳細な xml を表示するには、評価/変換とデータの移行のためのレポートを出力します。 更新および同期コマンドの詳細なエラー レポートを生成することもできます。  
  
## <a name="ssma-console-output-conventions"></a>SSMA コンソール出力の表記規則  
SSMA スクリプトのコマンドとオプションを実行すると、コンソール プログラムをユーザーに、コンソールの結果とメッセージ (については、エラーなど) を表示または、必要に応じて、xml 出力ファイルにリダイレクトします。 各メッセージの種類の出力には一意の色によって表されます。 白色のテキスト メッセージがスクリプト ファイルのコマンドを示しますたとえば、緑色で 1 つと、ユーザー入力を求めるを表します。  
  
![SSMAConsoleOutput_Sybase](../../ssma/sybase/media/ssmaconsoleoutput_sybase.JPG "SSMAConsoleOutput_Sybase")  
  
コンソール出力の色の解釈は、次の表に表示されます。  
  
|色|Description|  
|---------|---------------|  
|[赤]|実行中に致命的なエラー|  
|灰色|日付と時刻スタンプをユーザーにメッセージ|  
|White|スクリプト ファイルのコマンド、メッセージの種類|  
|黄|警告|  
|[緑]|ユーザー入力を求める|  
|シアン|開始、終了、および操作の結果|  
  
## <a name="see-also"></a>参照  
[SAP ASE 用 SSMA をインストールする&#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
