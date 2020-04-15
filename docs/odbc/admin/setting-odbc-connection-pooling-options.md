---
title: ODBC 接続プールオプションの設定 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection pooling [ODBC]
- ODBC data source administrator [ODBC], connection pooling options
- ODBC data source administrator [ODBC], performance monitoring
ms.assetid: 037e2f78-f204-40f4-b4ab-d9cdf562012b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1d8e66c506518b77320347ce9120254aa1cae287
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307199"
---
# <a name="setting-odbc-connection-pooling-options"></a>ODBC 接続プール オプションの設定
接続プールを使用すると、アプリケーションは、使用するたびに再確立する必要のない接続プールからの接続を使用できます。 **[ODBC データ ソース アドミニストレータ**] ダイアログ ボックスの [**接続プール**] タブを使用して、パフォーマンス監視を有効または無効にできます。 ドライバ名をダブルクリックして、接続タイムアウト期間を設定します。  
  
 ドライバ レベルでは、CPTimeout レジストリ値によって接続プールが有効になります。 このドライバーごとの選択的な有効化を有効にすると、システム管理者は、それをサポートできるドライバーのみの接続プールを有効にできます。 これは、ドライバのセットアップ プログラム中に CPTimeout の既定値を設定することによって実現されます。 ドライバ名をダブルクリックして、接続タイムアウト期間を設定します。  
  
 接続プールの詳細については[、「ODBC 接続プール](../../odbc/reference/develop-app/driver-manager-connection-pooling.md)」を参照してください。  
  
## <a name="performance-monitoring"></a>パフォーマンス監視  
 パフォーマンス・モニターは、さまざまな統計を記録することによって、接続のパフォーマンスを追跡します。 これらの統計は、次のような項目を含むように開発者がカスタマイズできます。  
  
|カウンター|定義|  
|-------------|----------------|  
|1 秒あたりの ODBC ハードコネクションカウンタ|サーバーに対して行われた実際の接続数 (1 秒あたり)。 初めて環境に大きな負荷がかかると、このカウンタは非常に迅速に上がります。 数秒後、ゼロにドロップします。 これは、接続プーリングが機能している場合の通常の状況です。 サーバーへの接続が確立されると、再利用のためにプールに使用され、配置されます。|  
|1 秒あたりの ODBC ハード切断カウンタ|サーバーに対して発行された 1 秒あたりのハード切断の数。 これらは、接続プールによって解放されるサーバーへの実際の接続です。 この値は、システム上のすべてのクライアントを停止し、接続がタイムアウトし始めるとゼロから増加します。|  
|1 秒あたりの ODBC ソフトコネクション カウンタ数|プールが 1 秒あたりに満たした接続の数、つまり、ユーザーに渡されたプールからの接続。 このカウンタは、プーリングが機能しているかどうかを示します。 サーバーの負荷によっては、毎秒 40 ~ 60 のソフト接続を表示する場合もあります。|  
|1 秒あたりの ODBC ソフト切断カウンタ|アプリケーションが発行した 1 秒あたりの切断数。 アプリケーションが解放または切断されると、接続はプールに戻されます。|  
|ODBC 現在アクティブな接続カウンタ|現在使用中のプール内の接続数。|  
|ODBC 現在の空き接続カウンタ|プールで使用可能な現在の空き接続の数。 これらは、使用可能なライブ接続です。|  
|現在アクティブなプール|現在アクティブなプールの数。 このカウンターは、接続プール内の接続を管理するドライバー用に、Windows 8 で追加されました。 詳細については、「[ドライバ対応接続プール](../../odbc/reference/develop-app/driver-aware-connection-pooling.md)」を参照してください。|  
|作成されたプール|アクティブなプールと削除されたプールを含む、アクティブなプールの数。 このカウンターは、接続プール内の接続を管理するドライバー用に、Windows 8 で追加されました。 詳細については、「[ドライバ対応接続プール](../../odbc/reference/develop-app/driver-aware-connection-pooling.md)」を参照してください。|  
  
 独自の監視パラメーターを指定する必要があります。 パフォーマンス監視のサンプルは、このバージョンの ODBC に含まれています。
