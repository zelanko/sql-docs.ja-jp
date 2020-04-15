---
title: データ ソースの管理 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- deleting data sources [ODBC], ODBC data source administrator
- data sources [ODBC], ODBC data source administrator
- adding data sources [ODBC], ODBC data source administrator
- removing data sources [ODBC], ODBC data source administrator
- ODBC data source administrator [ODBC], data source management
ms.assetid: 67cc4945-4850-4eb4-8da6-b835ddaeca4c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a5069ac9a5babc3071c52d73d5b56b21729a5d8a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307213"
---
# <a name="managing-data-sources"></a>データ ソースの管理
ドライバーのセットアップ プログラムから ODBC ドライバーをインストールした後、1 つ以上のデータ ソースを定義できます。 データ ソース名 (DSN) は、データの一意の説明を提供する必要があります。たとえば、*給与計算*や*買掛金勘定*など。 ODBC データ ソース**アドミニストレータ**ダイアログ ボックスの **[ユーザー DSN]** タブまたは [**システム DSN]** タブに、現在インストールされているすべてのドライバに対して定義されているユーザーおよびシステム データ ソースが表示されます。 指定したディレクトリ内のファイル データ ソースは、[**ファイル DSN]** タブに表示されます。表示されるディレクトリは、[**ファイル DSN]** タブの [**ファイルの場所**] ボックスに入力します。  
  
> [!NOTE]  
>  64 ビット プラットフォームで 32 ビット ドライバーに接続するデータ ソースを管理するには、c:\windows\sysWOW64\odbcad32.exe を使用します。 64 ビット ドライバーに接続するデータ ソースを管理するには、c:\windows\system32\odbcad32.exe を使用します。 64 ビット Windows 8 オペレーティング システムの**管理ツール**には、32 ビットと 64 ビットの両方の**ODBC データ ソース アドミニストレーター**のアイコンがあります。  
  
 64 ビット odbcad32.exe を使用して、32 ビット ドライバに接続する DSN**を構成\*** または削除すると、次のエラー メッセージが表示されます。  
  
```  
The specified DSN contains an architecture mismatch between the Driver and Application  
```  
  
 このエラーを解決するには、32 ビット odbcad32.exe を使用して DSN を構成または削除します。  
  
 データ ソースは、特定の ODBC ドライバーをそのドライバーを介してアクセスするデータに関連付けます。 たとえば、データ ソースを作成して ODBC dBASE ドライバを使用して、ハード ディスクまたはネットワーク ドライブの特定のディレクトリにある 1 つ以上の dBASE ファイルにアクセスできます。 ODBC データ ソース アドミニストレータを使用すると、次の表に示すように、データ ソースの追加、変更、および削除を行うことができます。  
  
|アクション|説明|  
|------------|-----------------|  
|データ ソースの追加|複数のデータ ソースを追加し、それぞれがドライバーをそのドライバーを使用してアクセスするデータに関連付けることも可能です。 各データ ソースに、そのデータ ソースを一意に識別する名前を付けます。 たとえば、顧客情報を含む dBASE ファイルのセットのデータ ソースを作成する場合、そのデータ ソースに "Customers" という名前を付けます。 アプリケーションは、通常、ユーザーが選択できるデータ ソース名を表示します。<br /><br /> ファイル データ ソースの追加は、ユーザーまたはシステム データ ソースの追加とは少し異なります。 詳細については、ODBC データ ソース アドミニストレータのヘルプ ファイルを参照してください。|  
|データ ソースの変更|要件によっては、データ ソースを再構成する必要がある場合があります。 オプションをリセットするには、ドライバーのセットアップダイアログ ボックスで [**構成**] をクリックします。|  
|データ ソースの削除|データ ソースを選択した後で [**削除**] をクリックします。|  
  
 ファイル データ ソースの詳細については、「[ファイル データ ソースを使用した接続](../../odbc/reference/develop-app/connecting-using-file-data-sources.md)」または[SQLDriverConnect 関数](../../odbc/reference/syntax/sqldriverconnect-function.md)を参照してください。  
  
## <a name="see-also"></a>参照  
 [ODBC データ ソース アドミニストレーター](../../odbc/admin/odbc-data-source-administrator.md)
