---
title: dBASE ドライバのオプションをプログラムで設定する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], DBasedriver
- desktop database drivers [ODBC], DBasedriver
- DBase driver [ODBC], setting options programmatically
- ODBC desktop database drivers [ODBC], DBasedriver
ms.assetid: 336d0fd4-5448-4d8c-b7d9-49e857228e36
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 75889d9ff3ccfe01f9b8d5141df7774205522815
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300782"
---
# <a name="setting-options-programmatically-for-the-dbase-driver"></a>dBASE ドライバーのプログラムでオプションの設定

|オプション|説明|Method|  
|------------|-----------------|------------|  
|おおよその行数|テーブル サイズの統計情報を近似するかどうかを決定します。 このオプションは、ODBC ドライバを使用するすべてのデータ ソースに適用されます。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)の呼び出しで**STATISTICS**キーワードを使用します。|  
|照合順序|フィールドを並べ替える順序。<br /><br /> シーケンスは、ASCII (デフォルト) または国際形式のいずれかです。|このオプションを動的に設定するには、呼び出しで**COLLATINGSEQUENCE**キーワードを使用[します](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)。|  
|データ ソース名|給与や人事など、データ ソースを識別する名前。|このオプションを動的に設定するには、DSN**キーワードを**使用して[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)を呼び出します。|  
|データベース|データベースを選択または作成しなくても、Access データ ソースを設定できます。 セットアップ時にデータベースが提供されていない場合、ユーザーはデータ ソースに接続するときにデータベース ファイルを選択するように求められます。|このオプションを動的に設定するには **、DBQ**キーワードを使用して[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)を呼び出します。|  
|説明|データ ソース内のデータの説明 (省略可能)。たとえば、"採用日、給与履歴、およびすべての従業員の現在の確認" などです。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)の呼び出しで**DESCRIPTION**キーワードを使用します。|  
|排他的|[**排他**] ボックスを選択すると、データベースは排他モードで開かれ、一度に 1 人のユーザーだけがアクセスできます。 排他モードで実行すると、パフォーマンスが向上します。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)の呼び出しで**EXCLUSIVE**キーワードを使用します。|  
|ページタイムアウト|ページが削除される前に、そのページがバッファー内に残っている期間を 10 分の 1 秒で指定します。 デフォルトは 600 分の 1 秒 (60 秒) です。 このオプションは、ODBC ドライバを使用するすべてのデータ ソースに適用されます。<br /><br /> 固有の遅延のため、ページタイムアウトを 0 にすることはできません。 ページ タイムアウト オプションがその値を下回る場合でも、ページ タイムアウトは、固有の遅延より小さくすることはできません。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)の呼び出しで**PAGETIMEOUT**キーワードを使用します。|  
|[読み取り専用]|データベースを読み取り専用に指定します。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)の呼び出しで**READONLY**キーワードを使用します。|  
|ディレクトリの選択|アクセスするファイルが含まれているディレクトリを選択するためのダイアログ ボックスが表示されます。<br /><br /> データ ソース ディレクトリを定義する場合は、最も頻繁に使用するファイルが格納されているディレクトリを指定します。 ODBC ドライバは、このディレクトリをデフォルト ディレクトリとして使用します。 頻繁に使用する場合は、他のファイルをこのディレクトリにコピーします。 または、SELECT ステートメントのファイル名をディレクトリ名で修飾することもできます。<br /><br /> C\*から選択:\マイディル\EMP<br /><br /> または、SQL_CURRENT_QUALIFIER オプションを指定して**SQLSetConnect オプション**関数を使用して、新しい既定のディレクトリを指定できます。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)の呼び出しで**DEFAULTDIR**キーワードを使用します。|  
|削除された行を表示|削除済みとしてマークされた行を取得または配置できるかどうかを指定します。 オフにすると、削除された行は表示されません。選択した場合、削除された行は削除されていない行と同じように扱われます。 既定値はオフです。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)の呼び出しで**DELETED**キーワードを使用します。|
