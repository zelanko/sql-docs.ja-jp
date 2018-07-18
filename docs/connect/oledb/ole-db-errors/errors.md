---
title: エラー |Microsoft ドキュメント
description: エラー
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 2c94e2beaf56e6987bf49bb73e8629f33a775496
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2018
ms.locfileid: "35665242"
---
# <a name="errors"></a>エラー
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE オブジェクトや COM オブジェクトは、オブジェクト メンバー関数の HRESULT リターン コードによってエラーを報告します。 OLE と COM の HRESULT は、ビットがまとめられている構造体です。 OLE には、構造体のメンバーを取り出すマクロが用意されています。  
  
 OLE と COM の指定、 **IErrorInfo**インターフェイスです。 インターフェイスはメソッドを公開など**GetDescription**です。 これにより、クライアントは OLE サーバーや COM サーバーからエラーの詳細を取得できます。 OLE DB を拡張**IErrorInfo**単一メンバー関数の実行に複数のエラー情報パケットの戻り値をサポートするためにします。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では複数のエラーを返すことができます。 アプリケーションは、一度にサーバー エラーは 1 つを呼び出すことによって取得できます[imultipleresults::getresult](http://go.microsoft.com/fwlink/?LinkId=129630) ISQLErrorInfo と IErrorRecords と組み合わせて使用します。  
  
 SQL Server の OLE DB Driver は、OLE DB レコードが強化されたを公開**IErrorInfo**、カスタム**ISQLErrorInfo**、およびプロバイダー固有[ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)エラーオブジェクトのインターフェイス。  
  
 トレースのエラーについては、次を参照してください。[データ アクセスのトレース](http://go.microsoft.com/fwlink/?LinkId=125805)です。 エラーのトレースで追加された機能強化については[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]を参照してください[へのアクセス ログの診断情報、拡張イベント](../../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [リターン コード](../../oledb/ole-db-errors/return-codes.md)  
  
-   [エラー インターフェイス内の情報](../../oledb/ole-db-errors/information-in-error-interfaces.md)  
  
-   [SQL Server エラーの詳細](../../oledb/ole-db-errors/sql-server-error-detail.md)  
  
-   [エラー情報の取得](../../oledb/ole-db-errors/retrieving-error-information.md)  
  
-   [SQL Server のメッセージ結果](../../oledb/ole-db-errors/sql-server-message-results.md)  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server のプログラミング](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
