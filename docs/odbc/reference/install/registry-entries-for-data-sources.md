---
title: データ ソースのレジストリ エントリ |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC]
- data sources [ODBC], registry entries
- registry entries for data sources [ODBC], about registry entries
- data sources [ODBC], configuring
- registry entries for data sources [ODBC]
ms.assetid: 78aaa3d3-d081-4550-80e3-720c910d5996
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d5f5f865c0b50ea75548bb3a409caef8acf64b51
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63281921"
---
# <a name="registry-entries-for-data-sources"></a>データ ソースのレジストリ エントリ
> [!NOTE]  
>  ODBC は Windows XP および Windows Server 2003 以降、Windows オペレーティング システムに含まれます。 Windows の以前のバージョンで ODBC を明示的にのみインストールしてください。  
  
 インストーラー DLL では、レジストリ内の各データ ソースについての情報を保持します。 Microsoft Windows NT または Windows 2000 および Microsoft Windows 95/98 では、この情報は、レジストリの次の 2 つのキーのいずれかの下のサブキーに格納されます。  
  
 HKEY_LOCAL_MACHINE  
  
 ソフトウェア  
  
 ODBC  
  
 Odbc.ini  
  
 HKEY_CURRENT_USER  
  
 ソフトウェア  
  
 ODBC  
  
 Odbc.ini  
  
 どのキーが使用されるかどうかは、データ ソースに依存、*システム データ ソース、* にすべてのユーザーに表示されるまたは*ユーザー データ ソース、* これは、現在のユーザーにのみ使用できます。 システム データ ソースは、HKEY_LOCAL_MACHINE ツリーに格納されているし、ユーザー データ ソースは、HKEY_CURRENT_USER ツリーに格納されます。 その他のすべての点では、システム データ ソースおよびデータ ソースのユーザーは同じです。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ODBC データ ソースのサブキー](../../../odbc/reference/install/odbc-data-sources-subkey.md)  
  
-   [データ ソースの仕様のサブキー](../../../odbc/reference/install/data-source-specification-subkeys.md)  
  
-   [既定のサブキー](../../../odbc/reference/install/default-subkey.md)  
  
-   [ODBC のサブキー](../../../odbc/reference/install/odbc-subkey.md)
