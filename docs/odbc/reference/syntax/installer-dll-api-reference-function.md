---
title: インストーラー DLL の API リファレンス関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installer DLL [ODBC]
ms.assetid: 47fcadc3-f102-4989-9ee7-a1c65233142a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 614548110102e21cdd9f4bd5ba01f85aff6a6c55
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="installer-dll-api-reference-function"></a>インストーラー DLL の API リファレンス関数
このセクションでは、インストーラーの DLL の API 内の関数の構文について説明します。 インストーラーの DLL の API は、20 の機能で構成されます。 これらの関数のうち 3 つ**SQLGetTranslator**、 **SQLRemoveDSNFromIni**、および**SQLWriteDSNToIni**Dll のセットアップによってのみ呼び出されます。 セットアップおよび管理プログラムによっては、他の関数が呼び出されます。  
  
 各関数には、導入された ODBC のバージョンが付いています。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [SQLConfigDataSource 関数](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)  
  
-   [SQLConfigDriver 関数](../../../odbc/reference/syntax/sqlconfigdriver-function.md)  
  
-   [SQLCreateDataSource 関数](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)  
  
-   [SQLGetConfigMode 関数](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)  
  
-   [SQLGetInstalledDrivers 関数](../../../odbc/reference/syntax/sqlgetinstalleddrivers-function.md)  
  
-   [SQLGetPrivateProfileString 関数](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)  
  
-   [SQLGetTranslator 関数](../../../odbc/reference/syntax/sqlgettranslator-function.md)  
  
-   [SQLInstallDriverEx 関数](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)  
  
-   [SQLInstallDriverManager 関数](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)  
  
-   [SQLInstallerError 関数](../../../odbc/reference/syntax/sqlinstallererror-function.md)  
  
-   [SQLInstallTranslator 関数](../../../odbc/reference/syntax/sqlinstalltranslator-function.md)  
  
-   [SQLInstallTranslatorEx 関数](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)  
  
-   [SQLManageDataSources 関数](../../../odbc/reference/syntax/sqlmanagedatasources.md)  
  
-   [SQLPostInstallerError 関数](../../../odbc/reference/syntax/sqlpostinstallererror-function.md)  
  
-   [SQLReadFileDSN 関数](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)  
  
-   [SQLRemoveDefaultDataSource 関数](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)  
  
-   [SQLRemoveDriver 関数](../../../odbc/reference/syntax/sqlremovedriver-function.md)  
  
-   [SQLRemoveDriverManager 関数](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)  
  
-   [SQLRemoveDSNFromIni 関数](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)  
  
-   [SQLRemoveTranslator 関数](../../../odbc/reference/syntax/sqlremovetranslator-function.md)  
  
-   [SQLSetConfigMode 関数](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)  
  
-   [SQLValidDSN 関数](../../../odbc/reference/syntax/sqlvaliddsn-function.md)  
  
-   [SQLWriteDSNToIni 関数](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)  
  
-   [SQLWriteFileDSN 関数](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)  
  
-   [SQLWritePrivateProfileString 関数](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)
