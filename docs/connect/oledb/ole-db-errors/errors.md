---
title: エラー |Microsoft Docs
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
ms.openlocfilehash: 477c89e8d058d2f2971dc295c3bf8e1449c5a3d9
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2018
ms.locfileid: "39105858"
---
# <a name="errors"></a>エラー
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE オブジェクトや COM オブジェクトは、オブジェクト メンバー関数の HRESULT リターン コードによってエラーを報告します。 OLE と COM の HRESULT は、ビットがまとめられている構造体です。 OLE には、構造体のメンバーを取り出すマクロが用意されています。  
  
 OLE と COM は、**IErrorInfo** インターフェイスを指定します。 このインターフェイスでは、**GetDescription** などのメソッドを公開します。 これにより、クライアントは OLE サーバーや COM サーバーからエラーの詳細を取得できます。 OLE DB では、複数のエラー情報パケットを 1 回のメンバー関数の実行で返すことができるように **IErrorInfo** を拡張します。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では複数のエラーを返すことができます。 アプリケーションで一度に 1 つずつサーバー エラーを取得するには、ISQLErrorInfo および IErrorRecords と組み合わせて [IMultipleResults::GetResult](http://go.microsoft.com/fwlink/?LinkId=129630) を呼び出します。  
  
 OLE DB Driver for SQL Server は、OLE DB レコードに対して機能強化された **IErrorInfo**、カスタム **ISQLErrorInfo**、およびプロバイダー固有の [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) の各エラー オブジェクト インターフェイスを公開します。  
  
 エラーのトレースの詳細については、「[データ アクセスのトレース](http://go.microsoft.com/fwlink/?LinkId=125805)」を参照してください。 エラーのトレースで追加の機能強化については[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]を参照してください[診断の情報を拡張イベント ログにアクセスする](../../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [リターン コード](../../oledb/ole-db-errors/return-codes.md)  
  
-   [エラー インターフェイス内の情報](../../oledb/ole-db-errors/information-in-error-interfaces.md)  
  
-   [SQL Server エラーの詳細](../../oledb/ole-db-errors/sql-server-error-detail.md)  
  
-   [エラー情報の取得](../../oledb/ole-db-errors/retrieving-error-information.md)  
  
-   [SQL Server のメッセージ結果](../../oledb/ole-db-errors/sql-server-message-results.md)  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server のプログラミング](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
