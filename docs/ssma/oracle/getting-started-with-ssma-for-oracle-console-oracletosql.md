---
title: Ssma for Oracle コンソール (OracleToSQL) 作業の開始 |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Oracle Console, Console Output Conventions
- Oracle Console, Launching Console
ms.assetid: 667a5e4a-6848-4973-a72d-1287f64718ac
caps.latest.revision: 31
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 86b8adc8841e06d91d164c2c35e2329511ac0e28
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38985754"
---
# <a name="getting-started-with-ssma--for-oracle-console-oracletosql"></a>Ssma for Oracle コンソール (OracleToSQL) 作業の開始
このセクションを起動し、Oracle のコンソール アプリケーションを使用する手順について説明します。 一覧表示、ここで、規則で使用されます SSMA コンソールの一般的な出力ウィンドウ。  
  
## <a name="launching-ssma-console"></a>SSMA コンソールの起動  
SSMA コンソール アプリケーションを起動するのにには、次の手順を使用します。  
  
1.  移動して**開始** をポイント**すべてのプログラム**します。  
  
2.  をクリックして、  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant Oracle コマンド プロンプトの**ショートカット。  
  
    SSMA コンソールの使用状況 メニューを表示および`(/? Help)`、コンソール アプリケーションを使用するためです。  
  
## <a name="procedure-for-using-the-ssma-console"></a>SSMA コンソールを使用する手順  
コンソールは、Windows システムに正常に起動した後は、作業を次の手順を使用できます。  
  
1.  SSMA コンソールは、スクリプト ファイルを構成します。 このセクションの詳細については、次を参照してください。[スクリプト ファイルの作成&#40;OracleToSQL&#41; ](../../ssma/oracle/creating-script-files-oracletosql.md)します。  
  
2.  [変数値ファイルを作成する&#40;OracleToSQL&#41;](../../ssma/oracle/creating-variable-value-files-oracletosql.md)  
  
3.  [サーバー接続ファイルを作成する&#40;OracleToSQL&#41;](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)  
  
4.  [SSMA コンソールの実行&#40;OracleToSQL&#41; ](../../ssma/oracle/executing-the-ssma-console-oracletosql.md)プロジェクトのニーズに基づく  
  
追加機能:  
  
1.  [パスワードを指定して](http://msdn.microsoft.com/8c7d9f8e-06bb-476c-bbd2-15b61d5bba3c)とエクスポート]、[ウィンドウの他のマシンにインポート  
  
2.  [レポートの生成](http://msdn.microsoft.com/ccad6262-01e1-447a-bd2b-c105154c80ce)詳細な xml を表示するには、評価/conversion とデータの移行のためのレポートを出力します。 更新および同期コマンドの詳細なエラー レポートを生成こともできます。  
  
## <a name="ssma-console-output-conventions"></a>SSMA コンソールの出力の規則  
SSMA スクリプト コマンドとオプションを実行すると、コンソール プログラムは、コンソールのユーザーに、結果とメッセージ (情報、エラーなど) を表示します。 または、必要な場合は、xml 出力ファイルにリダイレクトします。 一意の色では、各種のメッセージが出力に表されます。 たとえば、白のカラーにテキスト メッセージがスクリプト ファイルのコマンドを表します緑のカラーで 1 つとユーザーの入力を求めるプロンプトを表します。  
  
![Ssmaconsoleoutput_oracle](../../ssma/db2/media/ssmaconsoleoutput_oracle.jpg "ssmaconsoleoutput_oracle")  
  
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
[SSMA for Oracle のインストール](http://msdn.microsoft.com/9211013a-ab24-4c52-9b26-87994b35e502)  
  
