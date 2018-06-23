---
title: データ ソース (ODBC) の削除 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: 910e3e16-7b91-49d8-80bb-b4243926afaa
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d3b18bfe882147e0c60033dac9efd9dc4e3a6057
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074372"
---
# <a name="delete-a-data-source-odbc"></a>データ ソースの削除 (ODBC)
  ODBC アドミニストレーターをプログラムでを使用してデータ ソースを削除することができます (を使用して[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md))、または削除するファイル (ファイル データ ソース名)。  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a>ODBC アドミニストレーターを使用してデータ ソースを削除するには  
  
1.  **コントロール パネルの **、開かれている**管理ツール**、順にダブルクリック**データ ソース (ODBC)** です。 コマンド プロンプトから odbcad32.exe を実行することもできます。  
  
2.  クリックして、**ユーザー DSN**、**システム DSN**、または**ファイル DSN**タブです。  
  
3.  削除するデータ ソースをクリックします。  
  
4.  をクリックして**削除**、削除を確定します。  
  
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
  
  