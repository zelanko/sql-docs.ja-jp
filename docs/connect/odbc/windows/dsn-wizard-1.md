---
title: データ ソース ウィザード画面 1 (ODBC Driver for SQL Server) |Microsoft ドキュメント
ms.custom: ''
ms.date: 09/27/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3798f482e51653c629760c7bfdf6e26a5b8d31fa
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="data-source-wizard-screen-1"></a>データ ソース ウィザード画面 1

名前とデータ ソースの説明と、データ ソースが接続する SQL Server を実行しているサーバーの名前を指定します。 
    
## <a name="options"></a>オプション

### <a name="name"></a>名前

データ ソースへの接続を要求する場合に ODBC アプリケーションで使用されるデータ ソースの名前です。 たとえば、"人事" のようにします。 データ ソース名は、[ODBC データ ソース アドミニストレーター] ダイアログ ボックスに表示されます。

### <a name="description"></a>Description

(省略可) データ ソースの説明です。 たとえば、"全従業員の入社日、給与履歴、および現在の評価" のようにします。

### <a name="select-or-enter-a-server-name"></a>[サーバー名の選択または入力]

ネットワーク上の SQL Server のインスタンスの名前。 次の編集ボックスにサーバーを指定する必要があります。

ほとんどの場合、ODBC ドライバーは、既定のプロトコルの順序とは、このボックスで指定されたサーバー名を使用して接続できます。 サーバーの別名を作成またはクライアント ネットワーク ライブラリを構成する場合は、SQL Server 構成マネージャーを使用します。

入力できます"(local)"サーバー ボックスで SQL Server と同じコンピューターを使用している場合。 ユーザーは、ローカル ネットワークに接続されていないバージョンの SQL Server を実行する場合でも、SQL Server のインスタンスに接続できます。 SQL Server の複数のインスタンスは、同じコンピューターで実行できます。 SQL Server の名前付きインスタンスを指定するサーバー名として指定_ServerName_\\_InstanceName_です。

ネットワークのさまざまな種類のサーバー名の詳細については、SQL Server オンライン ブックの SQL Server のインストールに関するドキュメントを参照してください。

### <a name="finish"></a>完了

この画面で指定した情報がすべての SQL Server に接続するために必要な場合は、クリックして**完了**です。 ウィザードの他の画面で指定するすべての属性には既定値が使用されます。

### <a name="next"></a>Next

クリックして続行するには、ウィザードの次の画面に**次**です。

## <a name="next-steps"></a>次の手順

[データ ソース ウィザード画面 2](../../../connect/odbc/windows/dsn-wizard-2.md)
