---
title: DBASE ドライバーのプログラムによるオプションの設定 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], DBasedriver
- desktop database drivers [ODBC], DBasedriver
- DBase driver [ODBC], setting options programmatically
- ODBC desktop database drivers [ODBC], DBasedriver
ms.assetid: 336d0fd4-5448-4d8c-b7d9-49e857228e36
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 517d7053b651c6698e8b8ded7901d9dbcf1168f9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="setting-options-programmatically-for-the-dbase-driver"></a>DBASE ドライバーのプログラムによるオプションの設定
|オプション|Description|方法|  
|------------|-----------------|------------|  
|おおよその行の数|テーブル サイズの統計情報を概算するかどうかを判断します。 このオプションは、ODBC ドライバーを使用するすべてのデータ ソースに適用されます。|このオプションを動的に設定するには、使用、**統計**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)です。|  
|照合順序|フィールドが並べ替えられたシーケンスです。<br /><br /> シーケンスを指定できます: 並べ (既定)。|このオプションを動的に設定するには、使用、 **COLLATINGSEQUENCE**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)です。|  
|Data Source Name|給与担当者など、データ ソースを識別する名前。|このオプションを動的に設定するには、使用、 **DSN**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)です。|  
|データベース|Microsoft Access データ ソースは、選択するか、データベースを作成することがなくを設定できます。 セットアップ時にデータベースが指定されていない場合は、ファイルを選択して、データベース、データ ソースに接続するときにユーザーが求められます。|このオプションを動的に設定するには、使用、 **DBQ**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)です。|  
|Description|データ ソース内のデータの説明 (オプション)たとえば、「雇用日、給与履歴、およびすべての従業員の現在のレビューします。」|このオプションを動的に設定するには、使用、**説明**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)です。|  
|[Exclusive]|場合、**排他**ボックスが選択されている場合、データベースが排他モードで開き、一度に 1 つだけのユーザーがアクセスできます。 排他モードでの実行時のパフォーマンスが向上します。|このオプションを動的に設定するには、使用、**排他**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)です。|  
|ページのタイムアウト|部分が削除される前に、(使用しない場合)、ページがバッファーに残っている 1 秒の 1/10 で時間の期間を指定します。 既定値は 600 秒 (60 秒) の部分の 1/10。 このオプションは、ODBC ドライバーを使用するすべてのデータ ソースに適用されます。<br /><br /> ページのタイムアウトは、本質的な遅延のため、0 をすることはできません。 ページのタイムアウトは、その値を下回るページ タイムアウト オプションが設定されている場合でも、本質的な遅延よりも小さくできません。|このオプションを動的に設定するには、使用、 **PAGETIMEOUT**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)です。|  
|[読み取り専用]|読み取り専用で、データベースを指定します。|このオプションを動的に設定するには、使用、 **READONLY**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)です。|  
|ディレクトリを選択します。|アクセスするファイルを格納するディレクトリを選択 ダイアログ ボックスが表示されます。<br /><br /> データ ソース ディレクトリを定義するときは、最もよく使用されるファイルが配置されているディレクトリを指定します。 ODBC ドライバーは、このディレクトリを既定のディレクトリとして使用します。 頻繁に使用される場合は、その他のファイルをこのディレクトリにコピーします。 または、ディレクトリの名前で、SELECT ステートメント内のファイル名を修飾することができます。<br /><br /> 選択\*C:\MYDIR\EMP から<br /><br /> またはを使用して新しい既定のディレクトリを指定することができます、 **SQLSetConnectOption**関数 SQL_CURRENT_QUALIFIER オプションを使用します。|このオプションを動的に設定するには、使用、 **DEFAULTDIR**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)です。|  
|削除された行を表示します。|削除済みとしてマークされている行の取得やに配置されているかどうかを指定します。 オフの場合、削除された行は表示されません。削除された行を処理は、選択した場合、削除されていない行と同じです。 既定値はオフです。|このオプションを動的に設定するには、使用、 **DELETED**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)です。|
