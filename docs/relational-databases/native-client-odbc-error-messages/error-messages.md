---
title: エラーメッセージ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], types
- ODBC error handling, message types
- errors [ODBC], types
ms.assetid: 46c0c22e-d105-4d5b-bb9d-5694472e8651
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7d632d1d22cd8439a3d787e22301ec06ec4e0d93
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291748"
---
# <a name="error-messages"></a>エラー メッセージ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ネイティブ クライアント ODBC ドライバーによって返されるメッセージのテキストは、 **SQLGetDiagRec**のメッセージ テキスト パラメーターに配置されます。 *MessageText* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メッセージのヘッダーには、次のようにエラーの発生元が記載されます。  
  
 [Microsoft][ODBC Driver Manager]  
 このヘッダーに関連するエラーは、ODBC ドライバー マネージャーで発生しています。  
  
 [Microsoft][ODBC Cursor Library]  
 このヘッダーに関連するエラーは、ODBC カーソル ライブラリで発生しています。  
  
 [Microsoft][SQL Server Native Client]  
 これらのエラーはネイティブ クライアント[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ODBC ドライバーによって発生します。 Net-Library または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の名前が付いているノードが他にない場合、エラーはドライバー内で発生しています。  
  
 [マイクロソフト][SQL Server ネイティブ クライアント][*ネットトランスポート名*]  
 これらのエラーは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Net-Library によって発生しますが *、Net-Transportname*は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ネットワーク トランスポートの表示名です (たとえば、名前付きパイプ、共有メモリ、TCP/IP ソケット、または VIA)。 エラー メッセージの残りの部分には、呼び出された Net-Library 関数と、TDS 関数から呼び出された基になるネットワーク API の関数が含まれています。 これらのエラーで返される*pfNative*エラー コードは、基になるネットワーク プロトコル スタックからのエラー コードです。  
  
 [マイクロソフト][SQL Server ネイティブ クライアント][ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]  
 このヘッダーに関連するエラーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で発生しています。 エラー メッセージの残りの部分は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー メッセージのテキストです。 これらのエラーで返される*pfNative*コードは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のエラー番号です。 によって[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]返されるエラー メッセージの一覧 (およびその番号) の詳細については、 **master**データベースの**sysmessages**システム テーブルの説明とエラー列を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]参照してください。  
  
## <a name="see-also"></a>参照  
 [エラーとメッセージの処理](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
