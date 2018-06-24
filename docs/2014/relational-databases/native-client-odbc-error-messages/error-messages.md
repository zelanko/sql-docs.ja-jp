---
title: エラー メッセージ |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], types
- ODBC error handling, message types
- errors [ODBC], types
ms.assetid: 46c0c22e-d105-4d5b-bb9d-5694472e8651
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2ba9c50f600caf23a6948752ce34e816e493a41b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073479"
---
# <a name="error-messages"></a>エラー メッセージ
  によって返されるメッセージのテキスト、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーに配置されます、 *MessageText*のパラメーター **SQLGetDiagRec**です。 メッセージのヘッダーには、次のようにエラーの発生元が記載されます。  
  
 [Microsoft][ODBC Driver Manager]  
 このヘッダーに関連するエラーは、ODBC ドライバー マネージャーで発生しています。  
  
 [Microsoft][ODBC Cursor Library]  
 このヘッダーに関連するエラーは、ODBC カーソル ライブラリで発生しています。  
  
 [Microsoft][SQL Server Native Client]  
 これらのエラーが発生して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー。 Net-Library または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の名前が付いているノードが他にない場合、エラーはドライバー内で発生しています。  
  
 [Microsoft][SQL Server Native Client][*Net-transportname*]  
 によってこれらのエラーが発生した、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Net-library を場所*Net-transportname*の表示名は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ネットワーク トランスポート (たとえば、名前付きパイプ、共有メモリ、TCP/IP ソケット、または VIA)。 エラー メッセージの残りの部分には、呼び出された Net-Library 関数と、TDS 関数から呼び出された基になるネットワーク API の関数が含まれています。 *PfNative*これらのエラーと共に返されたエラー コードは、基になるネットワーク プロトコル スタックからのエラー コード。  
  
 [Microsoft][SQL Server Native Client][[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]  
 このヘッダーに関連するエラーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で発生しています。 エラー メッセージの残りの部分は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー メッセージのテキストです。 *PfNative*からのエラー番号は、これらのエラーで返されたコード[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 によって返されるエラー メッセージ (および番号) の一覧の詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の説明とエラー列を参照してください、 **sysmessages**システム テーブルに、**マスター**データベースに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
## <a name="see-also"></a>参照  
 [エラーとメッセージの処理](handling-errors-and-messages.md)  
  
  