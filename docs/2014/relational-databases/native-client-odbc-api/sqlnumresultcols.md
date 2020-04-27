---
title: SQLNumResultCols |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 88edec63a97ff6c463f07add895ff8399fc4268a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63046757"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
  実行されたステートメント[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の場合、NATIVE Client ODBC ドライバーはサーバーにアクセスせず、結果セットの列数を報告しません。 この場合、 `SQLNumResultCols`はサーバーのラウンドトリップを発生させません。 [SQLDescribeCol](sqldescribecol.md)や[sqlcolattribute](sqlcolattribute.md)と同様、 `SQLNumResultCols`準備済みで実行されていないステートメントを呼び出すと、サーバーのラウンドトリップが生成されます。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントまたはステートメント バッチが複数の結果行セットを返すときは、結果セットの列数を報告する場合、あるセットから別のセットへ結果セットを変更することができます。 `SQLNumResultCols`各セットに対してを呼び出す必要があります。 列数が変化すると、アプリケーションでは行の結果をフェッチする前に、データ値を再バインドする必要があります。 複数の結果セットを返す処理の詳細については、「 [Sqlmoreresults](sqlmoreresults.md)」を参照してください。  
  
 以降のデータベースエンジンの機能強化[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]により、SQLNumResultCols は、予期される結果についてより正確な説明を得ることができます。 これらのより正確な結果は、以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQLNumResultCols によって返される値とは異なる場合があります。 詳細については、「[メタデータの検出](../native-client/features/metadata-discovery.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQLNumResultCols 関数](https://go.microsoft.com/fwlink/?LinkId=59359)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
