---
title: エラー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
ms.assetid: bd0612f4-96ef-4919-b0f9-b5447210fe93
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e3979390a58235dbb8ec7c76e7b16478e7d9deb9
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705001"
---
# <a name="errors"></a>エラー
  OLE オブジェクトや COM オブジェクトは、オブジェクト メンバー関数の HRESULT リターン コードによってエラーを報告します。 OLE と COM の HRESULT は、ビットがまとめられている構造体です。 OLE には、構造体のメンバーを取り出すマクロが用意されています。  
  
 OLE と COM は、**IErrorInfo** インターフェイスを指定します。 このインターフェイスでは、**GetDescription** などのメソッドを公開します。 これにより、クライアントは OLE サーバーや COM サーバーからエラーの詳細を取得できます。 OLE DB では、複数のエラー情報パケットを 1 回のメンバー関数の実行で返すことができるように **IErrorInfo** を拡張します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では複数のエラーを返すことができます。 アプリケーションで一度に 1 つずつサーバー エラーを取得するには、ISQLErrorInfo および IErrorRecords と組み合わせて [IMultipleResults::GetResult](https://go.microsoft.com/fwlink/?LinkId=129630) を呼び出します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、OLE DB レコード拡張された**IErrorInfo**、カスタム `ISQLErrorInfo` 、およびプロバイダー固有の[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) error オブジェクトインターフェイスを公開します。  
  
 エラーのトレースの詳細については、「[データ アクセスのトレース](https://go.microsoft.com/fwlink/?LinkId=125805)」を参照してください。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] に追加されたエラーのトレースの機能強化については、「[拡張イベント ログの診断情報へのアクセス](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [リターン コード](return-codes.md)  
  
-   [エラー インターフェイス内の情報](information-in-error-interfaces.md)  
  
-   [SQL Server エラーの詳細](sql-server-error-detail.md)  
  
-   [エラー情報の取得](retrieving-error-information.md)  
  
-   [SQL Server のメッセージ結果](sql-server-message-results.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
