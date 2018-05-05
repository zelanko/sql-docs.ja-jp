---
title: トレース オプションを設定 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Analyzer tracing [ODBC]
- ODBC data source administrator [ODBC], tracing options
- tracing options [ODBC], ODBC data source administrator
ms.assetid: 44404a79-b716-4bc1-9ffb-70cd8239d237
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 224832615cbbfb20d61240015fed9b683da6e6c5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="setting-tracing-options"></a>トレース オプションの設定
**トレース**のタブ、 **ODBC データ ソース アドミニストレーター**  ダイアログ ボックスでは、ODBC 関数呼び出しをトレースする方法を構成することができます。  
  
## <a name="how-tracing-works"></a>トレースのしくみ  
 トレースを開始すると、**トレース** タブ、ドライバー マネージャー、後でアプリケーションの実行のすべてのすべての ODBC 関数呼び出しが記録されます。 トレースが開始される前に実行されているアプリケーションから ODBC 関数呼び出しは記録されません。 ODBC 関数呼び出しは、指定したログ ファイルに記録されます。  
  
 クリックした後にのみトレースは停止**今すぐトレースを停止**です。 トレースを増やすには、ログ ファイルが継続し、すべての ODBC アプリケーションのパフォーマンスに影響する注意してください。  
  
 トレースの詳細については、次を参照してください。[トレース](../../odbc/reference/develop-app/tracing.md)です。  
  
### <a name="changes-in-odbc-tracing"></a>ODBC のトレースの変更  
 MDAC 2.7 SP2 より前は、トレースが任意の id で実行されているすべての ODBC アプリケーションの公開の詳細をキャプチャするマシン全体で発生する ODBC トレースがのみ許可されます。 これには、プロセスの作成またはその他のローカル ユーザー アカウントとローカル サービスおよびネットワーク サービスなどの組み込みのセキュリティ プリンシパルに代わって実行される可能性があります ODBC に関連するアクティビティのトレースが含まれています。  
  
 既定では、ODBC を使用してユーザーごとのモードでは今すぐをトレースします。 ローカル管理者の場合は、ただし、ことができますも有効にするコンピューター全体のトレース、ODBC データ ソース アドミニストレーターを使用して、します。  
  
 ODBC トレース モードを構成します。  
  
1.  必要がある場合は、ローカルの Administrators グループのメンバーシップを持つアカウントを使用してログオンします。  
  
2.  管理ツールは、ODBC データ ソース アドミニストレーターを開きます。  
  
3.  クリックして、**トレース**タブです。  
  
4.  トレース モードを使用して、構成、**コンピューター全体のトレースをすべてのユーザー id を** チェック ボックス。  
  
5.  コンピューター全体のトレースを有効にするには、チェック ボックスを選択します。  
  
6.  ユーザーあたりのトレースを返すには、チェック ボックスをオフにします。  
  
7.  **[適用]** をクリックします。  
  
> [!NOTE]  
>  既に 1 つのモードでトレースを開始しているがある場合にトレースを停止し、正常に変更するモードの他のモードに切り替えます。  
  
> [!IMPORTANT]  
>  必要な場合、コンピューター全体のトレースを有効のみ必要があります。左のそれ以外の場合、無効になっています。  
  
## <a name="visual-studio-analyzer-tracing"></a>Visual Studio Analyzer のトレース  
  
> [!IMPORTANT]  
>  Visual Studio Analyzer のサポートが以降 (Visual Studio Analyzer のみに含まれていました Visual Studio の古いバージョンです。) Windows 8 では削除されました。 トラブルシューティング メカニズムの代わりの BID トレースを使用します。  
  
 Visual Studio® アナライザー トレース、パフォーマンスと、ODBC 層に関するデバッグ情報を提供します。 すべての送信イベントは、最上位のインターフェイスとして表示する正確な画像、できるだけ ODBC コンポーネントに費やされた時間の関連で実行されます。 Visual Studio Analyzer のトレース ソースを設定するときに登録するすべてのイベント ソースが必要です。 このようなトレースの詳細については、Visual Studio のマニュアルを参照してください。
