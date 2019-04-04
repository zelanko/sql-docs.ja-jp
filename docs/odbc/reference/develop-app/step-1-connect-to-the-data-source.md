---
title: '手順 1: データ ソースに接続する |Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], connecting to data source
- data sources [ODBC], connections
- connecting to data source [ODBC], steps
ms.assetid: 84298664-4523-4149-b821-7b2e42c85281
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 154fdd7368835ba2a578d3ec641705c4064859ac
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600900"
---
# <a name="step-1-connect-to-the-data-source"></a>ステップ 1: データ ソースへの接続
任意のアプリケーションの最初の手順では、データ ソースに接続します。 これを必要とする関数を含む、このフェーズは、次の図に表示されます。  
  
 ![ODBC アプリケーションのデータ ソースに接続する](../../../odbc/reference/develop-app/media/pr11.gif "pr11")  
  
 ドライバー マネージャーの読み込みし、使用して、環境ハンドルを割り当てるには、まずデータ ソースへの接続で**SQLAllocHandle**します。 詳細については、[環境ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-the-environment-handle.md)を参照してください。  
  
 その後、アプリケーションを呼び出すことによって、準拠している ODBC のバージョンを登録します**SQLSetEnvAttr** SQL_ATTR_APP_ODBC_VER 環境属性を持つ。 詳細については、[アプリケーションの ODBC バージョンを宣言する](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md)と[旧バージョンとの互換性と標準準拠](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)を参照してください。  
  
 次に、アプリケーションと接続ハンドルを割り当てます**SQLAllocHandle**でデータ ソースに接続し、 **SQLConnect**、 **SQLDriverConnect**、または**SQLBrowseConnect**します。 詳細については、[接続ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md)と[接続を確立する](../../../odbc/reference/develop-app/establishing-a-connection.md)を参照してください。  
  
 その後、アプリケーションでは、手動でトランザクションをコミットするかどうかなど、任意の接続属性を設定します。 詳細については、[接続属性](../../../odbc/reference/develop-app/connection-attributes.md)を参照してください。
