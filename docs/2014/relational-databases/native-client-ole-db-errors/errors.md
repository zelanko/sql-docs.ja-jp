---
title: エラー |Microsoft ドキュメント
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
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
ms.assetid: bd0612f4-96ef-4919-b0f9-b5447210fe93
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a3210cb1cd48a375e428cc6cf8a40e6f76f48b21
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076207"
---
# <a name="errors"></a>エラー
  OLE オブジェクトや COM オブジェクトは、オブジェクト メンバー関数の HRESULT リターン コードによってエラーを報告します。 OLE と COM の HRESULT は、ビットがまとめられている構造体です。 OLE には、構造体のメンバーを取り出すマクロが用意されています。  
  
 OLE と COM の指定、 **IErrorInfo**インターフェイスです。 インターフェイスはメソッドを公開など**GetDescription**です。 これにより、クライアントは OLE サーバーや COM サーバーからエラーの詳細を取得できます。 OLE DB を拡張**IErrorInfo**単一メンバー関数の実行に複数のエラー情報パケットの戻り値をサポートするためにします。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では複数のエラーを返すことができます。 アプリケーションは、一度にサーバー エラーは 1 つを呼び出すことによって取得できます[imultipleresults::getresult](http://go.microsoft.com/fwlink/?LinkId=129630) ISQLErrorInfo と IErrorRecords と組み合わせて使用します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、OLE DB レコードが強化されたを公開**IErrorInfo**、カスタム`ISQLErrorInfo`、およびプロバイダー固有[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) error オブジェクトインターフェイス。  
  
 トレースのエラーについては、次を参照してください。[データ アクセスのトレース](http://go.microsoft.com/fwlink/?LinkId=125805)です。 エラーのトレースで追加された機能強化については[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を参照してください[へのアクセス ログの診断情報、拡張イベント](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [リターン コード](return-codes.md)  
  
-   [エラー インターフェイス内の情報](information-in-error-interfaces.md)  
  
-   [SQL Server エラーの詳細](sql-server-error-detail.md)  
  
-   [エラー情報の取得](retrieving-error-information.md)  
  
-   [SQL Server のメッセージ結果](sql-server-message-results.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  