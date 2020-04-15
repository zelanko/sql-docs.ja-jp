---
title: テキスト ファイル ドライバのオプションをプログラムで設定する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], setting options programmatically
- ODBC desktop database drivers [ODBC], text file driver
- desktop database drivers [ODBC], text file driver
- Jet-based ODBC drivers [ODBC], text file driver
ms.assetid: cbde2ca1-5d4e-4444-a371-a72f3ac4d92a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e19c3b49479047bc92a7b6f72359d4951d8df16e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300752"
---
# <a name="setting-options-programmatically-for-the-text-file-driver"></a>テキスト ファイル ドライバーのプログラムでオプションの設定

|オプション|説明|Method|  
|------------|-----------------|------------|  
|データ ソース名|給与や人事など、データ ソースを識別する名前。|このオプションを動的に設定するには、DSN**キーワードを**使用して[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)を呼び出します。|  
|フォーマットの定義|[**テキスト形式の定義**] ダイアログ ボックスが表示され、データ ソース ディレクトリ内の個々のテーブルのスキーマを指定できます。|このオプションは、呼び出しによって動的に設定[できません](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)。|  
|説明|データ ソース内のデータの説明 (省略可能)。たとえば、"採用日、給与履歴、およびすべての従業員の現在の確認" などです。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)の呼び出しで**DESCRIPTION**キーワードを使用します。|  
|ディレクトリ|対象ディレクトリを選択します。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)の呼び出しで**DEFAULTDIR**キーワードを使用します。|  
|拡張機能リスト|データ ソース上のテキスト ファイルのファイル名拡張子を一覧表示します。 テキスト ドライバーを使用すると、CREATE TABLE ステートメントを実行するときに拡張子のないファイルが作成されます。 他のドライバーは、拡張子が指定されていない場合、既定の拡張子を持つファイルを作成します。 拡張子が .txt のファイルを作成するには、拡張子を名前に含める必要があります。 [**テキスト形式の定義**] ダイアログ ボックスの [*] で拡張子を付けずにファイルを表示するには は、拡張機能リストに追加する必要があります。|このオプションを動的に設定するには、**拡張**キーワードを使用して[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)を呼び出します。|  
|[読み取り専用]|データベースを読み取り専用に指定します。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)の呼び出しで**READONLY**キーワードを使用します。|  
|スキャンする行|各列のデータ型を決定するためにスキャンする行数。 データ型は、見つかったデータの最大種類を指定して決定されます。 列に対して推測されたデータ型と一致しないデータが検出された場合、そのデータ型は NULL 値として返されます。<br /><br /> テキスト ドライバの場合、スキャンする行数として 1 ~ 32767 の数値を入力できます。ただし、この値は常に 25 に設定されます。 (制限を超えた数値はエラーを返します。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)の呼び出しで**MAXSCANROWS**キーワードを使用します。|  
|ディレクトリの選択|アクセスするファイルを含むディレクトリを選択するためのダイアログ ボックスを表示します。<br /><br /> データ ソース ディレクトリを定義する際には、最も一般的に使用されるファイルが置かれているディレクトリを指定します。 ODBC ドライバは、このディレクトリをデフォルト ディレクトリとして使用します。 頻繁に使用する場合は、他のファイルをこのディレクトリにコピーします。 または、SELECT ステートメントのファイル名をディレクトリ名で修飾することもできます。`SELECT * FROM C:\MYDIR\EMP`<br /><br /> または、SQL_CURRENT_QUALIFIER オプションを指定して**SQLSetConnect オプション**関数を使用して、新しい既定のディレクトリを指定できます。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)の呼び出しで**DEFAULTDIR**キーワードを使用します。|
