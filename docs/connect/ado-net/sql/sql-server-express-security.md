---
title: SQL Server Express のセキュリティ
description: SQL Server Express のセキュリティ上の考慮事項を説明します。
ms.date: 09/26/2019
ms.assetid: cf9cf6d9-4b05-43e9-ac7b-6cefbfcd6d4e
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: cd6f71f5c42418ab9357a9aaeec9788ae3ea0d65
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920961"
---
# <a name="sql-server-express-security"></a>SQL Server Express のセキュリティ

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Microsoft SQL Server Express Edition (SQL Server Express) は Microsoft SQL Server をベースとしており、同データベース エンジンの多くの機能をサポートしています。 これは、重要ではない機能とネットワーク接続が既定でオフになるように設計されています。 これにより、悪意のあるユーザー攻撃に利用できる領域が小さくなります。  
  
SQL Server Express は、通常、名前付きインスタンスとしてインストールされます。 インスタンスの既定の名前は `SQLExpress` です。 名前付きインスタンスは、コンピューターのネットワーク名と、インストール時に指定したインスタンス名によって識別されます。  
  
## <a name="network-access"></a>ネットワーク アクセス  
セキュリティ上の理由により、SQL Server Express では、ネットワーク プロトコルが既定で無効になっています。 これにより、SQL Server Express のインスタンスをホストしているコンピューターを侵害する可能性のある外部ユーザーからの攻撃を防ぐことができます。 別のコンピューターから SQL Server Express インスタンスに接続するには、ネットワーク接続を明示的に有効にして、SQL Server Browser サービスを開始する必要があります。  
  
ネットワーク接続が有効になると、SQL Server Express インスタンスのセキュリティ要件は、SQL Server の他のエディションと同様になります。  
  
## <a name="user-instances"></a>ユーザー インスタンス  
ユーザー インスタンスは、SQL Server Express の親インスタンスによって生成される、SQL Server Express データベース エンジンの独立したインスタンスです。 ユーザー インスタンスの主な目的は、最小限の特権しか持たないユーザー アカウントで Windows を実行しているユーザーが、ローカル コンピューターの SQL Server Express インスタンスに対してシステム管理者 (`sysadmin`) の特権を持つことができるようにすることです。 ユーザー インスタンスは、自分のコンピューターのシステム管理者であるユーザーを対象とはしていません。  
  
ユーザー インスタンスは、ユーザーに代わるものとして、SQL Server または SQL Server Express のプライマリ インスタンスから生成されます。 これは、そのユーザーの Windows セキュリティ コンテキストでのユーザー プロセスとして実行されます。 SQL Server ログインは許可されません。Windows ログインのみがサポートされます。 これにより、ユーザー インスタンスで実行されるソフトウェアによって、そのユーザーにアクセス許可のないシステム全体の変更が行われるのを防ぐことができます。 ユーザー インスタンスは子インスタンスやクライアント インスタンスと呼ばれたり、"run as normal user (通常のユーザーとして実行)" の頭字語 RANU と呼ばれたりすることもあります。  
  
各ユーザー インスタンスは、その親インスタンスや同じコンピューター上で実行されている他のユーザー インスタンスからは分離されています。 ユーザー インスタンスにインストールされたデータベースはシングル ユーザー モードでのみ開かれます。つまり、複数のユーザーがそれに接続することはできません。 ユーザー インスタンスでは、レプリケーション、分散クエリ、およびリモート接続が無効になっています。 ユーザー インスタンスに接続している場合、ユーザーには親 SQL Server Express インスタンスに対する特別な権限はありません。  
  
## <a name="external-resources"></a>外部リソース  
SQL Server Express の詳細については、次のリソースを参照してください。  
  
|||  
|-|-|  
|[Microsoft SQL Server 2005 Express Edition オンライン ブック](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms165706(v=sql.90))|SQL Server 2005 Express Edition に関する詳細なドキュメント。|  
|「[管理者以外のユーザーのためのユーザー インスタンス](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms143684(v=sql.100))」 (SQL Server オンライン ブック)|ユーザー インスタンスの作成方法と配置方法を説明しています。|  
|[SQL Server Express のユーザー インスタンス](sql-server-express-user-instances.md)|ADO.NET アプリケーションのユーザー インスタンス機能について説明しています。 ユーザー インスタンスを有効にする方法、<xref:Microsoft.Data.SqlClient.SqlConnection> を使用してユーザー インスタンスに接続する方法、ユーザー インスタンスの有効期間、およびユーザー インスタンスのシナリオについて情報を提供しています。|  
  
## <a name="next-steps"></a>次のステップ
- [SQL Server のセキュリティ](sql-server-security.md)
- [SQL Server Express のユーザー インスタンス](sql-server-express-user-instances.md)
