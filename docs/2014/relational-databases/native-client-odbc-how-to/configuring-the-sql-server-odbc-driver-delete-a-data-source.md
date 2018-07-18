---
title: データ ソース (ODBC) の削除 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: 910e3e16-7b91-49d8-80bb-b4243926afaa
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e870254043d9cc85d99203d76513816f67267560
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415191"
---
# <a name="delete-a-data-source-odbc"></a>データ ソースの削除 (ODBC)
  プログラムで ODBC アドミニストレーターを使用してデータ ソースを削除することができます (を使用して[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md))、または (する場合、ファイル データ ソース名) にファイルを削除しています。  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a>ODBC アドミニストレーターを使用してデータ ソースを削除するには  
  
1.  **コントロール パネルの **、オープン**管理ツール**、し、ダブルクリック**データ ソース (ODBC)** します。 コマンド プロンプトから odbcad32.exe を実行することもできます。  
  
2.  をクリックして、**ユーザー DSN**、**システム DSN**、または**ファイル DSN**タブ。  
  
3.  削除するデータ ソースをクリックします。  
  
4.  クリックして**削除**、削除を確定します。  
  
## <a name="example"></a>例  
 データ ソースをプログラムで削除するには、呼び出す[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) 2 番目のパラメーターとして ODBC_REMOVE_DSN または ODBC_REMOVE_SYS_DSN を使用します。  
  
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
  
  
