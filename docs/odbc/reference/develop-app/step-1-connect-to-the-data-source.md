---
title: "手順 1: データ ソースに接続する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application process [ODBC], connecting to data source
- data sources [ODBC], connections
- connecting to data source [ODBC], steps
ms.assetid: 84298664-4523-4149-b821-7b2e42c85281
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e57a58062f352900e5411fcc99a4c5bc9c59393b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="step-1-connect-to-the-data-source"></a>手順 1: データ ソースに接続します。
任意のアプリケーションの最初の手順では、データ ソースへの接続です。 を必要とする関数を含む、このフェーズは、次の図に表示されます。  
  
 ![ODBC アプリケーションのデータ ソースに接続する](../../../odbc/reference/develop-app/media/pr11.gif "pr11")  
  
 データ ソースに接続する最初の手順は、ドライバー マネージャーの読み込みおよびで環境ハンドルを割り当てる**SQLAllocHandle**です。 詳細については、次を参照してください。[環境ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-the-environment-handle.md)です。  
  
 その後、アプリケーションを呼び出すことによって、準拠しています。 ODBC のバージョンを登録する**SQLSetEnvAttr** SQL_ATTR_APP_ODBC_VER 環境属性を持つ。 詳細については、次を参照してください。[アプリケーションの ODBC バージョンを宣言する](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md)と[旧バージョンとの互換性と標準の順守](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)です。  
  
 次に、アプリケーションが使用して、接続ハンドルを割り当てます**SQLAllocHandle**を持つデータ ソースに接続して**SQLConnect**、 **SQLDriverConnect**、または**SQLBrowseConnect**です。 詳細については、次を参照してください。[接続ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md)と[接続を確立する](../../../odbc/reference/develop-app/establishing-a-connection.md)です。  
  
 その後、アプリケーションでは、手動でトランザクションをコミットするかどうかなど、任意の接続属性を設定します。 詳細については、次を参照してください。[接続属性](../../../odbc/reference/develop-app/connection-attributes.md)です。
