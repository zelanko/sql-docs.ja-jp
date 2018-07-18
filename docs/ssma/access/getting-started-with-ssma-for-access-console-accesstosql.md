---
title: Ssma for Access コンソール (AccessToSQL) 作業の開始 |Microsoft Docs
ms.prod: sql
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
ms.assetid: 8585ec16-7e0a-483a-b250-adab9b9232a3
caps.latest.revision: 21
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 0e2a7465cc46e5ca2bb69ba4c7ef61dd85bf9882
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38985404"
---
# <a name="getting-started-with-ssma-for-access-console-accesstosql"></a>Ssma for Access コンソール (AccessToSQL) 作業の開始
このセクションを起動し、Access のコンソール アプリケーションを使用する手順について説明します。 一覧表示、ここで、規則で使用されます SSMA コンソールの一般的な出力ウィンドウ。  
  
## <a name="launching-ssma-console"></a>SSMA コンソールの起動  
SSMA コンソール アプリケーションを起動するのにには、次の手順を使用します。  
  
1.  移動して**開始** をポイント**すべてのプログラム**します。  
  
2.  をクリックして、 **SQL Server Migration Assistant へのアクセス コマンド プロンプトの**ショートカット。  
  
    SSMA コンソールの使用状況 メニューを表示および`(/? Help)`、コンソール アプリケーションを使用するためです。  
  
## <a name="procedure-for-using-the-ssma-console"></a>SSMA コンソールを使用する手順  
コンソールは、Windows システムに正常に起動した後は、作業を次の手順を使用できます。  
  
1.  SSMA コンソールは、スクリプト ファイルを構成します。 このセクションの詳細については、次を参照してください。[スクリプト ファイルの作成&#40;AccessToSQL&#41;](../../ssma/access/creating-script-files-accesstosql.md)します。  
  
2.  [変数値ファイルを作成する&#40;AccessToSQL&#41;](../../ssma/access/creating-variable-value-files-accesstosql.md)  
  
3.  [サーバー接続ファイルを作成する&#40;AccessToSQL&#41;](../../ssma/access/creating-the-server-connection-files-accesstosql.md)  
  
4.  [SSMA コンソールの実行&#40;AccessToSQL&#41; ](../../ssma/access/executing-the-ssma-console-accesstosql.md)プロジェクトのニーズに基づく  
  
追加機能:  
  
1.  [パスワードを指定して](http://msdn.microsoft.com/b099d0f9-dd37-4c87-8b6f-ed0177881ea4)とエクスポート]、[ウィンドウの他のマシンにインポート  
  
2.  [レポートの生成](http://msdn.microsoft.com/abb4264a-622e-4215-af5b-14e309b8a399)詳細な xml を表示するには、評価/conversion とデータの移行のためのレポートを出力します。 更新および同期コマンドの詳細なエラー レポートを生成こともできます。  
  
## <a name="ssma-console-output-conventions"></a>SSMA コンソールの出力の規則  
SSMA スクリプト コマンドとオプションを実行すると、コンソール プログラムは、コンソールのユーザーに、結果とメッセージ (情報、エラーなど) を表示します。 または、必要な場合は、xml 出力ファイルにリダイレクトします。 一意の色では、各種のメッセージが出力に表されます。 たとえば、白のカラーにテキスト メッセージがスクリプト ファイルのコマンドを表します緑のカラーで 1 つとユーザーの入力を求めるプロンプトを表します。  
  
![SSMA コンソールの出力](../../ssma/access/media/ssmaconsoleoutput.jpg "SSMA コンソールの出力")  
  
次の表に、コンソール出力の色解釈:  
  
|色|説明|  
|---------|---------------|  
|[赤]|実行中に致命的なエラー|  
|灰色|日付と時刻スタンプをユーザーに対するメッセージ|  
|White|スクリプト ファイルのコマンド、メッセージの種類|  
|黄|警告|  
|[緑]|ユーザー入力を求めるプロンプト|  
|シアン|開始、終了日と操作の結果|  
  
## <a name="see-also"></a>参照  
[SQL Server Migration Assistant for Access をインストールします。](http://msdn.microsoft.com/dd50eebd-75df-4e0d-8c4d-88b511aae4c7)  
  
