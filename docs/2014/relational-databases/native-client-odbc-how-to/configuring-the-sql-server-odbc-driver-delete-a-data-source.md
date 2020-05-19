---
title: データソースの削除 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: 910e3e16-7b91-49d8-80bb-b4243926afaa
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c87d0123c5174461e4e3470b4e77ccb4bc5b10a1
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82701894"
---
# <a name="delete-a-data-source-odbc"></a>データ ソースの削除 (ODBC)
  データソースを削除するには、ODBC 管理者を使用してプログラムで ( [Sqlconfigdatasource](../native-client-odbc-api/sqlconfigdatasource.md)を使用)、またはファイルを削除します (ファイルデータソース名が指定されている場合)。  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a>ODBC アドミニストレーターを使用してデータ ソースを削除するには  
  
1.  **コントロールパネル**で、[**管理ツール**] を開き、[**データソース (ODBC)**] をダブルクリックします。 コマンド プロンプトから odbcad32.exe を実行することもできます。  
  
2.  [**ユーザー dsn**]、[**システム dsn**]、または [**ファイル dsn** ] タブをクリックします。  
  
3.  削除するデータ ソースをクリックします。  
  
4.  [**削除**] をクリックし、削除を確定します。  
  
## <a name="example"></a>例  
 プログラムによってデータソースを削除するには、2番目のパラメーターとして ODBC_REMOVE_DSN または ODBC_REMOVE_SYS_DSN を使用して[Sqlconfigdatasource](../native-client-odbc-api/sqlconfigdatasource.md)を呼び出します。  
  
 次のサンプルでは、データ ソースをプログラムで削除する方法を示しています。  
  
```  
// remove_odbc_data_source.cpp  
// compile with: ODBCCP32.lib user32.lib  
#include <iostream>  
#include <windows.h>  
#include <odbcinst.h>  
  
int main() {   
   LPCSTR provider = "SQL Server";   // Windows SQL Server Driver  
   LPCSTR provider = "SQL Server";   // Windows SQL Server driver  
   LPCSTR provider2 = "SQL Server Native Client 11.0";   // SQL Server 2012 Native Client driver  
   LPCSTR dsnname = "DSN=data2";  
   BOOL retval = SQLConfigDataSource(NULL, ODBC_REMOVE_DSN, provider, dsnname);  
   std::cout << retval;   // 1 if successful  
}  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server ODBC ドライバーを構成する方法に関するトピック](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
