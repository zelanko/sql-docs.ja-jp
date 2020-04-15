---
title: データ ソースの例 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], examples
ms.assetid: cbf15f32-0550-4c74-8088-8f7ac3855469
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 48c87f0d9f0a48b7d216151178c15bb019c0cbaa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306523"
---
# <a name="data-source-example"></a>データ ソースの例
Microsoft を実行しているコンピュータでは®Windows NT ® サーバー/Windows 2000 サーバー、ワークステーション/Windows 2000 プロフェッショナル、または Windows® 95/98 を実行しているコンピュータでは、コンピュータのデータ ソース情報がレジストリに格納されます。 情報が格納されるレジストリ キーに応じて、データ ソースは*ユーザー データ ソース*またはシステム*データ*ソースと呼ばれます。 ユーザー データ ソースは、HKEY_CURRENT_USER キーの下に格納され、現在のユーザーだけが使用できます。 システム データ ソースは、HKEY_LOCAL_MACHINE キーの下に格納され、1 台のコンピューター上の複数のユーザーが使用できます。 また、システム全体のサービスで使用することも可能で、ユーザーがマシンにログオンしていなくてもデータ ソースにアクセスできます。 ユーザーおよびシステム データ ソースの詳細については、「 [SQLManageDataSources](../../odbc/reference/syntax/sqlmanagedatasources.md)」を参照してください。  
  
 ユーザーが 3 つのユーザー データ ソースを持っているとします: 人事とインベントリ、Oracle DBMS を使用します。および、マイクロソフトの SQL Server DBMS を使用する給与計算。 データ ソースのレジストリ値は次のようになります。  
  
```  
HKEY_CURRENT_USER  
SOFTWARE  
          ODBC  
               Odbc.ini  
                    ODBC Data Sources  
                    Personnel : REG_SZ : Oracle  
                    Inventory : REG_SZ : Oracle  
                    Payroll : REG_SZ : SQL Server  
```  
  
 また、給与データ ソースのレジストリ値は次のようになります。  
  
```  
HKEY_CURRENT_USER  
     SOFTWARE  
          ODBC  
               Odbc.ini  
                    Payroll  
                         Driver : REG_SZ : C:\WINDOWS\SYSTEM\Sqlsrvr.dll  
                         Description : REG_SZ : Payroll database  
                         Server : REG_SZ : PYRLL1  
                         FastConnectOption : REG_SZ : No                          UseProcForPrepare : REG_SZ : Yes  
                         OEMTOANSI : REG_SZ : No  
                         LastUser : REG_SZ : smithjo  
                         Database : REG_SZ : Payroll  
                         Language : REG_SZ :  
```
