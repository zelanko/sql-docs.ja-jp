---
title: トレース オプションの設定 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Analyzer tracing [ODBC]
- ODBC data source administrator [ODBC], tracing options
- tracing options [ODBC], ODBC data source administrator
ms.assetid: 44404a79-b716-4bc1-9ffb-70cd8239d237
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 21bee5d903459423a134389e62db844f5f63c9c1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307200"
---
# <a name="setting-tracing-options"></a>トレース オプションの設定
**[ODBC データ ソース アドミニストレータ**] ダイアログ ボックスの [**トレース**] タブでは、ODBC 関数呼び出しのトレース方法を構成できます。  
  
## <a name="how-tracing-works"></a>トレースのしくみ  
 [**トレース**] タブからトレースを開始すると、ドライバー マネージャーは、以降に実行されるすべてのアプリケーションのすべての ODBC 関数呼び出しを記録します。 トレースを開始する前に実行されているアプリケーションからの ODBC 関数呼び出しはログに記録されません。 ODBC 関数呼び出しは、指定したログ ファイルに記録されます。  
  
 [トレースを停止する] をクリックした後にのみ **、トレースが**停止します。 トレースがオンの間は、ログ ファイルが増加し続け、すべての ODBC アプリケーションのパフォーマンスに影響を与えることを覚えておいてください。  
  
 トレースの詳細については、「[トレース](../../odbc/reference/develop-app/tracing.md)」を参照してください。  
  
### <a name="changes-in-odbc-tracing"></a>ODBC トレースの変更点  
 MDAC 2.7 SP2 より前のバージョンでは、ODBC トレースはコンピュータ全体でしか実行できませんでした。 これには、他のローカル ユーザー アカウントや組み込みのセキュリティ プリンシパル (ローカル サービスやネットワーク サービスなど) の代わりに作成または実行されるプロセスに対して発生する可能性のある ODBC 関連のアクティビティのトレースが含まれます。  
  
 既定では、ODBC トレースではユーザー単位のモードが使用されるようになりました。 ただし、ローカル管理者の場合でも、ODBC データ ソース アドミニストレータを使用して、コンピュータ全体のトレースを有効にできます。  
  
 ODBC トレース モードを設定するには、次の手順を実行します。  
  
1.  必要に応じて、ローカル管理者グループのメンバーシップを持つアカウントを使用してログオンします。  
  
2.  管理ツールから、ODBC データ ソース アドミニストレータを開きます。  
  
3.  [トレース] タブ**を**クリックします。  
  
4.  **[すべてのユーザー ID に対してマシン全体のトレース**] チェック ボックスを使用してトレース モードを構成します。  
  
5.  マシン全体のトレースを有効にするには、チェック ボックスをオンにします。  
  
6.  ユーザーごとのトレースに戻るには、チェック ボックスをオフにします。  
  
7.  **[Apply]** をクリックします。  
  
> [!NOTE]  
>  既に 1 つのモードでトレースを開始している場合は、トレースを停止し、モードを正常に変更するには、もう一方のモードに切り替える必要があります。  
  
> [!IMPORTANT]  
>  マシン全体のトレースは、必要な場合にのみ有効にしてください。それ以外の場合は、オフのままにする必要があります。  
  
## <a name="visual-studio-analyzer-tracing"></a>ビジュアル スタジオ アナライザー トレース  
  
> [!IMPORTANT]  
>  Windows 8 で最初に Visual Studio アナライザーのサポートが削除されました (Visual Studio アナライザーは、以前のバージョンの Visual Studio にのみ含まれていました)。 代替トラブルシューティングメカニズムを使用するには、BID トレースを使用します。  
  
 Visual Studio ® アナライザ トレースは、ODBC レイヤーに関するパフォーマンスとデバッグ情報を提供します。 すべての送信イベントは、ODBC コンポーネントで費やされた時間に関してできるだけ正確な画像を表示するために、トップレベル インターフェイスで発生します。 Visual Studio アナライザー のトレースでは、ソースのセットアップ時に登録するイベント ソースが必要です。 この種のトレースの詳細については、Visual Studio のドキュメントを参照してください。
