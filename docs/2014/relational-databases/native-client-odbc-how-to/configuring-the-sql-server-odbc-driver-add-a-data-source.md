---
title: データソースの追加 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: b4ac6f0e-8e6a-4b1a-9a7e-60e0a69b2180
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c050efd2f309ccec76b80fd24b519e7d2389e4ea
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63126076"
---
# <a name="add-a-data-source-odbc"></a>データ ソースの追加 (ODBC)
  データソースを追加するには、ODBC アドミニストレーターを使用するか、プログラムで ( [Sqlconfigdatasource](../native-client-odbc-api/sqlconfigdatasource.md)を使用)、またはファイルを作成します。  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a>ODBC アドミニストレーターを使用してデータ ソースを追加するには  
  
1.  **コントロールパネル**で、[**管理ツール**]、[**データソース (ODBC)**] の順にアクセスします。 または、odbcad32.exe を呼び出すことができます。  
  
2.  [**ユーザー dsn**]、 **[システム dsn**]、または [**ファイル dsn** ] タブをクリックし、[**追加**] をクリックします。  
  
3.  [ **SQL Server**] をクリックし、[**完了**] をクリックします。  
  
4.  SQL Server への新しいデータ ソースの作成ウィザードの手順に従って実行します。  
  
### <a name="to-add-a-data-source-programmatically"></a>データ ソースをプログラムで追加するには  
  
1.  2番目のパラメーターを ODBC_ADD_DSN または ODBC_ADD_SYS_DSN に設定して[Sqlconfigdatasource](../native-client-odbc-api/sqlconfigdatasource.md)を呼び出します。  
  
### <a name="to-add-a-file-data-source"></a>ファイル データ ソースを追加するには  
  
1.  接続文字列で SAVEFILE = file_name パラメーターを指定して[SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md)を呼び出します。 接続が確立されると、ODBC ドライバーによって、SAVEFILE パラメーターが指す場所の接続パラメーターを使用してファイル データ ソースが作成されます。  
  
## <a name="see-also"></a>参照  
 [SQL Server ODBC ドライバーを構成する方法に関するトピック](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
