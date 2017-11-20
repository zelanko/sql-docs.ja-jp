---
title: "データ ソースのレジストリ エントリ |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subkeys [ODBC]
- data sources [ODBC], registry entries
- registry entries for data sources [ODBC], about registry entries
- data sources [ODBC], configuring
- registry entries for data sources [ODBC]
ms.assetid: 78aaa3d3-d081-4550-80e3-720c910d5996
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 177b6d8121cf218551f486599b5baf6ffc23a6fd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="registry-entries-for-data-sources"></a>データ ソースのレジストリ エントリ
> [!NOTE]  
>  Windows XP および Windows Server 2003 以降、Windows オペレーティング システムに ODBC が含まれます。 以前のバージョンの Windows で ODBC を明示的にのみインストールしてください。  
  
 インストーラー DLL は、各データ ソースに関するレジストリの情報を保持します。 Microsoft Windows NT または Windows 2000 および Microsoft Windows 95/98 では、この情報は、レジストリで次の 2 つのキーの 1 つ下のサブキーに格納されます。  
  
 HKEY_LOCAL_MACHINE  
  
 ソフトウェア  
  
 ODBC  
  
 Odbc.ini  
  
 HKEY_CURRENT_USER  
  
 ソフトウェア  
  
 ODBC  
  
 Odbc.ini  
  
 どのキーが使用されるかどうかは、データ ソースに依存、*システム データ ソース、*にあるすべてのユーザーに、または*ユーザー データ ソース、*これは、現在のユーザーにのみ使用できます。 システム データ ソースが、HKEY_LOCAL_MACHINE ツリーに格納されているし、ユーザー データ ソースが HKEY_CURRENT_USER ツリーに格納されます。 その他のすべての点では、システム データ ソースとユーザー データ ソースと同じです。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ODBC データ ソースのサブキー](../../../odbc/reference/install/odbc-data-sources-subkey.md)  
  
-   [データ ソースの仕様のサブキー](../../../odbc/reference/install/data-source-specification-subkeys.md)  
  
-   [既定のサブキー](../../../odbc/reference/install/default-subkey.md)  
  
-   [ODBC のサブキー](../../../odbc/reference/install/odbc-subkey.md)

