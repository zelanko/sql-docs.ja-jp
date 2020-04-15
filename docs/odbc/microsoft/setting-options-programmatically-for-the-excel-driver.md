---
title: Excel ドライバのオプションをプログラムで設定する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], Excel driver
- desktop database drivers [ODBC], Excel driver
- ODBC desktop database drivers [ODBC], Excel driver
- Excel driver [ODBC], setting options programmatically
ms.assetid: b5ee3636-4591-427a-a65a-a2d5926fcc1a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1fcd5542e4beee1f7c7a30d5e0ee9f2815a3f0b6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300772"
---
# <a name="setting-options-programmatically-for-the-excel-driver"></a>Excel ドライバーのプログラムでオプションの設定

|オプション|説明|Method|  
|------------|-----------------|------------|  
|データ ソース名|給与や人事など、データ ソースを識別する名前。|このオプションを動的に設定するには、DSN**キーワードを**使用して[SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)を呼び出します。|  
|データベース|データベースを選択または作成しなくても、Access データ ソースを設定できます。 セットアップ時にデータベースが提供されていない場合、データ ソースに接続するときにデータベース ファイルを選択するように求められます。|このオプションを動的に設定するには **、DBQ**キーワードを使用して[SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)を呼び出します。|  
|説明|データ ソース内のデータの説明 (省略可能)。たとえば、"採用日、給与履歴、およびすべての従業員の現在の確認" などです。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)の呼び出しで**DESCRIPTION**キーワードを使用します。|  
|ディレクトリ|現在選択されているディレクトリが表示されます。<br /><br /> Excel 3.0/4.0 ファイルの場合、パス表示には "ディレクトリ" というラベルが付けられますが、Excel 5.0、7.0、または 97 ファイルの場合は、パス表示のラベルが 「ワークブック」です。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)の呼び出しで**DEFAULTDIR**キーワードを使用します。|  
|[読み取り専用]|データベースを読み取り専用に指定します。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)の呼び出しで**READONLY**キーワードを使用します。|  
|スキャンする行|各列のデータ型を決定するためにスキャンする行数。 データ型は、見つかったデータの最大種類を指定して決定されます。 列に対して推測されたデータ型と一致しないデータが検出された場合、そのデータ型は NULL 値として返されます。<br /><br /> Excel ドライバの場合、スキャンする行には 1 から 16 までの数値を入力できます。 デフォルト値は 8 です。0 に設定すると、すべての行がスキャンされます。 (制限を超えた数値はエラーを返します。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)の呼び出しで**MAXSCANROWS**キーワードを使用します。|  
|ディレクトリの選択|アクセスするファイルを含むディレクトリを選択するためのダイアログ ボックスを表示します。<br /><br /> Access 以外のすべてのドライバに対してデータ ソース ディレクトリを定義する場合は、最もよく使用するファイルが格納されているディレクトリを指定します。 ODBC ドライバは、このディレクトリをデフォルト ディレクトリとして使用します。 頻繁に使用する場合は、他のファイルをこのディレクトリにコピーします。 または、SELECT ステートメントのファイル名をディレクトリ名で修飾することもできます。<br /><br /> C\*から選択:\マイディル\EMP<br /><br /> または、SQL_CURRENT_QUALIFIER オプションを指定して**SQLSetConnect オプション**関数を使用して、新しい既定のディレクトリを指定できます。<br /><br /> Excel 3.0 または 4.0 ファイルの場合、パス表示には「ディレクトリ」というラベルが付き、パス選択ボタンのラベルは「ディレクトリの選択」です。 Excel 5.0、7.0、または 97 ファイルの場合、パス表示には 「ワークブック」というラベルが付き、パス選択ボタンのラベルは「ワークブックの選択」です。 データ ソース ディレクトリを定義する場合は、最も一般的に使用される Excel ファイルが Microsoft Excel 3.0/4.0 用に配置されているディレクトリ、またはブック ファイルが Microsoft Excel 5.0、7.0、または 97 用のディレクトリを指定します。 現在**のディレクトリを使用**は、Excel 5.0、7.0、および 97 では無効です。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)の呼び出しで**DEFAULTDIR**キーワードを使用します。|
