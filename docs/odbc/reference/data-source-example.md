---
title: データソースの例 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ec9eacef6f0bd63eb0aaeac36dc97938297d1f16
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68135637"
---
# <a name="data-source-example"></a>データ ソースの例
Microsoft® Windows NT® Server/Windows 2000 Server、Microsoft Windows NT Workstation/Windows 2000 Professional、または Microsoft Windows®95/98 が実行されているコンピューターでは、コンピューターのデータソース情報はレジストリに格納されます。 情報が格納されているレジストリキーに応じて、データソースは*ユーザーデータ*ソースまたは*システムデータソース*と呼ばれます。 ユーザーデータソースは HKEY_CURRENT_USER キーの下に格納され、現在のユーザーのみが使用できます。 システムデータソースは HKEY_LOCAL_MACHINE キーの下に格納され、1台のコンピューター上の複数のユーザーが使用できます。 また、ユーザーがコンピューターにログオンしていない場合でもデータソースにアクセスできる、システム全体のサービスで使用することもできます。 ユーザーデータソースとシステムデータソースの詳細については、「 [Sqlmanagedatasources](../../odbc/reference/syntax/sqlmanagedatasources.md)」を参照してください。  
  
 たとえば、ユーザーが3つのユーザーデータソースを持っているとします。これは、Oracle DBMS を使用する担当者と在庫です。また、Microsoft SQL Server DBMS を使用する給与支払いです。 データソースのレジストリ値は次のようになります。  
  
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
  
 また、給与データソースのレジストリ値は次のようになります。  
  
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
