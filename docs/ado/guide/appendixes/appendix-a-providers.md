---
title: '付録 a: プロバイダー |Microsoft ドキュメント'
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data providers [ADO]
- providers [ADO]
- ADO, providers
- service providers [ADO]
- service components [ADO]
ms.assetid: e2581b47-b11e-4e1e-b96c-d39c77c5b48a
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e26659de53d43f14863e0bf83d70f5f6d3dbcfd0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="appendix-a-data-and-service-providers"></a>付録 a: データとサービス プロバイダー
このセクションでは、3 種類のプロバイダー。 データ プロバイダー、サービス プロバイダー、およびサービス コンポーネントです。 プロバイダーは 2 つのカテゴリに分類されます。 データとサービスを提供するものを提供するものです。 A*データ プロバイダー*独自のデータを所有し、表形式で、アプリケーションに公開します。 A*サービス プロバイダー*生成して、ADO アプリケーションの機能の拡張データを使用してサービスをカプセル化します。 サービス プロバイダーはさらとしても定義する、*サービス コンポーネント*、他のコンポーネントまたはサービス プロバイダーと連携する必要があります。

## <a name="data-providers"></a>データ プロバイダー
 ADO では強力で柔軟ないくつかの別のデータ プロバイダーのいずれかに接続し、指定されたプロバイダーの特定の機能に関係なく、同じプログラミング モデルを公開します。

 ただし、各データ プロバイダーが一意であるため、アプリケーションが ADO とやり取りする方法はによって多少異なりますデータ プロバイダー。 相違点は、通常、3 つのカテゴリに分類されます。

-   接続パラメーター、 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)プロパティです。

-   [コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトの使用量。

-   プロバイダー固有[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)動作します。

 現在、Microsoft から使用可能なデータ プロバイダーの詳細は次のとおりです。

|領域|トピック|
|----------|-----------|
|ODBC データベース|[Microsoft OLE DB Provider for ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)|
|Microsoft インテックス サービス|[Microsoft OLE DB Provider for Microsoft インテックス サービス](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-indexing-service.md)|
|Active Directory サービス|[Microsoft Active Directory サービスの Microsoft OLE DB プロバイダー](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-active-directory-service.md)|
|Microsoft Jet データベース|[OLE DB Provider for Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md)|
|Microsoft SQL Server|[Microsoft OLE DB Provider for SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)|
|Oracle データベース|[Microsoft OLE DB Provider for Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md)|
|インターネットへの発行|[インターネットへの発行の Microsoft OLE DB プロバイダー](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)|
|単純なデータ ソース|[Microsoft OLE DB の単純なプロバイダー](../../../ado/guide/appendixes/microsoft-ole-db-simple-provider.md)|

## <a name="provider-specific-dynamic-properties"></a>プロバイダー固有の動的プロパティ
 [プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)のコレクション、[接続](../../../ado/reference/ado-api/connection-object-ado.md)、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)、および[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトに固有の動的なプロパティが含まれます、。プロバイダー。 これらのプロパティは、ADO では組み込みのプロパティを超えるプロバイダーに固有の機能に関する情報を提供します。

 接続を確立すると、これらのオブジェクトを作成するを使用して、[更新](../../../ado/reference/ado-api/refresh-method-ado.md)メソッドを**プロパティ**プロバイダー固有のプロパティを取得するオブジェクトのコレクション。 プロバイダーのマニュアルを参照してください、 [OLE DB プログラマ ガイド](http://msdn.microsoft.com/en-us/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8)これらの動的プロパティについての詳細。

## <a name="service-providers"></a>サービス プロバイダー
 サービス プロバイダーを使用するには、キーワードを指定してください。 各サービス プロバイダーに関連付けられているプロバイダーに固有の動的なプロパティの対応する必要があります。 プロバイダー固有の詳細については、現在、Microsoft から提供されている各サービス プロバイダーのとおりです。

-   [Microsoft Data Shaping Service for OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)

-   [Microsoft OLE DB の永続化プロバイダー](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)

-   [Microsoft OLE DB のリモート処理プロバイダー](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md)

## <a name="service-components"></a>サービス コンポーネント
 [For OLE DB カーソル サービス](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)サービス コンポーネントがデータ プロバイダーのカーソル サポート機能を補完します。 また、キーワードを必要し、動的プロパティを持ちます。

 OLE DB プロバイダーの詳細については、次を参照してください。 [Microsoft OLE DB](https://msdn.microsoft.com/library/windows/desktop/ms722784.aspx)です。

## <a name="provider-commands"></a>プロバイダー コマンド
 プロバイダーごとに、アプリケーションがプロバイダーのコマンドとしての SQL ステートメントを入力するユーザーを許可する場合は、ここでは、一覧表示、常にユーザー入力を検証してハッカーの攻撃などを使用して、危険性のある SQL ステートメントに備える`DROP TABLE t1`、ユーザー入力の一部として。

## <a name="see-also"></a>参照
 [コマンド オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md) [接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) [インターネット パブリッシング用の Microsoft OLE DB Provider](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md) [Microsoft Active Directory サービスの Microsoft OLE DB プロバイダー](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-active-directory-service.md) [Microsoft OLE DB Provider for Microsoft インテックス サービス](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-indexing-service.md) [Microsoft OLE DB Provider for ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md) [Microsoft OLE DB Provider for Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md) [Microsoft OLE DB Provider for SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) [Microsoft OLE DB Provider for Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) [プロパティのコレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [Refresh メソッド (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)
