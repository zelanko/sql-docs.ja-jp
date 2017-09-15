---
title: "ODBC 接続プールのオプションを設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection pooling [ODBC]
- ODBC data source administrator [ODBC], connection pooling options
- ODBC data source administrator [ODBC], performance monitoring
ms.assetid: 037e2f78-f204-40f4-b4ab-d9cdf562012b
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6e22b3c2c09f4bc356b54ed2ecb73988f0de2764
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setting-odbc-connection-pooling-options"></a>ODBC 接続プールのオプションの設定
接続プールにより、アプリケーションを使用するたびに再確立する必要がない接続プールから接続を使用します。 使用することができます、**接続プール**のタブ、 **ODBC データ ソース アドミニストレーター**  ダイアログ ボックスを有効にし、パフォーマンスの監視を無効にします。 接続タイムアウト期間を設定するドライバー名をダブルクリックします。  
  
 ドライバー レベルで接続プールは CPTimeout レジストリ値で有効にします。 このドライバーごとのオプションを選択を有効にすると、それをサポートするドライバーだけに対する接続プールを有効にするシステム管理者ができます。 これは、ドライバーのセットアップ プログラムの中に CPTimeout の既定値の設定で実現されます。 接続タイムアウト期間を設定するドライバー名をダブルクリックします。  
  
 接続プールの詳細については、次を参照してください。 [ODBC 接続プーリング](../../odbc/reference/develop-app/driver-manager-connection-pooling.md)です。  
  
## <a name="performance-monitoring"></a>パフォーマンス監視  
 さまざまな統計情報を記録することによって接続のパフォーマンスを追跡するパフォーマンスを監視します。 これらの統計情報は、次のように項目を含める開発者によってカスタマイズできます。  
  
|カウンター|定義|  
|-------------|----------------|  
|1 秒あたりの ODBC ハード接続カウンター|サーバーに加えられた 1 秒あたりの実際の接続の数。 初めて環境内の実行、負荷の高いこのカウンターは上がる非常に短時間です。 、数秒後に、ゼロにそれが削除されます。 これは、接続プールが使用する場合、通常の状況です。 サーバーへの接続が確立されるが使用され、プールを再利用するために配置します。|  
|ODBC ハード切断 1 秒あたりのカウンター|サーバーに発行された 1 秒あたりの切断ハード数。 これらは、接続のプールでリリースされているサーバーへの実際の接続です。 システム上のすべてのクライアントを停止して、接続がタイムアウトする開始時に、この値が 0 から増加します。|  
|1 秒あたりの ODBC ソフト接続カウンター|1 秒あたりのプールでなければ接続の数、つまりからの接続プールがユーザーに渡すことです。 このカウンターは、プールが動作しているかどうかを示します。 サーバーで、負荷に応じて 1 秒あたり 40 ~ 60 のソフト接続を表示するは珍しいことではありません。|  
|1 秒あたりの ODBC ソフト切断カウンター|アプリケーションによって発行された 1 秒あたりの数を切断します。 アプリケーションでは、リリース、接続が切断または、接続がプールに配置されます。|  
|ODBC の現在アクティブな接続のカウンター|現在使用されている、プール内の接続の数。|  
|ODBC 現在無料接続カウンター|使用可能な空き接続プール内の現在数。 これらは、使用可能なライブ接続です。|  
|現在アクティブなプールします。|現在アクティブなプールの数。 このカウンターは、接続プール内の接続を管理するドライバーを Windows 8 で追加されました。 詳細については、次を参照してください。[ドライバー対応接続プール](../../odbc/reference/develop-app/driver-aware-connection-pooling.md)です。|  
|作成されたプール|作業中に、削除のプールを含む、アクティブなプールの数。 このカウンターは、接続プール内の接続を管理するドライバーを Windows 8 で追加されました。 詳細については、次を参照してください。[ドライバー対応接続プール](../../odbc/reference/develop-app/driver-aware-connection-pooling.md)です。|  
  
 独自の監視パラメーターを指定する必要があります。 パフォーマンスの監視用のサンプルは、ODBC のこのバージョンに付属されています。
