---
title: データ ソースのレジストリ エントリ |Microsoft ドキュメント
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
- subkeys [ODBC]
- data sources [ODBC], registry entries
- registry entries for data sources [ODBC], about registry entries
- data sources [ODBC], configuring
- registry entries for data sources [ODBC]
ms.assetid: 78aaa3d3-d081-4550-80e3-720c910d5996
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c225109657906459d86ab5d19e441158c16ca57d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
