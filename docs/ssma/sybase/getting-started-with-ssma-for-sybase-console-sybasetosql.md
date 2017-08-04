---
title: "Sybase コンソール (SybaseToSQL) for SSMA の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
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
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 239b7a8f4dbc3069e67d680b319bf426a0f917e6
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="getting-started-with-ssma-for-sybase-console-sybasetosql"></a>Sybase コンソール (SybaseToSQL) for SSMA の概要
このセクションを起動し、Sybase コンソール アプリケーションで作業を開始する手順について説明します。 一覧表示、ここで、規則ウィンドウで使用される、一般的な SSMA コンソール出力。  
  
## <a name="launching-ssma-console"></a>SSMA コンソールを起動します。  
SSMA コンソール アプリケーションを起動するのにには、次の手順を使用します。  
  
1.  先頭へ移動し、すべてのプログラム をポイントします。  
  
2.  クリックして、 **SQL Server Migration Assistant Sybase コマンド プロンプトの**ショートカットです。  
  
    SSMA コンソール メニューの使用状況を表示および`(/? Help)`、コンソール アプリケーションで作業を開始するためです。  
  
## <a name="procedure-for-using-the-ssma-console"></a>SSMA コンソールを使用する手順  
Windows システムで、コンソールを正常に起動した後、次の手順を使用して作業する可能性があります。  
  
1.  SSMA コンソールは、スクリプト ファイルを構成します。 このセクションの内容の詳細については、次を参照してください。[スクリプト ファイルの作成 & #40 です。SybaseToSQL &#41;](../../ssma/sybase/creating-script-files-sybasetosql.md) .  
  
2.  [変数値ファイル &#40; を作成します。SybaseToSQL &#41;](../../ssma/sybase/creating-variable-value-files-sybasetosql.md)  
  
3.  [サーバーの接続ファイル &#40; を作成します。SybaseToSQL &#41;](../../ssma/sybase/creating-the-server-connection-files-sybasetosql.md)  
  
4.  [SSMA コンソール &#40; を実行します。SybaseToSQL &#41;](../../ssma/sybase/executing-the-ssma-console-sybasetosql.md)プロジェクトのニーズに基づく  
  
追加機能:  
  
1.  [パスワードを指定して](http://msdn.microsoft.com/en-us/9b6a70f9-6840-4140-a059-bb7bd7ccc67c)エクスポート/その他のウィンドウのマシンにこれをインポートし、  
  
2.  [レポートの生成](http://msdn.microsoft.com/en-us/19278f6a-6d58-4867-9d71-c6228040466e)詳細な xml を表示するには、評価/conversion とデータの移行のためのレポートを出力します。 詳細なエラー レポートを更新および同期コマンドの生成もできます。  
  
## <a name="ssma-console-output-conventions"></a>SSMA コンソール出力の表記規則  
SSMA スクリプトのコマンドとオプションを実行すると、コンソール プログラムは、コンソールのユーザーに結果とメッセージ (については、エラーなど) を表示または、必要な場合は、xml 出力ファイルにリダイレクトします。 各メッセージの種類の出力には一意の色によって表されます。 白色のテキスト メッセージがスクリプト ファイルのコマンドを示しますたとえば、緑色で 1 つと、ユーザー入力を求めるを表します。  
  
![SSMAConsoleOutput_Sybase](../../ssma/sybase/media/ssmaconsoleoutput_sybase.JPG "SSMAConsoleOutput_Sybase")  
  
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
[SSMA の Sybase &#40; のインストールSybaseToSQL &#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
  

