---
title: エラー |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1c722a870a5ac6d9715f874b3135d4ed0058ac63
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34707310"
---
# <a name="errors"></a>エラー
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  OLE オブジェクトや COM オブジェクトは、オブジェクト メンバー関数の HRESULT リターン コードによってエラーを報告します。 OLE と COM の HRESULT は、ビットがまとめられている構造体です。 OLE には、構造体のメンバーを取り出すマクロが用意されています。  
  
 OLE と COM の指定、 **IErrorInfo**インターフェイスです。 インターフェイスはメソッドを公開など**GetDescription**です。 これにより、クライアントは OLE サーバーや COM サーバーからエラーの詳細を取得できます。 OLE DB を拡張**IErrorInfo**単一メンバー関数の実行に複数のエラー情報パケットの戻り値をサポートするためにします。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では複数のエラーを返すことができます。 アプリケーションは、一度にサーバー エラーは 1 つを呼び出すことによって取得できます[imultipleresults::getresult](http://go.microsoft.com/fwlink/?LinkId=129630) ISQLErrorInfo と IErrorRecords と組み合わせて使用します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、OLE DB レコードが強化されたを公開**IErrorInfo**、カスタム**ISQLErrorInfo**、およびプロバイダー固有[ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)エラー オブジェクト インターフェイスです。  
  
 トレースのエラーについては、次を参照してください。[データ アクセスのトレース](http://go.microsoft.com/fwlink/?LinkId=125805)です。 エラーのトレースで追加された機能強化については[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を参照してください[へのアクセス ログの診断情報、拡張イベント](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [リターン コード](../../relational-databases/native-client-ole-db-errors/return-codes.md)  
  
-   [エラー インターフェイス内の情報](../../relational-databases/native-client-ole-db-errors/information-in-error-interfaces.md)  
  
-   [SQL Server エラーの詳細](../../relational-databases/native-client-ole-db-errors/sql-server-error-detail.md)  
  
-   [エラー情報の取得](../../relational-databases/native-client-ole-db-errors/retrieving-error-information.md)  
  
-   [SQL Server のメッセージ結果](../../relational-databases/native-client-ole-db-errors/sql-server-message-results.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
