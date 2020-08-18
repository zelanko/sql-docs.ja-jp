---
description: '付録 A: データおよびサービスプロバイダー'
title: '付録 A: Providers |Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data providers [ADO]
- providers [ADO]
- ADO, providers
- service providers [ADO]
- service components [ADO]
ms.assetid: e2581b47-b11e-4e1e-b96c-d39c77c5b48a
author: rothja
ms.author: jroth
ms.openlocfilehash: d14a3399eb771965d039126ebf3672a8ad3d5190
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88396408"
---
# <a name="appendix-a-data-and-service-providers"></a>付録 A: データおよびサービスプロバイダー
このセクションでは、データプロバイダー、サービスプロバイダー、およびサービスコンポーネントの3種類のプロバイダーについて説明します。 プロバイダーは、データを提供するカテゴリとサービスを提供するカテゴリの2つのカテゴリに分類されます。 *データプロバイダー*は独自のデータを所有し、アプリケーションに表形式で公開します。 *サービスプロバイダー*は、データを生成して使用することによってサービスをカプセル化し、ADO アプリケーションの機能を強化します。 サービスプロバイダーは、他のサービスプロバイダーまたはコンポーネントと連携して動作する必要がある *サービスコンポーネント*としてさらに定義することもできます。

## <a name="data-providers"></a>データ プロバイダー
 ADO は、さまざまなデータプロバイダーのいずれかに接続でき、特定のプロバイダーの特定の機能に関係なく同じプログラミングモデルを公開できるため、強力で柔軟性があります。

 ただし、各データプロバイダーは一意であるため、アプリケーションと ADO の対話方法はデータプロバイダーによって多少異なります。 これらの違いは、通常、次の3つのカテゴリのいずれかに分類されます。

-   [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)プロパティの接続パラメーター。

-   [コマンド](../../../ado/reference/ado-api/command-object-ado.md) オブジェクトの使用法。

-   プロバイダー固有の [レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md) の動作。

 Microsoft から現在提供されている各データプロバイダーの詳細については、次の一覧を参照してください。

|領域|トピック|
|----------|-----------|
|ODBC データベース|[Microsoft OLE DB Provider for ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)|
|Microsoft インデックスサービス|[Microsoft OLE DB Provider for Microsoft Indexing Service](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-indexing-service.md)|
|Active Directory サービス|[Microsoft OLE DB Provider for Microsoft Active Directory サービス](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-active-directory-service.md)|
|Microsoft Jet データベース|[Microsoft Jet 用 OLE DB プロバイダー](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md)|
|Microsoft SQL Server|[Microsoft OLE DB Provider for SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)|
|Oracle データベース|[Microsoft OLE DB Provider for Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md)|
|インターネット公開|[Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)|
|単純なデータソース|[Microsoft OLE DB Simple プロバイダー](../../../ado/guide/appendixes/microsoft-ole-db-simple-provider.md)|

## <a name="provider-specific-dynamic-properties"></a>プロバイダー固有の動的プロパティ
 [Connection](../../../ado/reference/ado-api/connection-object-ado.md)、 [Command](../../../ado/reference/ado-api/command-object-ado.md)、および[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトの[properties](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションには、プロバイダー固有の動的プロパティが含まれます。 これらのプロパティは、ADO がサポートする組み込みプロパティ以外のプロバイダー固有の機能に関する情報を提供します。

 接続を確立し、これらのオブジェクトを作成したら、オブジェクトの**properties**コレクションに対して[Refresh](../../../ado/reference/ado-api/refresh-method-ado.md)メソッドを使用して、プロバイダー固有のプロパティを取得します。 これらの動的プロパティの詳細については、プロバイダーのドキュメントと [OLE DB プログラマーガイド](https://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8) を参照してください。

## <a name="service-providers"></a>サービス プロバイダー
 サービスプロバイダーを使用するには、キーワードを指定する必要があります。 また、各サービスプロバイダーに関連付けられているプロバイダー固有の動的プロパティにも注意する必要があります。 プロバイダー固有の詳細については、Microsoft から現在提供されているサービスプロバイダーごとに記載されています。

-   [Microsoft Data Shaping Service for OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)

-   [Microsoft OLE DB 永続化プロバイダー](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)

-   [Microsoft OLE DB リモート処理プロバイダー](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md)

## <a name="service-components"></a>サービス コンポーネント
 OLE DB サービスコンポーネント [用の Cursor service](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) は、データプロバイダーのカーソルサポート機能を補完します。 また、キーワードと動的プロパティが必要です。

 OLE DB プロバイダーの詳細については、「 [Microsoft OLE DB](https://msdn.microsoft.com/library/windows/desktop/ms722784.aspx)」を参照してください。

## <a name="provider-commands"></a>プロバイダーコマンド
 ここに一覧表示されているプロバイダーごとに、アプリケーションでプロバイダーコマンドとして SQL ステートメントを入力できるようにするには、ユーザー入力を常に検証する必要があり `DROP TABLE t1` ます。また、ユーザー入力の一部として、などの危険な sql ステートメントを使用してハッカー攻撃を受ける可能性があります。

## <a name="see-also"></a>参照
 [コマンドオブジェクト (ado)](../../../ado/reference/ado-api/command-object-ado.md) [接続オブジェクト (ado)](../../../ado/reference/ado-api/connection-object-ado.md) Microsoft [OLE DB provider For Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md) Microsoft [OLE DB Provider for microsoft Active Directory Service](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-active-directory-service.md) [microsoft OLE DB PROVIDER for microsoft インデックスサービス](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-indexing-service.md)Microsoft OLE DB provider For [ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md) [Microsoft OLE DB Provider for Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md) microsoft OLE DB provider For [MICROSOFT Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) [Properties Collection (](../../../ado/reference/ado-api/properties-collection-ado.md) ado) [Recordset Object (](../../../ado/reference/ado-api/recordset-object-ado.md) ado) [Refresh Method (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md) [を実行](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)します。
