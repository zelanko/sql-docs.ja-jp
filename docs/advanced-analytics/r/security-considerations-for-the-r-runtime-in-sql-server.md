---
title: "機械学習で SQL Server のセキュリティに関する考慮事項 |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5065197-69e6-4fce-9654-00acaecc148b
caps.latest.revision: 15
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d9b5fba856cc40c11f218faf0a61f66ee5451aa4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="security-considerations-for-machine-learning-in-sql-server"></a>機械学習で SQL Server のセキュリティに関する考慮事項

この記事は、管理者や設計者は、留意ください machine learning のサービスを使用する場合に、セキュリティの考慮事項を一覧表示します。

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習のサービス

## <a name="use-a-firewall-to-restrict-network-access-by-r"></a>ファイアウォールを使用して、R によるネットワーク アクセスを制限します。

既定インストールでは、Windows ファイアウォールの規則は、R ランタイム プロセスからのすべての発信ネットワーク アクセスをブロックするために使用します。 R ランタイム プロセスによって、パッケージのダウンロード、および悪意のある可能性があるその他のネットワーク呼び出しが実行されないように、ファイアウォール ルールを作成する必要があります。

別のファイアウォール プログラムを使用している場合にも、ローカル ユーザー アカウント用、またはユーザー アカウント プールによって表されるグループ用のルールを設定することで、R ランタイムの送信ネットワーク接続をブロックするためのルールを作成できます。

R、または Python ランタイムによって設けるネットワーク アクセスを防ぐために Windows ファイアウォール (または別のファイアウォール) を有効にすることを強くお勧めします。

## <a name="authentication-methods-supported-for-remote-compute-contexts"></a>リモート計算コンテキストでサポートされる認証メソッド

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]間の接続を作成するときに、Windows 統合認証と SQL の両方のログインをサポートしている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]とリモート データ サイエンス クライアント。

たとえば、ノート PC で R ソリューションを開発し、SQL Server コンピューターで計算を実行する場合は、**rx** 関数を使用し、Windows 資格情報に基づいて接続文字列を定義することによって、SQL Server データ ソースを R で作成します。

変更すると、_計算コンテキスト_、SQL Server コンピューターにラップトップから使用する Windows アカウントに必要なアクセス許可がある場合すべて R コードが実行される SQL Server コンピューターにします。 さらに、R コードの一部として実行された SQL クエリは、管理者の資格情報も実行されます。

このシナリオでは、混合モード認証を許可する SQL Server インスタンスを構成することが必要では、SQL ログインの使用はサポートされても。

### <a name="implied-authentication"></a>暗黙の認証

 一般に、[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]外部スクリプトの実行時を起動し、独自のアカウント下でスクリプトを実行します。 ただし、外部のランタイムは、ODBC 呼び出しを行う場合、 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] ODBC 呼び出しが異常終了しないようにするコマンドを送信したユーザーの資格情報の権限を借用します。 これは*暗黙の認証*と呼ばれます。
 
 > [!IMPORTANT]
 >
 > 暗黙の認証が正常に行われるには、ワーカー アカウント (既定では **SQLRUser**) を含む Windows ユーザー グループがインスタンスのマスター データベースにアカウントを持ち、このアカウントにインスタンスへの接続許可が付与されている必要があります。
 > 
 > グループ**SQLRUser** Python スクリプトを実行しているときにも使用します。 

## <a name="no-support-for-encryption-at-rest"></a>保存時の暗号化はサポートされていません

データを送信または受信外部スクリプトの実行時からに、透過的なデータ暗号化はサポートされていません。 その結果、保存時の暗号化**は**R または Python スクリプト、ディスク、または任意の保存された中間結果を保存されるデータで使用する任意のデータに適用されます。

## <a name="resources"></a>リソース

詳細については、サービスの管理、および R スクリプトを実行するために使用するユーザー アカウントをプロビジョニングする方法について、次を参照してください。[構成 Advanced Analytics Extensions を管理および](../../advanced-analytics/r/configure-and-manage-advanced-analytics-extensions.md)です。

セキュリティ アーキテクチャの説明を参照してください。

+ [R のセキュリティの概要](security-overview-sql-server-r.md)
+ [Python のセキュリティの概要](../python/security-overview-sql-server-python-services.md)

