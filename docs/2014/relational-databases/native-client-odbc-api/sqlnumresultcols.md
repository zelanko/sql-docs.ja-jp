---
title: SQLNumResultCols |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 73ac3425eab1a4c19130352ef566153eb6c34e53
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072994"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
  ステートメントの実行、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーに結果セット内の列の数を報告するサーバーがアクセスしていません。 この場合、`SQLNumResultCols`サーバーとのやり取りは行われません。 同様に[SQLDescribeCol](sqldescribecol.md)と[SQLColAttribute](sqlcolattribute.md)、呼び出し元`SQLNumResultCols`準備されてが実行されていないステートメントには、サーバーとのやり取りが生成されます。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントまたはステートメント バッチが複数の結果行セットを返すときは、結果セットの列数を報告する場合、あるセットから別のセットへ結果セットを変更することができます。 `SQLNumResultCols` 各セットに対して呼び出す必要があります。 列数が変化すると、アプリケーションでは行の結果をフェッチする前に、データ値を再バインドする必要があります。 セットを返す複数の結果を処理の詳細についてを参照してください[SQLMoreResults](sqlmoreresults.md)です。  
  
 以降で、データベース エンジンの機能強化[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]SQLNumResultCols を期待する結果のより正確な記述を取得できるようにします。 以前のバージョンの SQLNumResultCols によって返される値からこれらのより正確な結果が異なる場合があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 詳細については、次を参照してください。[メタデータ検出](../native-client/features/metadata-discovery.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLNumResultCols 関数](http://go.microsoft.com/fwlink/?LinkId=59359)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  