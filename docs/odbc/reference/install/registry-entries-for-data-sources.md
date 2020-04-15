---
title: データ ソースのレジストリ エントリ |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c73ea704b091bc37afb1ac42b520304022d929c3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296272"
---
# <a name="registry-entries-for-data-sources"></a>データ ソースのレジストリ エントリ
> [!NOTE]  
>  WINDOWS XP および Windows Server 2003 以降では、ODBC が Windows のオペレーション システムに含まれています。 ODBC は、以前のバージョンの Windows にのみ明示的にインストールしてください。  
  
 インストーラー DLL は、各データ ソースに関する情報をレジストリに保持します。 Windows NT/Windows 2000 および Windows 95/98 では、この情報は、レジストリ内の次の 2 つのキーの下にあるサブキーに格納されます。  

 ```console
 HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\Odbc.ini  
 ```

 ```console
 HKEY_CURRENT_USER\SOFTWARE\ODBC\Odbc.ini
 ```

 使用されるキーは、データ ソースが*システム データ ソース*(すべてのユーザーが使用できる) か、現在のユーザーのみが使用できるユーザー データ*ソース*であるかによって異なります。 システム データ ソースはHKEY_LOCAL_MACHINE ツリーに格納され、ユーザー データ ソースはHKEY_CURRENT_USER ツリーに格納されます。 その他すべての点では、システム データ ソースとユーザー データ ソースは同じです。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ODBC データ ソースのサブキー](../../../odbc/reference/install/odbc-data-sources-subkey.md)  
  
-   [データ ソースの仕様のサブキー](../../../odbc/reference/install/data-source-specification-subkeys.md)  
  
-   [既定のサブキー](../../../odbc/reference/install/default-subkey.md)  
  
-   [ODBC のサブキー](../../../odbc/reference/install/odbc-subkey.md)
