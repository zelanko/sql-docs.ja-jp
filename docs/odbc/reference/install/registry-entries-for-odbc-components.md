---
title: ODBC コンポーネントのレジストリエントリ |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC]
- installing ODBC components [ODBC], registry entries
- registry entries for components [ODBC]
- subkeys [ODBC], for components
- registry entries for components [ODBC], about registry entries
ms.assetid: c90aa8a4-6ece-48de-901c-17d23739a9ff
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bead63f11b253342cd444e1d5bd0697ee00cfbc1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81296182"
---
# <a name="registry-entries-for-odbc-components"></a>ODBC コンポーネントのレジストリ エントリ
> [!NOTE]  
>  Windows XP および windows Server 2003 以降では、ODBC は Windows オペレーティングシステムに含まれています。 ODBC は、以前のバージョンの Windows にのみ明示的にインストールする必要があります。  
  
 インストーラー DLL は、インストールされている各 ODBC コンポーネントに関する情報をレジストリに保持します。 Microsoft Windows NT および Microsoft Windows 95/98 を実行しているコンピューターでは、この情報はレジストリの次のキーの下のサブキーに格納されます。  

 ```console
 HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\Odbcinst.ini
 ```

 Odbcinst は HKEY_LOCAL_MACHINE ツリーのサブキーであるため、ODBC コンポーネントに関する情報は、コンピューターのすべてのユーザーが使用できます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ODBC Core サブキー](../../../odbc/reference/install/odbc-core-subkey.md)  
  
-   [ODBC ドライバーのサブキー](../../../odbc/reference/install/odbc-drivers-subkey.md)  
  
-   [ドライバーの仕様のサブキー](../../../odbc/reference/install/driver-specification-subkeys.md)  
  
-   [既定のドライバーのサブキー](../../../odbc/reference/install/default-driver-subkey.md)  
  
-   [ODBC トランスレーターのサブキー](../../../odbc/reference/install/odbc-translators-subkey.md)  
  
-   [ドライバーの仕様のサブキー](../../../odbc/reference/install/translator-specification-subkeys.md)
