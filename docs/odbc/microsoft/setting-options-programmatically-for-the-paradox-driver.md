---
title: Paradox ドライバのオプションをプログラムで設定する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Paradox driver
- Paradox driver [ODBC], setting options programmatically
- desktop database drivers [ODBC], Paradox driver
- Jet-based ODBC drivers [ODBC], Paradox driver
ms.assetid: 7996d3f8-b5f5-4cac-8a66-fc96a42b603e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d04de1f0de4baca5b3f474ef9fbcf3f886e6906f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300762"
---
# <a name="setting-options-programmatically-for-the-paradox-driver"></a>Paradox ドライバーのプログラムでオプションの設定

|オプション|説明|Method|  
|------------|-----------------|------------|  
|ディレクトリ|対象ディレクトリを設定します。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)の呼び出しで**DEFAULTDIR**キーワードを使用します。|  
|照合順序|フィールドを並べ替える順序。<br /><br /> シーケンスは、ASCII (デフォルト)、国際、スウェーデン-フィンランド語、ノルウェー語 -デンマーク語です。|このオプションを動的に設定するには、呼び出しで**COLLATINGSEQUENCE**キーワードを使用[します](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)。|  
|説明|データ ソース内のデータの説明 (省略可能)。たとえば、"採用日、給与履歴、およびすべての従業員の現在の確認" などです。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)の呼び出しで**DESCRIPTION**キーワードを使用します。|  
|排他的|[**排他**] ボックスを選択すると、データベースは排他モードで開かれ、一度に 1 人のユーザーだけがアクセスできます。 排他モードで実行するとパフォーマンスが向上します。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)の呼び出しで**EXCLUSIVE**キーワードを使用します。|  
|ネットスタイル|Paradox データにアクセスするときに使用するネットワーク アクセス スタイル: Paradox 3 の場合は "3.*x"* のいずれかです。*x*または "4.*x*" パラドックス 4.*x*または 5。*x .* 「3」に設定できます。*x*" または "4.*x*" のバージョンが Paradox 4 の場合。*x*または 5。*x;* バージョンがパラドックス3の場合。*x*の場合、スタイルは "3.*x*".|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)の呼び出しで**PARADOXNETSTYLE**キーワードを使用します。|  
|ページタイムアウト|ページが削除される前にバッファー内に残る時間を 10 分の 1 秒で指定します。 デフォルトは 600 分の 1 秒 (60 秒) です。 このオプションは、ODBC ドライバを使用するすべてのデータ ソースに適用されます。<br /><br /> 固有の遅延のため、ページタイムアウトを 0 にすることはできません。 ページ タイムアウト オプションがその値を下回る場合でも、ページ タイムアウトは、固有の遅延より小さくすることはできません。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)の呼び出しで**PAGETIMEOUT**キーワードを使用します。|  
|[読み取り専用]|データベースを読み取り専用に指定します。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)の呼び出しで**READONLY**キーワードを使用します。|  
|ディレクトリの選択|アクセスするファイルを含むディレクトリを選択するためのダイアログ ボックスを表示します。<br /><br /> データ ソース ディレクトリを定義する際には、最も一般的に使用されるファイルが置かれているディレクトリを指定します。 ODBC ドライバは、このディレクトリをデフォルト ディレクトリとして使用します。 頻繁に使用する場合は、他のファイルをこのディレクトリにコピーします。 または、SELECT ステートメントのファイル名をディレクトリ名で修飾することもできます。<br /><br /> C\*から選択:\マイディル\EMP<br /><br /> または、SQL_CURRENT_QUALIFIER オプションを指定して**SQLSetConnect オプション**関数を使用して、新しい既定のディレクトリを指定できます。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)の呼び出しで**DEFAULTDIR**キーワードを使用します。|  
|ネットワーク ディレクトリの選択|paradox ロック データベースを含むディレクトリの完全パスは、Pdoxusrs.net ファイル (Paradox 4.*x)* またはParadox.netファイル(Paradox 5.*x*)。 ディレクトリにこれらのファイルが含まれていない場合、Paradox ドライバはファイルを作成します。 これらのファイルの詳細については、Paradox のドキュメントを参照してください。<br /><br /> ネットワーク ディレクトリを選択する前に、[ユーザー名] テキスト ボックスに Paradox ユーザー**名**を入力する必要があります。 [**ネットワーク ディレクトリの選択**] をクリックして、ネットワーク ディレクトリを選択します。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)の呼び出しで**PARADOXNETPATH**キーワードを使用します。|  
|[ユーザー名]|パラドックスのユーザー名。 これは、ロックが発生したときに Paradox ファイルの他のユーザーに表示される名前です。|このオプションを動的に設定するには[、SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)の呼び出しで**PARADOXUSERNAME**キーワードを使用します。|
