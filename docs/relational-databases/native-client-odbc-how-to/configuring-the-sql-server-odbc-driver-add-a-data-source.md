---
title: データ ソースの追加 (ODBC) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: b4ac6f0e-8e6a-4b1a-9a7e-60e0a69b2180
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 55ae4f357aa850f6b3ff4ba9cca0b59a2ccbc570
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298333"
---
# <a name="configuring-the-sql-server-odbc-driver---add-a-data-source"></a>SQL Server ODBC ドライバーの構成 - データ ソースの追加
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降で ODBC アプリケーションを使用する前に、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でカタログ ストアド プロシージャのバージョンをアップグレードする方法や、データ ソースを追加、削除、およびテストする方法を理解しておく必要があります。  
  
  データ ソースを追加するには、ODBC アドミニストレーターを使用するか、プログラムで[(SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)を使用して) またはファイルを作成します。  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a>ODBC アドミニストレーターを使用してデータ ソースを追加するには  
  
1.  コントロール**パネル**から **[管理ツール]** にアクセスし **、[ODBC データ ソース ](64 ビット)** または**ODBC データ ソース (32 ビット)** を指定します。 または、odbcad32.exe を呼び出すことができます。  
  
2.  [**ユーザー DSN]、[** システム**DSN]、** または **[ファイル DSN]** タブをクリックし、[**追加**] をクリックします。  
  
3.  [SQL **Server]** をクリックし、[**完了**] をクリックします。  
  
4.  SQL Server への**新しいデータ ソースの作成ウィザードの手順を**実行します。  
  
### <a name="to-add-a-data-source-programmatically"></a>データ ソースをプログラムで追加するには  
  
1.  2 番目のパラメーターをODBC_ADD_DSNまたはODBC_ADD_SYS_DSNに設定して[、SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)を呼び出します。  
  
### <a name="to-add-a-file-data-source"></a>ファイル データ ソースを追加するには  
  
1.  接続文字列内の saveFILE=file_name パラメーターを使用して[接続](../../relational-databases/native-client-odbc-api/sqldriverconnect.md)を呼び出します。 接続が確立されると、ODBC ドライバーによって、SAVEFILE パラメーターが指す場所の接続パラメーターを使用してファイル データ ソースが作成されます。  
  
## <a name="see-also"></a>参照  
[ODBC&#41;&#40;データ ソースを削除する](../../relational-databases/native-client-odbc-how-to/configuring-the-sql-server-odbc-driver-delete-a-data-source.md)    
  
  
