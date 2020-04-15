---
title: '手順 1: データ ソースに接続する |マイクロソフトドキュメント'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2a104733c0e5ec5acc87eeabd00c4e51d4bfd000
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301352"
---
# <a name="step-1-connect-to-the-data-source"></a>手順 1:データ ソースに接続する
アプリケーションの最初の手順は、データ ソースに接続することです。 このフェーズは、必要な機能を含め、次の図に示します。  
  
 ![ODBC アプリケーションのデータ ソースへの接続](../../../odbc/reference/develop-app/media/pr11.gif "pr11")  
  
 データ ソースに接続する最初の手順は、ドライバー マネージャーを読み込み **、SQLAllocHandle**を使用して環境ハンドルを割り当てることです。 詳細については、「[環境ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-the-environment-handle.md)」を参照してください。  
  
 その後、アプリケーションは **、SQLSetEnvAttr**をSQL_ATTR_APP_ODBC_VER環境属性で呼び出すことによって、準拠する ODBC のバージョンを登録します。 詳細については、「[アプリケーションの ODBC バージョンの宣言](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md)」および[「下位互換性と標準準拠](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)」を参照してください。  
  
 次に、アプリケーションは**SQLAllocHandle**を使用して接続ハンドルを割り当て **、SQLConnect** **、SQLDriverConnect**、または**SQLBrowseConnect**を使用してデータ ソースに接続します。 詳細については、「[接続ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md)」および[「接続の確立](../../../odbc/reference/develop-app/establishing-a-connection.md)」を参照してください。  
  
 アプリケーションは、手動でトランザクションをコミットするかどうかなどの接続属性を設定します。 詳細については、「[接続属性](../../../odbc/reference/develop-app/connection-attributes.md)」を参照してください。
