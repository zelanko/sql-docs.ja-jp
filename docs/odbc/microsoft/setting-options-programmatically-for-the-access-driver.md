---
title: アクセスドライバのオプションをプログラムで設定する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], setting options programmatically
- ODBC desktop database drivers [ODBC], Access driver
- Jet-based ODBC drivers [ODBC], Access driver
- desktop database drivers [ODBC], Access driver
ms.assetid: 1690eb71-0cd3-4c00-9e15-f6a3ac5316dd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9a90f0a20569a2a0a5bb93dec7aa4b95b50093dc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300792"
---
# <a name="setting-options-programmatically-for-the-access-driver"></a>プログラムで Access ドライバーのオプションの設定

|オプション|説明|Method|  
|------------|-----------------|------------|  
|バッファー サイズ|ディスクとの間でデータを転送するために使用される内部バッファのサイズ (KB 単位)。 デフォルトのバッファ サイズは 2048 KB です(2048 として表示されます)。 256 で割り切れる整数値を入力できます。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)の呼び出しで MAXBUFFERSIZE キーワードを使用します。|  
|データ ソース名|給与や人事など、データ ソースを識別する名前。|このオプションを動的に設定するには、DSN**キーワードを**使用して[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)を呼び出します。|  
|データベース|データベースを選択または作成しなくても、Access データ ソースを設定できます。 セットアップ時にデータベースが提供されていない場合、データ ソースに接続するときにデータベース ファイルを選択するように求められます。|このオプションを動的に設定するには **、DBQ**キーワードを使用して[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)を呼び出します。|  
|説明|データ ソース内のデータの説明 (省略可能)。たとえば、"採用日、給与履歴、およびすべての従業員の現在の確認" などです。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)の呼び出しで**DESCRIPTION**キーワードを使用します。|  
|排他的|[**排他**] ボックスを選択すると、データベースは排他モードで開かれ、一度に 1 人のユーザーだけがアクセスできます。 排他モードで実行するとパフォーマンスが向上します。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)の呼び出しで**EXCLUSIVE**キーワードを使用します。|  
|暗黙的なコミット同期|トランザクションの外部で行われた変更をデータベースに書き込む方法を決定します。 この値は、最初は "Yes" に設定されています。|このオプションは、Microsoft Access ドライバの **[詳細オプションの設定]** ダイアログ ボックスに含まれています。|  
|ページタイムアウト|ページが (使用されていない場合) がバッファー内に残ってから削除されるまでの時間をミリ秒単位で指定します。 Access ドライバの場合、デフォルトは 500 ミリ秒 (0.5 秒) です。 このオプションは、ODBC ドライバを使用するすべてのデータ ソースに適用されます。<br /><br /> 固有の遅延のため、ページタイムアウトを 0 にすることはできません。 ページ タイムアウト オプションがその値を下回る場合でも、ページ タイムアウトは、固有の遅延より小さくすることはできません。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)の呼び出しで**PAGETIMEOUT**キーワードを使用します。|  
|[読み取り専用]|データベースを読み取り専用に指定します。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)の呼び出しで**READONLY**キーワードを使用します。|  
|システム データベース|アクセスする Access データベースで使用する Access システム データベースの完全パス。<br /><br /> [**システム データベース**] ボタンをクリックして、使用するシステム データベースを選択します。 ODBC Access ドライバは、名前とパスワードを入力するよう求めるプロンプトを表示します。 既定の名前は Admin で、管理者ユーザーの Microsoft Access の既定のパスワードは空の文字列です。<br /><br /> Microsoft Access データベースのセキュリティを強化するには、新しいユーザーを作成して管理者ユーザーを削除し、管理者ユーザーを削除するか、管理者ユーザーがアクセスできるオブジェクトを変更します。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)の呼び出しで**SYSTEMDB**キーワードを使用します。|  
|Threads|使用するエンジンのバックグラウンド スレッドの数。 Access ドライバの場合、この値はデフォルトで 3 ですが、変更できます。 データベース内に大量のアクティビティがある場合は、スレッド数を増やすこともできます。<br /><br /> このオプションは、Microsoft Access ドライバの **[詳細オプションの設定]** ダイアログ ボックスに含まれています。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)の呼び出しで**THREADS**キーワードを使用します。|  
|ユーザーコミットシンク|Access ドライバーが明示的なユーザー定義のトランザクションを非同期的に実行するかどうかを決定します。 この値は、最初は "Yes" に設定されています。<br /><br /> このオプションを False に設定すると、マルチユーザー環境で予期しない結果が生じる可能性があります。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)の呼び出しで**USERCOMMITSYNC**キーワードを使用します。|
