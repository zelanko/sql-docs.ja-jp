---
title: エラー |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
ms.assetid: bd0612f4-96ef-4919-b0f9-b5447210fe93
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a9753b3dea7dc0883963022c43ab440b7c7a01ea
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420101"
---
# <a name="errors"></a>エラー
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  OLE オブジェクトや COM オブジェクトは、オブジェクト メンバー関数の HRESULT リターン コードによってエラーを報告します。 OLE と COM の HRESULT は、ビットがまとめられている構造体です。 OLE には、構造体のメンバーを取り出すマクロが用意されています。  
  
 OLE と COM を指定します、 **IErrorInfo**インターフェイス。 インターフェイスなどにメソッドを公開する**GetDescription**します。 これにより、クライアントは OLE サーバーや COM サーバーからエラーの詳細を取得できます。 OLE DB 拡張**IErrorInfo**単一メンバー関数の実行時に複数のエラー情報パケットの戻り値をサポートするためにします。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では複数のエラーを返すことができます。 アプリケーションは呼び出すことで、一度に 1 つのサーバー エラーを取得することができます[imultipleresults::getresult](http://go.microsoft.com/fwlink/?LinkId=129630) ISQLErrorInfo および IErrorRecords と組み合わせることです。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの公開、OLE DB レコードが強化された**IErrorInfo**、カスタム**ISQLErrorInfo**、およびプロバイダー固有[ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)エラー オブジェクト インターフェイス。  
  
 エラーのトレースについては、次を参照してください。[データ アクセスのトレース](http://go.microsoft.com/fwlink/?LinkId=125805)します。 エラーのトレースで追加の機能強化については[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を参照してください[診断の情報を拡張イベント ログにアクセスする](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [リターン コード](../../relational-databases/native-client-ole-db-errors/return-codes.md)  
  
-   [エラー インターフェイス内の情報](../../relational-databases/native-client-ole-db-errors/information-in-error-interfaces.md)  
  
-   [SQL Server エラーの詳細](../../relational-databases/native-client-ole-db-errors/sql-server-error-detail.md)  
  
-   [エラー情報の取得](../../relational-databases/native-client-ole-db-errors/retrieving-error-information.md)  
  
-   [SQL Server のメッセージ結果](../../relational-databases/native-client-ole-db-errors/sql-server-message-results.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
