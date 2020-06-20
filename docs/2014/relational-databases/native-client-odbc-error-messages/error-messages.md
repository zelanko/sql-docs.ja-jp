---
title: エラーメッセージ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], types
- ODBC error handling, message types
- errors [ODBC], types
ms.assetid: 46c0c22e-d105-4d5b-bb9d-5694472e8651
author: rothja
ms.author: jroth
ms.openlocfilehash: d004ba320b50896b6f57c5de335d7f7b3d33e87a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85020035"
---
# <a name="error-messages"></a>エラー メッセージ
  Native Client ODBC ドライバーによって返されるメッセージのテキスト [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、 **SQLGetDiagRec**の*messagetext*パラメーターに格納されます。 メッセージのヘッダーには、次のようにエラーの発生元が記載されます。  
  
 [Microsoft][ODBC Driver Manager]  
 このヘッダーに関連するエラーは、ODBC ドライバー マネージャーで発生しています。  
  
 [Microsoft][ODBC Cursor Library]  
 このヘッダーに関連するエラーは、ODBC カーソル ライブラリで発生しています。  
  
 [Microsoft][SQL Server Native Client]  
 これらのエラーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーによって発生します。 Net-Library または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の名前が付いているノードが他にない場合、エラーはドライバー内で発生しています。  
  
 エクスプローラー[SQL Server Native Client][*Net-transportname*]  
 これらのエラーは、Net-library によって発生し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 *net-transportname*は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントネットワークトランスポート (名前付きパイプ、共有メモリ、tcp/ip ソケット、VIA など) の表示名です。 エラー メッセージの残りの部分には、呼び出された Net-Library 関数と、TDS 関数から呼び出された基になるネットワーク API の関数が含まれています。 これらのエラーと共に返される*pfNative*エラーコードは、基になるネットワークプロトコルスタックからのエラーコードです。  
  
 [Microsoft][SQL Server Native Client][[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]  
 このヘッダーに関連するエラーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で発生しています。 エラー メッセージの残りの部分は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー メッセージのテキストです。 これらのエラーと共に返される*pfNative*コードは、からのエラー番号です [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 によって返されるエラーメッセージの一覧 (およびその番号) の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、の**master**データベースにある**sysmessages**システムテーブルの description 列と error 列を参照してください [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
## <a name="see-also"></a>参照  
 [エラーとメッセージの処理](handling-errors-and-messages.md)  
  
  
