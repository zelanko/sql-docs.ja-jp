---
title: '手順 1: データソースに接続する |Microsoft Docs'
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
ms.openlocfilehash: 80f2dfc05d9d27f60aca414ee0abd13e13b3ea65
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114269"
---
# <a name="step-1-connect-to-the-data-source"></a>ステップ 1: データ ソースへの接続
アプリケーションの最初の手順は、データソースに接続することです。 このフェーズ (必要な関数を含む) を次の図に示します。  
  
 ![ODBC アプリケーションのデータ ソースへの接続](../../../odbc/reference/develop-app/media/pr11.gif "pr11")  
  
 データソースに接続するための最初の手順は、ドライバーマネージャーを読み込み、 **SQLAllocHandle**を使用して環境ハンドルを割り当てることです。 詳細については、「[環境ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-the-environment-handle.md)」を参照してください。  
  
 次に、SQL_ATTR_APP_ODBC_VER 環境属性を使用して**SQLSetEnvAttr**を呼び出すことによって、準拠している ODBC のバージョンを登録します。 詳細については、「[アプリケーションの ODBC バージョンの宣言](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md)」および「旧バージョンとの[互換性と標準の準拠](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)」を参照してください。  
  
 次に、アプリケーションは**SQLAllocHandle**を使用して接続ハンドルを割り当て、 **SQLConnect**、 **SQLDriverConnect**、または**SQLBrowseConnect**を使用してデータソースに接続します。 詳細については、「[接続ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md)と[接続の確立](../../../odbc/reference/develop-app/establishing-a-connection.md)」を参照してください。  
  
 その後、アプリケーションは、トランザクションを手動でコミットするかどうかなど、接続属性を設定します。 詳細については、「[接続属性](../../../odbc/reference/develop-app/connection-attributes.md)」を参照してください。
