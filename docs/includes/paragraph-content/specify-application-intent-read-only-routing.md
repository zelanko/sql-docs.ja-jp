---
title: ファイルを含める
description: ファイルを含める
services: sql-database
author: MightyPen
ms.service: sql-database
ms.topic: include
ms.date: 04/05/2018
ms.author: genemi
ms.custom: include file
ms.openlocfilehash: 842a7377bcd6bdcb649a78b2f31eb66de95bc5a3
ms.sourcegitcommit: a98ed7872afc055c65aa9697d571f8b300f6eeb4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36313398"
---
## <a name="specifying-application-intent"></a>アプリケーション インテントの指定

キーワード**ApplicationIntent**接続文字列で指定できます。 割り当てることができる値は**ReadWrite**または**ReadOnly**です。 既定値は**ReadWrite**です。

ときに**ApplicationIntent = ReadOnly**クライアントが接続するときに、読み取りワークロードを要求します。 サーバー、目的とした接続時にと適用中に、**使用**ステートメントをデータベースします。

**ApplicationIntent**キーワードは従来の読み取り専用データベースでは機能しません。  


#### <a name="targets-of-readonly"></a>読み取り専用のターゲット

接続を選択すると**ReadOnly**接続が、次の特別な構成がデータベースに存在する場合のいずれかに割り当てられています。

- [Always On](~/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)
    - データベースでは、許可したり、対象の Always On データベース ワークロードの読み取りを許可しないようにすることができます。 この選択を使用して制御されます、 **ALLOW_CONNECTIONS**の句、 **PRIMARY_ROLE**と**SECONDARY_ROLE** TRANSACT-SQL ステートメント。

- [Geo レプリケーション](https://docs.microsoft.com/azure/sql-database/sql-database-geo-replication-overview)

- [スケール アウトの読み取り](https://docs.microsoft.com/azure/sql-database/sql-database-read-scale-out)

これらの特別なターゲットのいずれも使用可能な場合、通常のデータベースから読み取られます。

&nbsp;

**ApplicationIntent**キーワードを使用*読み取り専用ルーティング*です。


## <a name="read-only-routing"></a>読み取り専用ルーティング

読み取り専用ルーティングは、データベースの読み取り専用レプリカの可用性を実現する機能です。 読み取り専用ルーティングを有効にするには、以下のすべての適用。

- AlwaysOn 可用性グループ リスナーに接続する必要があります。

- **ApplicationIntent** 接続文字列キーワードを **ReadOnly**に設定する必要があります。

- データベース管理者が可用性グループを構成し、読み取り専用のルーティングを有効にする必要があります。

複数の接続を使用して読み取り専用ルーティングがすべてが同じ読み取り専用レプリカに接続します。 データベース同期の変更やサーバーのルーティング構成の変更によって、クライアントが別の読み取り専用レプリカに接続される場合があります。 すべての読み取り専用要求が同じ読み取り専用レプリカに接続を確認することができます。 によってこの sameness ことを確認*いない*に可用性グループ リスナーを渡す、**サーバー**接続文字列キーワードです。 代わりに、読み取り専用インスタンスの名前を指定します。

読み取り専用ルーティングは、プライマリに接続するよりも長くかかる可能性があります。 長い待機は読み取り専用ルーティングは、まず、プライマリに接続するためと、次に、最適な使用可能な読み取り可能セカンダリを検索します。 これら複数 staps のためには、少なくとも 30 秒間にログイン タイムアウトを長く必要があります。

