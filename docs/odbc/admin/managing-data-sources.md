---
title: データ ソースの管理 |Microsoft ドキュメント
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
ms.topic: conceptual
helpviewer_keywords:
- deleting data sources [ODBC], ODBC data source administrator
- data sources [ODBC], ODBC data source administrator
- adding data sources [ODBC], ODBC data source administrator
- removing data sources [ODBC], ODBC data source administrator
- ODBC data source administrator [ODBC], data source management
ms.assetid: 67cc4945-4850-4eb4-8da6-b835ddaeca4c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 222bbc143fee7aa89d8414a05510fa01a35873cd
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="managing-data-sources"></a>データ ソースの管理
ドライバーのセットアップ プログラムから ODBC ドライバーをインストールした後は、その 1 つまたは複数のデータ ソースを定義できます。 データ ソース名 (DSN) が作成したデータの一意の説明を提供する必要があります。たとえば、*給与*または*Accounts Payable*です。 現在インストールされているすべてのドライバーに定義されているユーザーおよびシステム データ ソースは、「、**ユーザー DSN**または**システム DSN**のタブ、 **ODBC データ ソース アドミニストレーター** ダイアログ ボックス。 特定のディレクトリ内のファイル データ ソースは、「、**ファイル DSN** ; タブに表示されるディレクトリを入力、**ファイルの場所**ボックスに、**ファイル DSN**  タブ。  
  
> [!NOTE]  
>  64 ビット プラットフォームでの 32 ビット ドライバーに接続するデータ ソースを管理するには、c:\windows\sysWOW64\odbcad32.exe を使用します。 64 ビット ドライバーに接続するデータ ソースを管理するには、c:\windows\system32\odbcad32.exe を使用します。 **管理ツール**64 ビットの Windows 8 オペレーティング システムでは、32 ビットと 64 ビットの両方のアイコンは**ODBC データ ソース アドミニストレーター**  ダイアログ ボックス。  
  
 構成や削除など、32 ビット ドライバーに接続する DSN に 64 ビット odbcad32.exe を使用する場合**ドライバーは Microsoft Access (\*.mdb)**、次のエラー メッセージが表示されます。  
  
```  
The specified DSN contains an architecture mismatch between the Driver and Application  
```  
  
 このエラーを解決するには、構成または DSN を削除する 32 ビット odbcad32.exe を使用します。  
  
 データ ソースは、そのドライバーを通じてアクセスするデータを特定の ODBC ドライバーを関連付けます。 たとえば、dBASE の ODBC ドライバーを使用して、ハード ディスクまたはネットワーク ドライブ上の特定のディレクトリで見つかった dBASE ファイルを 1 つまたは複数をアクセスするデータ ソースを作成する可能性があります。 ODBC データ ソース アドミニストレーターを使用して、することができますを追加、変更、および次の表に示すように、データ ソースを削除します。  
  
|操作|Description|  
|------------|-----------------|  
|データ ソースの追加|各 1 つにそのドライバーを使用してアクセスするデータの一部とドライバーの関連付けが複数のデータ ソースを追加することができます。 各データ ソースにそのデータ ソースを一意に識別する名前を付けます。 たとえば、顧客情報を含む dBASE ファイルのセットのデータ ソースを作成する場合は、"Customers"データ ソースを名前可能性があります。 アプリケーションは、通常のユーザーが選択するデータ ソース名を表示します。<br /><br /> ファイル データ ソースを追加する方法が異なりますユーザーまたはシステム データ ソースを追加します。 詳細については、ヘルプ ファイル、ODBC データ ソース アドミニストレーターを参照してください。|  
|データ ソースを変更します。|要件に応じてした方がデータ ソースを再構成するために必要です。 クリックしてオプションをリセットできます**構成**ドライバーのセットアップ ダイアログ ボックス。|  
|データ ソースの削除|をクリックして**削除**データ ソースを選択した後です。|  
  
 ファイルのデータ ソースの詳細については、次を参照してください。[を使用してファイル データ ソースの接続](../../odbc/reference/develop-app/connecting-using-file-data-sources.md)または[SQLDriverConnect 関数](../../odbc/reference/syntax/sqldriverconnect-function.md)です。  
  
## <a name="see-also"></a>参照  
 [ODBC データ ソース アドミニストレーター](../../odbc/admin/odbc-data-source-administrator.md)
